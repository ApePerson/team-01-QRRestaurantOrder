# P2 sections owned by Isaiah Bueno-Hernandez (@buenoisaiah006-bit)

> Commit this file from your own GitHub account on branch `p2/design` and open a pull request; another member reviews it.

## 6 High-Level Design



### 6.1 Quality-attribute scenarios

| **ID · quality**      | **Stimulus and environment**                                                                                                      | **Response**                                                              | **Response measure**                                                                 | **From**            |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|--------------------------------------------------------------------------------------|---------------------|
| QAS-1 · Performance   | 20 diners at 20 tables submit orders within the same minute during dinner rush; staff queue open on one tablet.                   | Each new order appears on every open staff screen without a reload.       | ≥ 95% of orders shown within 3 s of Submit (spike 01: 0.3 s at the 95th percentile). | QR-01, UC-01, UC-03 |
| QAS-2 · Availability  | The staff tablet loses its network for 60 s while 5 orders are submitted.                                                         | On reconnection the queue shows every order received meanwhile, in order. | 0 orders missing; queue complete within 5 s of reconnection.                         | UC-03 1a, A2        |
| QAS-3 · Security      | Someone sends 1,000 requests to staff and manager functions without logging in, and 100 manager-only requests with a Staff login. | Every request is refused; nothing changes.                                | 100% refused; 0 card numbers found in our data or logs by a full-text search.        | QR-05, CON-02       |
| QAS-4 · Modifiability | The restaurant changes to a different payment provider.                                                                           | Only the part that talks to the provider changes.                         | 1 component changed (C8); ≤ 3 person-days; no change to ordering.                    | UC-07, A5, Q1       |

### 6.2 Architectural style

**Chosen: layered client–server (a single, modular application server) with publish–subscribe for live updates (ADR-01).** Browsers run the customer and staff interfaces; one application server holds all rules in separate modules; one relational database stores the data. When an order changes, the order module publishes an event and a live-update module pushes it to every subscribed screen.

| **Style**                                                                    | **QAS-1 speed**            | **QAS-2 recovery**                        | **QAS-3 security**                                    | **QAS-4 change**                                 | **Cost for us**                                                | **Verdict** |
|------------------------------------------------------------------------------|----------------------------|-------------------------------------------|-------------------------------------------------------|--------------------------------------------------|----------------------------------------------------------------|-------------|
| Layered client–server, modular server + publish–subscribe                    | Push measured 0.3 s p95    | Server keeps the queue; screen reloads it | One place to check every request                      | Payment isolated in one module                   | One deployable; fits 6 students and \$50/month                 | **Chosen**  |
| Microservices (menu, orders, payment as separate services)                   | Extra network hop per call | Each service must recover alone           | Auth repeated in each service                         | Best isolation                                   | Several deployables, a gateway, more hosting cost and ops work | Rejected    |
| Serverless backend-as-a-service (client talks to a hosted database directly) | Good, built-in sync        | Built-in                                  | Rules written as database policies; easy to get wrong | Payment logic ends up in the client or functions | Vendor lock-in; prices and rules partly enforced on the phone  | Rejected    |

### 6.3 Component view

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="media/image6.png" style="width:6.9in;height:2.13032in" /></p>
<p><strong>Figure 6. Component view.</strong> Each box names the use cases, scenarios or decisions it answers to. Solid arrows are requests; dashed arrows are pushes from the Live Update Hub.</p></td>
</tr>
</tbody>
</table>

| **Component**              | **Responsibility**                                                                                       | **Answers to**                                 |
|----------------------------|----------------------------------------------------------------------------------------------------------|------------------------------------------------|
| C1 Customer Web App        | Menu, cart, confirmation, order status and pay screens for one table.                                    | UC-01, UC-02, UC-07; ADR-05                    |
| C2 Staff & Manager Web App | Staff queue, status changes, sold-out flags, menu and table editing.                                     | UC-03 to UC-06                                 |
| C3 Access Control          | Logins, sessions and roles; checks every staff and manager request.                                      | FR-14, QR-05, QAS-3                            |
| C4 Menu Manager            | Categories, items, options, prices, availability.                                                        | UC-01, UC-04, UC-05                            |
| C5 Table & QR Manager      | Tables, table links, QR images, active/inactive.                                                         | UC-06; FR-01, FR-15                            |
| C6 Order Manager           | Shared table carts, orders, table checks, server confirmation, line cancellation, status changes, bills. | UC-01, UC-03, UC-07; FR-18, FR-21–FR-23, FR-27 |
| C7 Live Update Hub         | Pushes order events to subscribed screens; 1-s polling fallback.                                         | QAS-1, QAS-2; ADR-02; spike 01                 |
| C8 Payment Adapter         | Only component that talks to the payment gateway; verifies its signed results.                           | UC-07; QAS-4; ADR-03; CON-02                   |
| C9 Data Store              | Keeps menu, tables, orders, bills, payments, staff accounts.                                             | ADR-04                                         |

### 6.4 Deployment view

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="media/image7.png" style="width:6.9in;height:1.99661in" /></p>
<p><strong>Figure 7. UML deployment view.</strong> Four trust zones (dashed). Every connection that crosses a zone is encrypted (HTTPS, WSS or TLS). The diner's phone talks to the gateway directly for card entry, so card data never crosses into zone 3.</p></td>
</tr>
</tbody>
</table>

| **Connection**                       | **Protocol**                   | **Boundary crossed** | **Protection**                                                                                     |
|--------------------------------------|--------------------------------|----------------------|----------------------------------------------------------------------------------------------------|
| Phone ↔ application server           | HTTPS + WSS                    | 1 → 3                | TLS; every request re-checked on the server; cart and prices held on the server (ADR-05)           |
| Tablet / laptop ↔ application server | HTTPS + WSS                    | 2 → 3                | TLS; session cookie (HttpOnly, Secure); role check in C3                                           |
| Application server ↔ database        | SQL over TLS                   | inside 3             | Private network only; no public address                                                            |
| Application server ↔ payment gateway | HTTPS API; signed webhook back | 3 ↔ 4                | Secret key kept in server configuration, never in the repository; webhook signature verified by C8 |
| Phone → gateway checkout page        | HTTPS redirect                 | 1 → 4                | Card data typed on the gateway's page only (CON-02)                                                |

### 6.5 Analysis-to-component mapping

| **Analysis object (5.2)** | **Component(s)**                                                                                                        |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------|
| TableMenu                 | C1 Customer Web App (screens) + C6 Order Manager (rules it asks for)                                                    |
| Table                     | C5 Table & QR Manager                                                                                                   |
| Menu, MenuItem            | C4 Menu Manager                                                                                                         |
| Cart                      | C6 Order Manager (one cart per table session, ADR-05) + C7 Live Update Hub (shows each phone's additions to the others) |
| OrderBook                 | C6 Order Manager                                                                                                        |
| StaffQueue                | C6 Order Manager (contents) + C7 Live Update Hub (delivery) + C2 (display)                                              |
| Bill, Payment             | C6 Order Manager                                                                                                        |
| PaymentGateway            | External; reached only through C8 Payment Adapter                                                                       |
| StaffMember (UC-03 actor) | C3 Access Control                                                                                                       |

### 6.6 Design principles in this design

| **Principle**               | **Where it shows**                                                                                                                                      |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Separation of concerns      | Three layers: browser apps (C1, C2), server modules (C3–C8), data (C9).                                                                                 |
| Information hiding          | Only C8 knows the payment provider; swapping it touches one component (QAS-4).                                                                          |
| High cohesion, low coupling | Each server module owns one group of domain concepts (6.5); modules call each other through narrow requests and publish events instead of sharing data. |
| Do not trust the client     | Phones only send choices; C6 holds the shared cart and recomputes every price and availability on submit (ADR-05).                                      |
| Least privilege             | C3 checks the role on every staff and manager request; the database is reachable only from the server.                                                  |
| Single source of truth      | An order exists only once C6 records it; screens show copies pushed by C7.                                                                              |

## 7 Design Rationale



### 7.1 ADR-01 Architectural style

| **Field**     | **Content**                                                                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Status · date | Accepted · 4 Nov 2026 (after CR-01 to CR-10)                                                                                                                                        |
| Context       | Six students, one term, \$50/month hosting (2.6), QAS-1 to QAS-4.                                                                                                                   |
| Alternatives  | Microservices; serverless backend-as-a-service; layered client–server with a modular server (6.2).                                                                                  |
| Decision      | Layered client–server: browser apps, one modular application server, one relational database, publish–subscribe inside the server for live updates.                                 |
| Cost          | One deployable: a fault in any module can stop the whole server, and modules cannot be scaled separately. Accepted because one restaurant needs far less than one server can carry. |
| Linked to     | QAS-1 to QAS-4; components C1–C9                                                                                                                                                    |

### 7.2 ADR-02 Live order updates

| **Field**     | **Content**                                                                                                                                              |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Status · date | Accepted · 4 Nov 2026 · changed by spike 01                                                                                                              |
| Context       | QR-01 needs 95% of orders on the staff screen within 3 s; P1 risk R2 assumed 3-s polling would also do.                                                  |
| Alternatives  | Polling only (every 3 s); server-sent events; WebSocket push with a polling fallback.                                                                    |
| Decision      | WebSocket push from C7 as the main channel; if the socket cannot open, the screen polls every 1 s.                                                       |
| Cost          | The server keeps one open connection per screen and must handle reconnection (QAS-2). 1-s polling, when used, sends 3 times the requests of 3-s polling. |
| Linked to     | QR-01, QAS-1, QAS-2, spike 01 (section 8), CR-07                                                                                                         |

### 7.3 ADR-03 Payment through a hosted checkout behind an adapter

| **Field**     | **Content**                                                                                                                                                             |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Status · date | Accepted · 5 Nov 2026                                                                                                                                                   |
| Context       | FR-16/17 need online payment; CON-02 forbids card data in our system; the interview named Square as the restaurant's provider, with the restaurant paying the fee (Q1). |
| Alternatives  | Card form on our own page sent to the gateway's API; paying at the restaurant's till only; hosted checkout reached through one adapter.                                 |
| Decision      | Customers pay on the gateway's hosted page; only C8 talks to the gateway and verifies its signed result before C6 marks orders Paid.                                    |
| Cost          | Customers leave our page to pay, and we depend on the gateway's availability and its fee (about 3% per payment, A5). We cannot style the card form.                     |
| Linked to     | UC-07, FR-16, FR-17, CON-02, QAS-3, QAS-4                                                                                                                               |

### 7.4 ADR-04 Relational database

| **Field**     | **Content**                                                                                                                   |
|---------------|-------------------------------------------------------------------------------------------------------------------------------|
| Status · date | Accepted · 5 Nov 2026                                                                                                         |
| Context       | Orders, lines, bills and payments are linked records that must change together (5.1).                                         |
| Alternatives  | Document store; relational database (PostgreSQL).                                                                             |
| Decision      | A managed PostgreSQL database; recording an order and its lines, or a payment and its Paid flags, happens in one transaction. |
| Cost          | Schema changes need migrations; a managed plan is part of the \$50/month hosting estimate.                                    |
| Linked to     | C9; FR-07, FR-17, FR-18                                                                                                       |

### 7.5 ADR-05 One shared cart per table, kept on the server

| **Field**     | **Content**                                                                                                                                                                                |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Status · date | Accepted · 8 Nov 2026 · supersedes the 6 Nov decision "cart kept on the phone"                                                                                                             |
| Context       | The manager interview asked that phones at one table share one cart (CR-17, FR-27). The 6 Nov decision kept each cart on its phone, which cannot be shared.                                |
| Alternatives  | Cart on each phone, sent once on submit (the 6 Nov decision); cart on the server per table session, synced to every phone.                                                                 |
| Decision      | C6 keeps one cart per table session; every change is sent to the server and C7 pushes it to the other phones at the table. On submit C6 re-checks availability and prices (alternate 12a). |
| Cost          | Every cart change is a request, so the menu needs a connection while ordering; two phones editing the same line at once need a rule (last change wins).                                    |
| Linked to     | UC-01, FR-04, FR-06, FR-18, FR-27; C6, C7; principle "do not trust the client"                                                                                                             |

### 7.6 Trade-off summary

| **Decision**                 | **We gain**                                                             | **We give up**                               | **We revisit if**                                 |
|------------------------------|-------------------------------------------------------------------------|----------------------------------------------|---------------------------------------------------|
| ADR-01 layered, one server   | Simple deployment, low cost, one place for rules                        | Independent scaling and fault isolation      | More than one restaurant uses one install         |
| ADR-02 push + 1-s polling    | QR-01 met with margin (0.3 s p95)                                       | Open connections to manage                   | P3 measurement on the real host misses QAS-1      |
| ADR-03 hosted checkout       | No card data, small PCI scope, provider swap in C8                      | Control of the payment page; fee per payment | The restaurant's provider has no hosted page (Q1) |
| ADR-04 relational DB         | Order + lines and payment + Paid flags change together                  | Schema migrations                            | —                                                 |
| ADR-05 shared cart on server | One cart per table as the manager asked; cart survives a closed browser | More requests; ordering needs a connection   | Spike re-run shows cart pushes slow QAS-1         |
