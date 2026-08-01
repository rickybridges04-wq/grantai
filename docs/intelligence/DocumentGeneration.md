# DocumentGeneration

**Status:** Draft — founder review required
**Phase:** 4 — Intelligence Engine

## Purpose

The mechanical layer `GrantWriter-Agent` calls to actually produce
formatted output — turning drafted narrative + budget content into the file
format a funder expects (PDF, Word doc, web-form-ready text blocks, etc.),
rather than Writer needing to handle formatting itself.

## What It Does

1. Takes Writer's drafted content (narrative sections + budget from
   `BudgetTemplates.md`) plus the funder's required format (from the
   opportunity's record)
2. Assembles the final document structure per `ProposalTemplates.md`
3. Outputs in whatever format the funder requires — this may mean multiple
   output types for the same draft (e.g. a PDF narrative plus a separate
   spreadsheet budget)

## Boundaries

- Pure formatting/assembly — does not originate content, does not make
  judgment calls about what to include (that's Writer's job upstream)
- Output stays in `draft` status in `ApplicationTracker.md` regardless of
  format — generating a polished PDF does not change submission status

## Open Decisions

- [ ] Which output formats need to be supported at launch — depends on
  which funders in `FundingOrganizations.md` get activated first, and what
  their submission portals actually require
