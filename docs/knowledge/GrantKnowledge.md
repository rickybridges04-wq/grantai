# GrantKnowledge

**Status:** Draft — founder review required
**Phase:** 3 — Knowledge Base

## Purpose

The central index and shared knowledge layer for everything GrantAI learns
about grants, funders, and the grant-seeking process in general. Category
files (`FederalGrants.md`, `StateGrants.md`, `CorporateGrants.md`,
`FoundationGrants.md`) hold the actual opportunity listings; this file holds
what's true across all of them — patterns, terminology, and the general
knowledge that makes GrantAI's agents competent rather than just
search-and-match tools.

## What Lives Here

- **Grant terminology glossary** — matching funds, indirect cost rate,
  letter of intent vs. full proposal, etc. — so every agent interprets
  funder language consistently
- **Cross-cutting patterns learned over time** (e.g. "federal grants in
  category X typically require Y lead time before deadline") — populated by
  `GrantResearch-Agent` and refined by `ContinuousLearning.md` once Phase 7
  exists
- **Opportunity record schema** — the shared structure every entry in the
  category files follows, so `EligibilityEngine.md` and `MatchingAlgorithm.md`
  can process any category file identically

## Opportunity Record Schema

Every grant listing in any category file uses this structure:

```
- Name:
- Funder:
- Category: (Federal / State / Corporate / Foundation)
- Amount range:
- Deadline:
- Eligibility summary:
- Fit score: (populated by ScoringSystem.md — not filled at ingestion)
- Source: (which entry in FundingOrganizations.md this came from)
- Status: (new / reviewed / pursuing / drafted / submitted / awarded / declined / expired)
- Last updated:
```

## Notes

This file starts thin by design — it's meant to accumulate real, learned
knowledge, not be pre-filled with assumptions about what patterns will
emerge. The first entries should come from actual sweeps once
`FundingOrganizations.md` sources are activated.
