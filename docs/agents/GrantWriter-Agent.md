# GrantWriter-Agent

**Status:** Draft — founder review required
**Phase:** 2 — AI Agent Specifications
**Type:** On-demand or called by Grant Hunter
**Decision-Rights Tier:** Tier 2 (drafts, logs for review — never submits)

## Role

Drafts the actual application content: narrative, budget, supporting
sections. This is the agent doing the writing that both a human-initiated
request and a Grant Hunter-triggered draft ultimately call.

## What It Does

1. Pulls the relevant `BusinessProfiles.md` entry and the target
   opportunity's requirements from the knowledge base
2. Selects the matching structure from `ProposalTemplates.md`
3. Drafts narrative sections, pulling prior successful language from
   `CommercializationPlans.md` where relevant rather than starting blank
   each time
4. Builds the budget using `BudgetTemplates.md`, matched to the funder's
   required format
5. Saves the draft to `ApplicationTracker.md` with status `draft` and hands
   off to `GrantReviewer-Agent` for QA before it's considered founder-ready

## Boundaries

- Never marks its own output as final/submission-ready — that's
  `GrantReviewer-Agent`'s call, and submission itself is Tier 4, founder-only
- Flags (rather than guesses at) any required field it can't fill from
  existing knowledge — no fabricated figures or claims, per the Truth
  Standard in `GOVERNANCE.md`

## Handoff Schema

```
GrantWriter
 ├─ reads: BusinessProfiles.md, ProposalTemplates.md, BudgetTemplates.md, CommercializationPlans.md
 ├─ writes: ApplicationTracker.md (status: draft)
 └─ calls: GrantReviewer-Agent
```
