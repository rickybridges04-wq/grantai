# FundingOrganizations

**Status:** Draft — founder review required
**Phase:** 3 — Knowledge Base
**Decision-Rights Tier:** Tier 3 — additions/removals require founder approval

## Purpose

This is the allow-list. Grant Hunter, GrantFinder, and GrantResearch may
only pull opportunity data from sources listed here. No agent may add,
remove, or substitute a source on its own — that's a Tier 3 decision per
`GOVERNANCE.md`. This file existing and being deliberately small at launch
is a feature, not a gap: better to sweep five trustworthy sources reliably
than fifty unverified ones badly.

## Source Entry Format

Each source gets an entry with:
- **Name**
- **Type** (Federal / State / Corporate / Foundation)
- **URL**
- **Update cadence** (how often it posts new listings, informs Hunter's
  sweep schedule)
- **Access method** (public search, API, requires login/registration)
- **Status** (Active / Pending founder approval / Suspended)

## Federal

| Name | URL | Cadence | Access | Status |
|---|---|---|---|---|
| Grants.gov | grants.gov | Daily | Public search | Pending founder approval |
| SAM.gov (entity/award data) | sam.gov | Daily | Public search | Pending founder approval |
| SBA.gov funding programs | sba.gov | Weekly | Public | Pending founder approval |

## State (Indiana-focused, given BHI's service area)

| Name | URL | Cadence | Access | Status |
|---|---|---|---|---|
| Indiana Economic Development Corporation (IEDC) | iedc.in.gov | Weekly | Public | Pending founder approval |
| Indiana state grants portal | in.gov | Weekly | Public | Pending founder approval |

## Corporate

_No sources approved yet. Corporate grant programs (e.g. major bank/vendor
small business grant programs) tend to be seasonal and application-window
based rather than continuously open — recommend populating this after
Phase 3 review with named programs rather than a generic search source._

## Foundation

_No sources approved yet — same reasoning as Corporate. Foundation grants
are highly fit-dependent (mission alignment matters more than eligibility
boxes), so this list should be populated deliberately, not swept broadly._

## Founder Action Required

Every source above is listed as **Pending founder approval** — none are
live yet. Nothing in Phase 3 knowledge base or Phase 4 scoring can safely
run until at least the Federal and State rows are reviewed and flipped to
Active. This is intentional: the allow-list should never auto-activate.

## Change Log

_(Populate as sources are added, removed, or suspended — required for audit
trail per `AuditLogging.md` once Phase 7 is built.)_
