# AGENTS.md — GrantAI

This is the lean router for the GrantAI repo, matching the pattern used
across the rest of the Bridges AI Enterprises portfolio. Full context lives
in `docs/`; this file exists so any agent or contributor knows where to
look first.

## What This Repo Is

GrantAI — a Grant Intelligence Operating System, built as a BAEOS enterprise
module. See `docs/README.md` for the full overview.

## Where Things Are

- `docs/README.md`, `GOVERNANCE.md`, `MISSION.md`, `VISION.md`,
  `ROADMAP.md` — Foundation
- `docs/agents/` — the 7 agent specs (GrantFinder, GrantWriter,
  GrantReviewer, GrantResearch, GrantCompliance, GrantHunter,
  ExecutiveGrantAdvisor)
- `docs/knowledge/` — GrantKnowledge + funder allow-list + category files
- `docs/intelligence/` — Eligibility, Matching, Scoring, Document
  Generation, Automation Workflow
- `docs/application/` — Proposal/Budget templates, Business Profiles,
  Commercialization Plans, Application Tracker
- `docs/engineering/` — Architecture, Database Schema, API, Security,
  Testing, Deployment
- `docs/operations/` — SOPs, Quality Control, Continuous Learning, Audit
  Logging, Metrics (Phase 7 — not yet built)

## Non-Negotiables (read `GOVERNANCE.md` for full detail)

1. **Tier 3** — `docs/knowledge/FundingOrganizations.md` is an allow-list.
   No agent adds or activates a source on its own.
2. **Tier 4** — No agent, under any circumstance, submits an application.
   Enforced at the database/API layer (`docs/engineering/Security.md`),
   not just by convention.
3. **Truth Standard** — fabrication (a false "submitted," an invented
   eligibility rule, an inflated fit score) is worse than an honest
   failure. Applies to every agent in `docs/agents/`.

## Full Build Audit Mode

Same trigger clause as the rest of the BAE portfolio: saying "AGENTS.md —
go to work" loads full context and runs a 5-pass QA sweep, auto-committing
a dated report to `docs/audits/` plus a rollup line in `docs/AUDIT_LOG.md`.
Tier 3/4 findings still require founder approval before any fix executes.

## External Modules

### → partnerai
Repo: https://github.com/rickybridges04-wq/Partnerai

GrantAI's ExecutiveGrantAdvisor may call PartnerAI's StrategyAdvisor
to check portfolio-priority scoring before drafting an application.
Shared Supabase tables: portfolio_apps, funding_opportunities,
shared_handoff_log.
