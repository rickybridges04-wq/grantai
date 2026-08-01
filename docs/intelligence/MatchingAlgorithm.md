# MatchingAlgorithm

**Status:** Draft — founder review required
**Phase:** 4 — Intelligence Engine

## Purpose

Once `EligibilityEngine.md` clears an opportunity, MatchingAlgorithm
determines *how well* it fits — not eligible/ineligible, but strong/weak
match. Its output feeds `ScoringSystem.md`, which converts the match
assessment into the numeric fit score everything downstream (drafting
threshold, ranking, Executive Advisor's priority view) depends on.

## Match Factors

- **Category alignment** — does the funder's stated purpose match the
  business's actual work (e.g. a trade-skills or home-improvement-adjacent
  program vs. a generic small-business program)
- **Award size vs. need** — is the award range meaningfully useful, or is
  the effort-to-payout ratio poor
- **Deadline feasibility** — enough lead time to realistically prepare a
  competitive application, factoring in `GrantCompliance-Agent` flags on
  required prerequisites
- **Competitive positioning** — where known (via `GrantResearch-Agent`
  findings in `GrantKnowledge.md`), how the business's profile compares to
  typical awardees
- **Mission/foundation fit** (Foundation category only) — weighted more
  heavily here than in Federal/State, per the note in `FoundationGrants.md`

## Output

A structured match assessment per opportunity — not a single number yet,
but the component ratings `ScoringSystem.md` combines into the final score.
Keeping matching and scoring as separate files/steps means the weighting
logic (how much each factor matters) can be tuned in `ScoringSystem.md`
without touching how each factor itself is assessed here.

## Open Decisions

- [ ] Relative weighting of the five match factors — needs at least one
  real sweep's worth of data to calibrate sensibly rather than guessing
