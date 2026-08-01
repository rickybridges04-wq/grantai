# EligibilityEngine

**Status:** Draft — founder review required
**Phase:** 4 — Intelligence Engine

## Purpose

Determines whether a business is eligible for a given grant opportunity
before any time is spent scoring fit or drafting. This is the first gate
every new opportunity passes through — Grant Hunter calls it on every new
listing, Finder calls it on every query result.

## Inputs

- The opportunity's eligibility summary (from its record in
  `FederalGrants.md` / `StateGrants.md` / etc., enriched by
  `GrantCompliance-Agent`)
- The relevant `BusinessProfiles.md` entry (entity type, size, location,
  years in operation, prior awards, certifications held)

## Logic

1. **Hard filters** — binary pass/fail checks with no scoring involved:
   entity type match, geographic eligibility, size standard, prior-award
   exclusions, required certifications/registrations already in place
2. **Soft filters** — conditions that are possible to satisfy but require
   action before applying (e.g. "SAM.gov registration required" — not
   disqualifying, but flagged as a prerequisite)
3. **Output:** `Eligible` / `Ineligible` / `Eligible with prerequisites`,
   plus the specific reason in every case — never a bare pass/fail with no
   rationale, since that rationale is what gets logged for audit and what a
   founder needs to sanity-check a surprising result

## Boundaries

- Only determines eligibility — does not score fit (that's
  `MatchingAlgorithm.md` + `ScoringSystem.md`) and does not assess
  obligations post-award (that's `GrantCompliance-Agent`'s deeper pass)
- An `Ineligible` result is logged, not deleted — Grant Hunter's digest
  needs to show what was checked and ruled out, not just what passed

## Open Decisions

- [ ] Where does the authoritative `BusinessProfiles.md` entry get
  maintained, and who updates it when the business's own status changes
  (new certification, change in size, etc.)?
