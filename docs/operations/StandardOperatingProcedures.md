# StandardOperatingProcedures

**Status:** Draft — founder review required
**Phase:** 7 — Operations

## Purpose

The human-facing operating manual — what the founder actually does,
routinely, to keep GrantAI running well. Everything before this phase
defined what the system does; this defines what the founder's own recurring
role in it is.

## Weekly Routine

1. Check `ExecutiveGrantAdvisor-Agent`'s priority view (drafts awaiting
   review, deadlines approaching)
2. Review any `review-passed` draft in `ApplicationTracker.md` — approve to
   submit, request revision, or decline
3. Scan the latest Grant Hunter digest (`AuditLogging.md`) — confirm sources
   swept successfully, note anything that errored

## Monthly Routine

1. Review `FundingOrganizations.md` — any new sources to add (Tier 3
   decision), any source consistently underperforming/erroring to suspend
2. Spot-check a handful of `Low`/`Moderate` scored opportunities — confirm
   `ScoringSystem.md`'s threshold still feels right, not just trust it
   silently
3. Review `Metrics.md` rollup — applications drafted, submitted, win rate

## When Something Goes Wrong

- **Hunter digest shows a source error** → check the source manually; if
  structurally changed, flag for `GrantResearch-Agent`/founder review of
  whether it needs a new access method
- **A drafted application has a factual error** → this is a Truth Standard
  incident per `GOVERNANCE.md`; log it the same way BAEOS already logs
  agent fabrication incidents, don't just quietly fix and move on
- **Founder disagrees with a fit score** → note it; feeds
  `ContinuousLearning.md`'s calibration loop rather than being a one-off
  override

## Open Decisions

- [ ] Confirm actual review cadence (weekly/monthly above are
  recommendations) once real sweep volume is known
