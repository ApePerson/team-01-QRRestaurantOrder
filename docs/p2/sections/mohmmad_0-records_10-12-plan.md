# P2 sections owned by Mohmmad Abuzetoon (@mrzetoon)

> Commit this file from your own GitHub account on branch `p2/records-plan` and open a pull request; another member reviews it.

## 0 Revision History and Contribution Record

Version history, who produced what for P2 (with repository evidence), and every change made since the P1 baseline, including our answer to each point of the P1 feedback.

| **Version** | **Date**   | **Author**                                        | **Summary of change**                                                                             |
|-------------|------------|---------------------------------------------------|---------------------------------------------------------------------------------------------------|
| 0.1         | 2026-10-18 | All members                                       | P1 baseline (submitted on Canvas; committed as /docs/p1/P1-submitted.pdf)                         |
| 0.5         | 2026-11-01 | Mohmmad Abuzetoon, Rafay Alvi                     | P1 feedback answered (0.2); change requests CR-01 to CR-06 applied to sections 2 and 3            |
| 0.8         | 2026-11-04 | Eshitasri Punuganti, Xuan Mai Tran, Len Isherwood | Sections 4, 5 and 8: expanded use cases, analysis models, spike 01 result; CR-07 to CR-10         |
| 0.9         | 2026-11-07 | Isaiah Bueno-Hernandez, Eshitasri Punuganti       | Sections 6, 7 and 9: high-level design, decision records, traceability; cross-checks K1 to K6 run |
| 1.0         | 2026-11-08 | All members                                       | P2 baseline: reviewed, signed (section 12), committed to /docs/p2 and tagged p2                   |

### 0.1 Individual contribution record

| **Team member**        | **What this person produced for P1**                                                                                                                                                                           | **Evidence in the repository**                                                                                                                             |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mohmmad Abuzetoon      | Section 0 (records and the answers to P1 feedback in 0.2); sections 10 to 12; repository restructure to the 10.4 layout; one issue per section; assembled the PDF, committed it to /docs/p2 and pushed tag p2. | Commits by @mrzetoon: <span class="mark">\[hashes\]</span>; PR \#<span class="mark">\[n\]</span>; review of PR \#<span class="mark">\[n\]</span>           |
| Rafay Alvi             | Sections 1 to 3 under change control: CR-01 to CR-06, FR-18 to FR-20, FR-14 source fix, use case diagram replacement in 3.4.                                                                                   | Commits by @MuhammadAlvi03: <span class="mark">\[hashes\]</span>; PR \#<span class="mark">\[n\]</span>; review of PR \#<span class="mark">\[n\]</span>     |
| Eshitasri Punuganti    | Section 4: UC-01, UC-03 and UC-07 expanded turn by turn, and the self-review log; section 9: traceability matrix and gap analysis.                                                                             | Commits by @peshi24: <span class="mark">\[hashes\]</span>; PR \#<span class="mark">\[n\]</span>; review of PR \#<span class="mark">\[n\]</span>            |
| Xuan Mai Tran          | Section 5: domain model, analysis object list, scenario tables and both analysis sequence diagrams (sources in /docs/p2/diagrams); ran K1 to K6 and kept the defect log.                                       | Commits by @keasark: <span class="mark">\[hashes\]</span>; PR \#<span class="mark">\[n\]</span>; review of PR \#<span class="mark">\[n\]</span>            |
| Isaiah Bueno-Hernandez | Sections 6 and 7: quality-attribute scenarios, style choice, component and deployment views, mapping, design principles, ADR-01 to ADR-05; filed the restaurant manager interview notes in /docs/elicitation.  | Commits by @buenoisaiah006-bit: <span class="mark">\[hashes\]</span>; PR \#<span class="mark">\[n\]</span>; review of PR \#<span class="mark">\[n\]</span> |
| Len Isherwood          | Section 8: spike 01 (live order delivery) — server, benchmark, 12 measured runs and README in /spikes/spike-01-live-orders.                                                                                    | Commits by @ApePerson: <span class="mark">\[hashes\]</span>; PR \#<span class="mark">\[n\]</span>; review of PR \#<span class="mark">\[n\]</span>          |

### 0.2 Changes since the P1 baseline

Every point of the P1 feedback, what we changed, and where. Requirement changes were raised as change requests (CR) below and approved by team vote before ADR-01 chose the architecture.

| **P1 feedback point**                                                                                      | **What we changed**                                                                                                                                                                                                                                                                                                                                                       | **Where**                                                                          |
|------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| C1 — every stakeholder need was still marked as assumed; the restaurant interview was planned but not done | <span class="mark">\[Interviewer name\]</span> interviewed the manager of <span class="mark">\[restaurant type and area\]</span> on <span class="mark">\[date\]</span>. The manager confirmed the needs of S1–S4 in 2.2 and answered Q1–Q6, Q8 and Q9. Five answers contradicted our assumptions and became change requests CR-11 to CR-17 before the design was revised. | 2.2, 11, CR-11–CR-17, /docs/elicitation/2026-11-08-restaurant-manager-interview.md |
| C1 — the submitted version replaced the cost estimate with an open range (\$8,000–\$75,000)                | Stakeholder S6 now cites the itemized estimate of \$43,263 (2.6). The range appears only as the budget ceiling in C3 and CON-03.                                                                                                                                                                                                                                          | 2.2, 2.6, CR-02                                                                    |
| C4 — /docs folders, meeting notes and issues described in 4.4 were missing                                 | Repository rebuilt to the layout in 10.4: /docs/p1, /docs/p2, /docs/p2/diagrams, /docs/elicitation, /docs/meetings, /spikes. Meeting notes for every weekly meeting since 18 Oct; one issue per P2 section.                                                                                                                                                               | 10.4, repository                                                                   |
| C4 — only three members had commits                                                                        | Each member owns a P2 section and committed it from their own account on a branch, merged through a pull request that another member reviewed.                                                                                                                                                                                                                            | 0.1                                                                                |
| C4 — the PDF in the repository differed from the one on Canvas                                             | The Canvas P1 PDF is committed as /docs/p1/P1-submitted.pdf. For P2 the same file goes to /docs/p2 and is tagged p2 before one member uploads it.                                                                                                                                                                                                                         | 10.4                                                                               |
| Leftover placeholders (an unfilled pull-request number and an unfilled member name)                        | Removed. Section 0.1 cites only commits and pull requests that exist.                                                                                                                                                                                                                                                                                                     | 0.1                                                                                |
| Repository URL on the cover page                                                                           | Corrected and checked by opening it while logged out.                                                                                                                                                                                                                                                                                                                     | Cover                                                                              |
| FR-14 cited S5, which is not a source of that need                                                         | FR-14 now cites S2, S3 and S4 (the staff and manager who log in). Q7 no longer names the instructor as a funder.                                                                                                                                                                                                                                                          | 3.1, 11, CR-01                                                                     |
| Record the interview results and update requirements under change control before choosing an architecture  | CR-01 to CR-10 were approved before ADR-01 (4 Nov). The interview raised CR-11 to CR-17, which changed UC-01, UC-03, UC-07, the domain model and ADR-05 (8 Nov).                                                                                                                                                                                                          | 0.2, 4–7, 9                                                                        |

**Change requests approved since the P1 baseline**

| **ID** | **Change**                                                                                                                                                                                                                    | **Reason**                                                                | **Affects**             |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------|
| CR-01  | FR-14 source changed from S4, S5 to S2, S3, S4.                                                                                                                                                                               | P1 feedback                                                               | 3.1                     |
| CR-02  | S6 need cites the itemized estimate instead of a range.                                                                                                                                                                       | P1 feedback                                                               | 2.2                     |
| CR-03  | Use case diagram replaced: the "Payment process" oval ("we won't build it") is gone; UC-07 Pay Bill with the Payment Gateway as supporting actor; «include» Browse Menu and Log In; «extend» Customize Item and Cancel Order. | The P1 diagram contradicted FR-16, FR-17 and the 3.5 matrix (found by K3) | 3.4                     |
| CR-04  | FR-18 added: a resubmitted cart is recorded only once.                                                                                                                                                                        | UC-01 alternate 13a (section 4.2)                                         | 3.1                     |
| CR-05  | FR-19 added: the staff queue shows time since each order was received.                                                                                                                                                        | UC-03 step (0) (section 4.3)                                              | 3.1                     |
| CR-06  | FR-20 added: the customer sees a payment receipt.                                                                                                                                                                             | UC-07 acknowledgment, step (8) (section 4.4)                              | 3.1                     |
| CR-07  | Risk R2 fallback changed from polling every 3 s to every 1 s.                                                                                                                                                                 | Spike 01 measured 3-s polling below the QR-01 target                      | 10.3, ADR-02            |
| CR-08  | Expanded use cases moved from 3.4 to section 4 and rewritten turn by turn; 3.4 keeps the diagram and one-line scopes.                                                                                                         | P2 structure                                                              | 3.4, 4                  |
| CR-09  | UC-01 precondition "the menu has at least one available item" became alternate flow 3a.                                                                                                                                       | Self-review question 6                                                    | 4.2                     |
| CR-10  | P1 risk R5 mitigation corrected: it described load time, not labour hours.                                                                                                                                                    | Internal review                                                           | 10.3                    |
| CR-11  | FR-21 added: all orders of a table session are grouped on one table check. Replaces our assumption of separate tickets.                                                                                                       | Interview Q3 (Q2)                                                         | 3.1, 4.3, 5.1           |
| CR-12  | FR-22 added: staff can cancel a single order line with a reason. UC-03 alternate changed from whole-order cancel.                                                                                                             | Interview Q4 (Q3)                                                         | 3.1, 4.3, 5.1           |
| CR-13  | FR-23 added: a server confirms each new order before the kitchen sees it (new status Awaiting confirmation).                                                                                                                  | Interview Q5 (Q4)                                                         | 1.3, 3.1, 4.2, 4.3, 5.3 |
| CR-14  | FR-24 added: menu in English and Spanish.                                                                                                                                                                                     | Interview Q6 (Q5)                                                         | 3.1, 5.1                |
| CR-15  | FR-25 added: each item lists its common allergens (was free text in the description).                                                                                                                                         | Interview Q7 (Q6)                                                         | 3.1, 5.1                |
| CR-16  | FR-26 added: staff see a clear alert when a customer's payment fails.                                                                                                                                                         | Interview Q8 (Q8)                                                         | 3.1, 4.4                |
| CR-17  | FR-27 added: phones at one table share one cart. ADR-05 reversed: the cart is kept on the server.                                                                                                                             | Interview Q9 (Q9)                                                         | 3.1, 6.5, 7.5           |

## 10 Project Plan



### 10.1 Team roles and working agreement

| **Team member**        | **Role for P2 to P3**                                      | **How the team decides when it disagrees**                                                                                                                |
|------------------------|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mohmmad Abuzetoon      | Project manager, repository owner, release and tagging     | Discuss in the weekly meeting or team chat; majority vote after 24 hours; the section owner breaks a tie; every decision is an issue labelled "decision". |
| Rafay Alvi             | Requirements and change control; acceptance tests from 3.1 | Same rule (/docs/team-agreement.md)                                                                                                                       |
| Eshitasri Punuganti    | Use cases, traceability; P3 test cases from section 4      | Same rule                                                                                                                                                 |
| Xuan Mai Tran          | Detailed design (Chapter 9 class and sequence diagrams)    | Same rule                                                                                                                                                 |
| Isaiah Bueno-Hernandez | Architecture owner; server modules C3–C8                   | Same rule                                                                                                                                                 |
| Len Isherwood          | Live updates (C7) and performance re-measurement           | Same rule                                                                                                                                                 |

### 10.2 Plan to P3

| **Date**             | **What will be finished**                                                                                      | **Owner**                       |
|----------------------|----------------------------------------------------------------------------------------------------------------|---------------------------------|
| 8 Nov                | P2 committed to /docs/p2, tag p2 pushed, PDF uploaded to Canvas                                                | Mohmmad Abuzetoon               |
| 14 Nov               | Follow-up with a server and a kitchen staff member (the interview reached only the manager); Q7 funding answer | Isaiah Bueno-Hernandez          |
| 12 Nov               | Detailed design: design class diagram and design sequence diagrams for UC-01 and UC-07                         | Xuan Mai Tran                   |
| 15 Nov               | Server skeleton for C3–C6 with the database schema (ADR-04)                                                    | Isaiah Bueno-Hernandez          |
| 19 Nov               | Live Update Hub (C7) on the deployed host; spike 01 re-measured with the real database and shared-cart traffic | Len Isherwood                   |
| 22 Nov               | Customer and staff web apps for UC-01 and UC-03 end to end                                                     | Rafay Alvi, Eshitasri Punuganti |
| 26 Nov               | Payment adapter (C8) against the gateway's test mode; UC-07 end to end                                         | Isaiah Bueno-Hernandez          |
| 29 Nov               | Test plan and acceptance tests from 3.1 and 3.2 (Chapter 11)                                                   | Eshitasri Punuganti, Rafay Alvi |
| P3 deadline (Canvas) | P3 document, code and test results committed and tagged                                                        | Mohmmad Abuzetoon               |

### 10.3 Risks

| **\#** | **Risk**                                                                                                        | **Likelihood** | **Impact** | **Mitigation — action and owner**                                                                                           |
|--------|-----------------------------------------------------------------------------------------------------------------|----------------|------------|-----------------------------------------------------------------------------------------------------------------------------|
| R1     | The seven interview changes (CR-11 to CR-17) add work before P3, and the server/kitchen follow-up may add more. | Medium         | High       | Isaiah Bueno-Hernandez raises any change as a CR before 12 Nov; Rafay Alvi re-runs 3.5 and section 9.                       |
| R2     | Push updates fail on the chosen host (connections closed by a proxy).                                           | Medium         | High       | Len Isherwood re-runs spike 01 on the host by 19 Nov; fallback is 1-s polling, measured to meet QR-01 (CR-07).              |
| R3     | Scope creep: split bills, POS integration, loyalty.                                                             | Medium         | Medium     | Rafay Alvi checks every new idea against 1.2 and change control (0.2).                                                      |
| R4     | A member stops contributing.                                                                                    | Medium         | High       | Mohmmad Abuzetoon reviews the issue board every Monday, reassigns work overdue by 3 days, and tells the instructor at once. |
| R5     | Labour runs over 600 hours, pushing cost toward the ceiling.                                                    | Low            | Medium     | Mohmmad Abuzetoon logs hours weekly from 9 Nov; past 450 hours by 1 Dec, SHOULD and COULD items are dropped first (CR-10).  |
| R6     | The payment gateway's test mode is unavailable or needs paperwork.                                              | Medium         | Medium     | Isaiah Bueno-Hernandez opens a test account by 15 Nov; if blocked, C8 is tested against a recorded gateway response.        |

### 10.4 Repository and tooling

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Repository:</strong> https://github.com/mrzetoon/team-01-QRRestaurantOrder — public (or instructor read access before the deadline).</p>
<p><strong>Folders:</strong> /docs/p1 (P1-submitted.pdf, the file on Canvas) · /docs/p2 (this PDF and its .docx) · /docs/p2/diagrams (every diagram's source: .dot, .py, and the images) · /docs/elicitation (interview notes) · /docs/meetings (weekly minutes) · /docs/ai-log.md · /spikes/spike-01-live-orders · /src (from P3).</p>
<p><strong>Branches and pull requests:</strong> main is protected; each member works on p2/&lt;section&gt; and merges through a pull request reviewed by another member.</p>
<p><strong>Issues:</strong> one per P2 section and one per change request, labelled doc, requirement, spike or decision, with an owner and a due date.</p>
<p><strong>Release:</strong> the P2 PDF is committed to /docs/p2 and tagged p2 (git tag p2; git push origin p2) before the same file is uploaded to Canvas by Mohmmad Abuzetoon. No passwords or API keys are committed; the gateway key lives in the host's configuration.</p></td>
</tr>
</tbody>
</table>

### 10.5 Declaration of AI tool use

| **Tool**           | **What it was used for**                                                                               | **Who used it**   | **What we checked or changed**                                                                                                     |
|--------------------|--------------------------------------------------------------------------------------------------------|-------------------|------------------------------------------------------------------------------------------------------------------------------------|
| Claude (Anthropic) | P1: first draft of requirements, use cases and diagrams.                                               | Mohmmad Abuzetoon | Requirements re-checked for testability; stakeholder sources rewritten; placeholders removed.                                      |
| Claude (Anthropic) | P2: draft wording of sections 0.2 and 4–9, diagram scripts (/docs/p2/diagrams), and the spike 01 code. | Mohmmad Abuzetoon | Each owner read and corrected their section; Xuan Mai Tran re-ran K1–K6; Len Isherwood re-ran the spike and checked results.jsonl. |

## 11 Open Questions

| **\#** | **The question**                                                            | **Who can answer it** | **Needed by** | **Status · what we assume meanwhile**                                                                          |
|--------|-----------------------------------------------------------------------------|-----------------------|---------------|----------------------------------------------------------------------------------------------------------------|
| Q1     | Which payment gateway does the restaurant use, and who pays its fee?        | Restaurant owner (S4) | 8 Nov         | Answered \[R9\]: Square; the restaurant pays the processing fee. ADR-03 uses Square's hosted checkout.         |
| Q2     | Is a second order from a table a new order or part of the first?            | Manager, server       | 8 Nov         | Answered \[R9\]: added to the table's original ticket. CR-11 (FR-21 table check).                              |
| Q3     | Can the kitchen cancel one item instead of the whole order?                 | Kitchen staff (S3)    | 8 Nov         | Answered \[R9\]: yes, single items. CR-12 (FR-22).                                                             |
| Q4     | Must a server confirm each order before the kitchen sees it?                | Manager (S4)          | 8 Nov         | Answered \[R9\]: yes, to avoid mistakes. CR-13 (FR-23).                                                        |
| Q5     | Which languages must the menu support?                                      | Manager (S4)          | 8 Nov         | Answered \[R9\]: English and Spanish. CR-14 (FR-24).                                                           |
| Q6     | Must allergen information have a fixed format?                              | Manager (S4)          | 8 Nov         | Answered \[R9\]: common allergens listed on the menu; staff answer questions. CR-15 (FR-25).                   |
| Q7     | Will the restaurant fund about \$43,300 to build and \$4,200 a year to run? | Restaurant owner (S4) | 14 Nov        | Open (not asked at the interview) · the 2.6 estimate stands.                                                   |
| Q8     | If a payment fails or cannot be confirmed, what should staff see?           | Manager (S4)          | 8 Nov         | Answered \[R9\]: a clear payment-failure notification so staff can help the customer pay again. CR-16 (FR-26). |
| Q9     | Should two phones at one table share one cart?                              | Manager, server       | 8 Nov         | Answered \[R9\]: yes. CR-17 (FR-27); ADR-05 reversed.                                                          |
| Q10    | When two phones change the same cart line at once, which change wins?       | Manager (S4)          | 14 Nov        | New (ADR-05) · the last change wins.                                                                           |
| Q11    | Should drinks or simple items skip server confirmation?                     | Manager, server       | 14 Nov        | New (FR-23) · every order is confirmed.                                                                        |

## 12 Baseline Declaration

*We confirm that this document, version 1.0, is our agreed requirements and design baseline as of the submission date, that the PDF on Canvas is the file tagged p2 in the repository, and that every team member has read it in full.*

| **Team member**        | **Signature (typed name)** | **Date**   |
|------------------------|----------------------------|------------|
| Mohmmad Abuzetoon      |                            | 8 Nov 2026 |
| Rafay Alvi             |                            | 8 Nov 2026 |
| Eshitasri Punuganti    |                            | 8 Nov 2026 |
| Xuan Mai Tran          |                            | 8 Nov 2026 |
| Len Isherwood          |                            | 8 Nov 2026 |
| Isaiah Bueno-Hernandez |                            | 8 Nov 2026 |
