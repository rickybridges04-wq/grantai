# API

**Status:** Draft — founder review required
**Phase:** 6 — Engineering

## Purpose

Defines the internal API surface agents and the frontend use to interact
with the data layer — not a public API, since GrantAI at this stage is an
internal BAE tool, not a product with external API consumers.

## Endpoint Groups

**Opportunities**
- `GET /opportunities` — list, filterable by category/status/score
- `POST /opportunities` — create (called by Hunter/Finder after
  Eligibility + Matching + Scoring)
- `PATCH /opportunities/:id` — update (e.g. Research-Agent enrichment)

**Applications**
- `GET /applications` — list, filterable by status
- `POST /applications` — create draft (Writer-Agent)
- `PATCH /applications/:id/status` — status transitions; the `submitted`
  transition is restricted to founder-authenticated frontend calls only,
  never the service-role key agents use (see `Security.md`)

**Funding Organizations**
- `GET /funding_organizations`
- `PATCH /funding_organizations/:id` — status changes; same Tier 3
  restriction as above, founder-only

**Hunter Runs**
- `POST /hunter/run` — manual trigger (founder or scheduler-invoked)
- `GET /hunter/runs/:id` — digest retrieval for a specific run

## Authentication

Two distinct credential types, deliberately kept separate:
1. **Service-role key** — used by scheduled/agent processes; scoped to
   read/write on opportunities and applications, explicitly *not* permitted
   on the `submitted` status transition or `funding_organizations.status`
2. **Founder session auth** — used by the frontend; the only credential
   type that can perform Tier 3/4 actions

## Open Decisions

- [ ] Confirm this stays internal-only, or if a future version needs
  external API access (e.g. if GrantAI becomes its own offered product per
  the Stage 3 vision)
