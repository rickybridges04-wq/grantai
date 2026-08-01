# QualityControl

**Status:** Draft — founder review required
**Phase:** 7 — Operations

## Purpose

Defines how GrantAI's actual output quality (draft quality, scoring
accuracy, eligibility accuracy) gets checked on an ongoing basis — distinct
from `Testing.md` (Phase 6), which verifies the system works as built.
Quality Control verifies the system's *judgment* stays good over time.

## Draft Quality Checks

- `GrantReviewer-Agent`'s pass/fail rate over time — a rising fail rate on
  drafts signals `GrantWriter-Agent`'s templates or source material
  (`ProposalTemplates.md`, `CommercializationPlans.md`) need attention
- Periodic founder spot-check of a `review-passed` draft even when not
  required — catches issues Reviewer's automated checks might miss

## Scoring Quality Checks

- Compare `ScoringSystem.md` fit scores against actual outcomes
  (`ApplicationTracker.md` awarded/declined) — this is the core input to
  `ContinuousLearning.md`'s recalibration
- Watch for score clustering (everything landing in one band) as a signal
  the weighting in `MatchingAlgorithm.md` needs adjustment

## Eligibility Quality Checks

- Any `Ineligible` determination that a founder manually overrides gets
  logged and reviewed — either the override was right (feed back into
  `EligibilityEngine.md` logic) or it wasn't (documented as a near-miss to
  avoid repeating)

## Standard

Consistent with BAEOS's evidence-based Definition of Done: a quality claim
("scoring is accurate," "drafts are good") needs to be backed by tracked
data over time, not asserted from a handful of good runs.

## Open Decisions

- [ ] Minimum sample size before scoring/eligibility quality claims are
  considered meaningful rather than anecdotal
