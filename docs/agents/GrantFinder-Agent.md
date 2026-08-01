# GrantFinder-Agent

**Status:** Draft — founder review required
**Phase:** 2 — AI Agent Specifications
**Type:** On-demand
**Decision-Rights Tier:** Tier 1

## Role

The on-demand counterpart to Grant Hunter. Where Hunter sweeps continuously
across the whole allow-list, Finder answers a specific question: "find me
grants for X" — a business, a project, a funding amount, a deadline window.

## What It Does

1. Takes a query (business profile, project description, or constraint set)
2. Searches the existing knowledge base first (`GrantKnowledge.md` +
   category files); only reaches out to live sources if the ask requires
   fresher data than what's cached
3. Returns a ranked shortlist with fit rationale, not just a raw list
4. Hands off qualifying opportunities to `GrantResearch-Agent` for a deeper
   dive on request

## Boundaries

- Restricted to the same `FundingOrganizations.md` allow-list as Grant
  Hunter — Finder doesn't get to search sources Hunter isn't trusted with
- Does not draft applications (that's `GrantWriter-Agent`) — Finder's job
  ends at "here's what's out there and why it fits"

## Handoff Schema

```
GrantFinder
 ├─ reads: GrantKnowledge.md, FundingOrganizations.md, BusinessProfiles.md
 ├─ calls (on request): GrantResearch-Agent
 └─ output: ranked shortlist + fit rationale
```
