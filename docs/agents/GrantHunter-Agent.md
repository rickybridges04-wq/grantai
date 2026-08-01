# GrantHunter-Agent

**Status:** Draft — founder review required
**Phase:** 2 — AI Agent Specifications
**Type:** Scheduled/autonomous (not on-demand)
**Decision-Rights Tier:** Operates at Tier 1–2 for search/score/draft; hard-blocked from Tier 4 (submission)

## Role

Grant Hunter is the only GrantAI agent that runs on a schedule instead of
being invoked. It is the mechanism that turns GrantAI from "ask it to find a
grant" into "it already found the grant." Every other agent in this system
can be thought of as a capability Grant Hunter calls on its sweep.

## Trigger

- Runs on a fixed schedule (recommend: daily for federal/state sources,
  weekly for corporate/foundation sources — cadence should follow how often
  each source type actually posts new listings; see `Deployment.md` in
  Phase 6 for the actual cron/GitHub Action mechanism)
- Can also be triggered manually by the founder for an ad-hoc sweep

## What It Does, In Order

1. **Load the allow-list.** Reads `FundingOrganizations.md` — Grant Hunter
   may only query sources on this list. It cannot add a source to its own
   allow-list (Tier 3 decision, founder-only).
2. **Sweep.** Queries each approved source for new or updated listings since
   its last successful run.
3. **Diff.** Compares results against the existing knowledge base
   (`GrantKnowledge.md` + the relevant `FederalGrants.md` /
   `StateGrants.md` / `CorporateGrants.md` / `FoundationGrants.md` file) to
   isolate what's actually new.
4. **Eligibility check.** Passes each new listing through the
   `EligibilityEngine.md` against the relevant `BusinessProfiles.md` entry.
   Anything ineligible is logged and dropped — not deleted, logged, so the
   reasoning is auditable.
5. **Score.** Anything eligible goes through `MatchingAlgorithm.md` +
   `ScoringSystem.md` to get a fit score.
6. **Update knowledge base.** Anything eligible gets written into the
   knowledge base regardless of score — Grant Hunter's job is to build a
   complete picture, not just a curated one.
7. **Draft (conditional).** Anything that clears the "high-value" threshold
   defined in `ScoringSystem.md` gets a draft application package prepared
   using `GrantWriter-Agent` + `ProposalTemplates.md` + `BudgetTemplates.md`.
   The draft is saved to `ApplicationTracker.md` in `draft` status. It is
   never submitted, sent, emailed, or otherwise transmitted outside the
   system by Grant Hunter or any other agent.
8. **Digest.** Produces a run log per `AuditLogging.md`: sources checked,
   new listings found, eligible count, scored count, drafts prepared,
   anything that errored. A zero-result run still produces a digest — the
   absence of a digest is itself a failure signal.

## What It Never Does

- Never submits an application
- Never expands its own source allow-list
- Never silently discards an ineligible or low-scoring opportunity — logs
  it with the reason
- Never reports success on a step it didn't actually complete (Truth
  Standard — see `GOVERNANCE.md`)
- Never overwrites a founder's manual edit to a drafted application; if the
  underlying opportunity data changes after a founder has started editing a
  draft, it flags the conflict rather than resolving it unilaterally

## Handoff Schema (calls made per run)

```
GrantHunter
 ├─ reads: FundingOrganizations.md, GrantKnowledge.md, BusinessProfiles.md
 ├─ calls: EligibilityEngine → eligible/ineligible + reason
 ├─ calls: MatchingAlgorithm + ScoringSystem → fit score
 ├─ writes: FederalGrants.md / StateGrants.md / CorporateGrants.md / FoundationGrants.md
 ├─ calls (conditional, score > threshold): GrantWriter-Agent, GrantCompliance-Agent
 ├─ writes: ApplicationTracker.md (status: draft)
 └─ writes: AuditLogging.md (run digest)
```

## Failure Modes to Design Against

- **Stale source access** (a funding site changes structure/login and Hunter
  silently returns zero results indefinitely) — mitigated by requiring the
  digest to distinguish "checked, zero new listings" from "could not
  access source."
- **Threshold drift** (scoring model changes over time in a way that quietly
  stops surfacing anything) — mitigated by `ContinuousLearning.md` tracking
  score distribution over time, not just pass/fail counts.
- **Draft sprawl** (Hunter prepares drafts faster than the founder can
  review them) — mitigated by capping drafts-in-flight and surfacing the
  cap-hit condition in the digest rather than queueing silently.

## Open Decisions (Blocking)

- [ ] What is the actual scoring threshold for "high-value, draft it"? Needs
  `ScoringSystem.md` to exist first.
- [ ] What's the draft-in-flight cap before Hunter stops preparing new
  drafts and just flags them?
- [ ] Does a rejected/expired opportunity get removed from the knowledge
  base or archived in place?
