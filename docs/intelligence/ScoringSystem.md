# ScoringSystem

**Status:** Draft — founder review required
**Phase:** 4 — Intelligence Engine

## Purpose

Converts `MatchingAlgorithm.md`'s component assessment into a single fit
score per opportunity. This score is the number referenced everywhere else
in the system: `GrantKnowledge.md`'s record schema, `ApplicationTracker.md`
sorting, Executive Advisor's priority view, and — most consequentially —
the threshold `GrantHunter-Agent` uses to decide whether to prepare a draft
application automatically.

## Score Scale

0–100, computed from the weighted match factors in `MatchingAlgorithm.md`.
Recommend three bands rather than a raw number alone, since a bare number
invites false precision:

- **0–39 — Low fit.** Logged in the knowledge base, not drafted, not
  surfaced to Executive Advisor's priority view unless the founder asks
- **40–69 — Moderate fit.** Logged and surfaced to Executive Advisor as
  "worth a look," but not auto-drafted
- **70–100 — High fit.** This is the **Hunter draft threshold** — clearing
  this band is what triggers Grant Hunter to hand off to `GrantWriter-Agent`
  for an automatic draft, per `GrantHunter-Agent.md` step 7

## Why a Threshold, Not "Draft Everything Eligible"

Drafting is expensive (Writer + Reviewer + Compliance all run), and a
founder can only review so many drafts. The threshold exists to keep Hunter
useful rather than noisy — see the "Draft sprawl" failure mode already
flagged in `GrantHunter-Agent.md`.

## Calibration

The 70-point threshold is a starting recommendation, not a fixed rule. It
should move based on real outcomes tracked in `ContinuousLearning.md` (Phase
7) — if drafts above threshold are consistently not worth pursuing, raise
it; if strong opportunities are landing just under it, lower it or revisit
the weighting in `MatchingAlgorithm.md`.

## Open Decisions

- [ ] Confirm the 70-point threshold and the draft-in-flight cap referenced
  in `GrantHunter-Agent.md` together — they interact (a lower threshold
  with a low cap means good opportunities get silently deprioritized)
