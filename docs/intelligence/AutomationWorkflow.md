# AutomationWorkflow

**Status:** Draft — founder review required
**Phase:** 4 — Intelligence Engine

## Purpose

Documents the end-to-end sequence connecting every Phase 4 component, so
the Intelligence Engine reads as one pipeline rather than four disconnected
files. This is the reference `Architecture.md` (Phase 6) will formalize into
actual system design.

## The Pipeline

```
New opportunity found (GrantHunter or GrantFinder)
        │
        ▼
EligibilityEngine.md ──► Ineligible? → log reason, stop
        │
        ▼ Eligible / Eligible with prerequisites
MatchingAlgorithm.md ──► component match assessment
        │
        ▼
ScoringSystem.md ──► fit score (0–100)
        │
        ├─ 0–39 (Low)      → log to knowledge base only
        ├─ 40–69 (Moderate)→ log + surface to Executive Advisor
        └─ 70–100 (High)   → trigger draft
                │
                ▼
        GrantWriter-Agent (narrative + budget)
                │
                ▼
        DocumentGeneration.md (formatting/assembly)
                │
                ▼
        GrantReviewer-Agent (QA pass)
                │
                ▼
        ApplicationTracker.md (status: review-passed, awaiting founder)
                │
                ▼
        Founder decision (Tier 4 — submit, revise, or decline)
```

## Where Human Judgment Enters

Two points in this pipeline are hard-gated for founder involvement, not
agent discretion:

1. **Source allow-list** (`FundingOrganizations.md`) — Tier 3, upstream of
   everything
2. **Submission** — Tier 4, downstream of everything, no exceptions

Every step between those two gates can run without a human in the loop —
that's what makes Grant Hunter's autonomy safe rather than reckless.

## Open Decisions

- [ ] What happens to a "review-failed" draft — does it go back to Writer
  automatically for one revision pass, or does it stop and wait for founder
  input? (Recommend: one automatic revision pass, then stop — avoids an
  infinite draft-revise loop.)
