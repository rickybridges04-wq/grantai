# FederalGrants

**Status:** Draft — awaiting first sweep
**Phase:** 3 — Knowledge Base
**Category:** Federal

## Purpose

Holds federal grant opportunity records, using the Opportunity Record
Schema defined in `GrantKnowledge.md`. Populated by `GrantFinder-Agent`
(on-demand) and `GrantHunter-Agent` (scheduled sweep) once the Federal rows
in `FundingOrganizations.md` are activated.

## Entries

_No entries yet — this file populates once Federal sources in
`FundingOrganizations.md` are flipped from "Pending founder approval" to
"Active" and a first sweep runs._

## Notes

- Federal grants typically carry the strictest compliance/reporting
  requirements in the portfolio — `GrantCompliance-Agent` should be run
  against every entry here before anything moves to draft status
- SAM.gov registration (if not already in place for the applying business)
  is a common prerequisite that should be checked early, not discovered at
  application time
