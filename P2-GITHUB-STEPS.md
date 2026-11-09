# P2 — how each member commits their section (so the 12 individual points count)

The grader checks: your own commits, your own pull request (PR), and at least one review of a teammate's PR — all **before Sunday 8 Nov, 11:59 PM**.

## Everyone (website only, no terminal needed)
1. Open the repository → **Issues** → find the issue for your section (Mohmmad creates them) → assign yourself.
2. Go to the folder for your files (e.g. `docs/p2/sections/`) → **Add file → Upload files** → drop your file(s).
3. At the bottom choose **"Create a new branch for this commit and start a pull request"**. Name the branch as below. Click **Propose changes → Create pull request**. In the description write `Closes #<issue number>`.
4. Ask a teammate to review. **Every member must also review one teammate's PR:** open it → **Files changed → Review changes → Approve** with a real comment (what you checked).
5. After approval, the author clicks **Merge pull request**.
6. Copy your commit hash (7 characters, shown in the PR) and your PR number into section 0.1 of the document.

| Member | Files to upload | Branch |
|---|---|---|
| Mohmmad | `docs/p2/sections/mohmmad_0-records_10-12-plan.md`, `README.md`, `docs/meetings/*` | `p2/records-plan` |
| The teammate who did the interview | `docs/elicitation/2026-11-08-restaurant-manager-interview.md` (fill the top lines first) | `p2/interview` |
| Rafay | `docs/p2/sections/rafay_1-3-requirements.md`, `docs/p2/diagrams/usecase.py`, `usecase.png`, `context.dot`, `context.png` | `p2/requirements` |
| Eshitasri | `docs/p2/sections/eshitasri_4-use-cases_9-traceability.md` | `p2/use-cases` |
| Xuan Mai | `docs/p2/sections/xuanmai_5-analysis-models.md`, `docs/p2/diagrams/domain.dot`, `domain.png`, `seq.py`, `seq_uc01.png`, `seq_uc07.png` | `p2/analysis-models` |
| Isaiah | `docs/p2/sections/isaiah_6-design_7-adrs.md`, `docs/p2/diagrams/components.dot`, `components.png`, `deployment.dot`, `deployment.png` | `p2/design` |
| Len | everything in `spikes/spike-01-live-orders/` | `p2/spike` |

Read your section before you upload it and change anything that is not true for our team — you are the one who has to defend it.

## Mohmmad only — the final release (Sunday 8 Nov, before 11:59 PM)
1. Put the P1 PDF that was submitted on Canvas in `docs/p1/P1-submitted.pdf`.
2. Save the final document as PDF. Upload it to `docs/p2/` (with the .docx) and commit to `main`.
3. Create the tag on that commit: **Releases → Draft a new release → Choose a tag → type `p2` → Create new tag → target `main` → Publish release.**
   (Terminal alternative: `git tag p2 && git push origin p2`.)
4. Upload **the same PDF** to Canvas. Only you upload. Do not upload a second version.
5. Make the repository public, or give the instructor account read access (Settings → Collaborators).

## Never commit
Passwords, API keys, the payment gateway secret key, or anyone's personal data.
