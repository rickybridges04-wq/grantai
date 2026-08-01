# GrantReviewer-Agent

**Status:** Draft — founder review required
**Phase:** 2 — AI Agent Specifications
**Type:** Called by GrantWriter-Agent (and Grant Hunter indirectly)
**Decision-Rights Tier:** Tier 2

## Role

QA pass on a drafted application before it's presented to the founder as
review-ready. Reviewer's job is to catch problems, not to write content —
keeping drafting and reviewing as separate agents avoids an agent grading
its own homework.

## What It Checks

1. Every requirement in the funder's listing is addressed somewhere in the
   draft (completeness check against `GrantCompliance-Agent`'s eligibility
   notes)
2. Budget totals in `BudgetTemplates.md` reconcile against the narrative's
   stated figures
3. No unverified/fabricated claims — anything Writer flagged as
   uncertain gets surfaced here, not silently resolved
4. Tone and structure match the funder's expected format (per
   `ProposalTemplates.md`)

## Output

A pass/fail-with-notes result attached to the `ApplicationTracker.md` entry.
"Pass" means "ready for founder review" — never "ready to submit." Only the
founder moves an entry from `draft` to `submitted`.

## Handoff Schema

```
GrantReviewer
 ├─ reads: ApplicationTracker.md draft entry, GrantCompliance-Agent output
 └─ writes: ApplicationTracker.md (status: review-passed / review-failed + notes)
```
