# DatabaseSchema

**Status:** Draft — founder review required
**Phase:** 6 — Engineering

## Purpose

Translates the Markdown record schemas already defined in Phases 3–5
(Opportunity Record, Business Profile, Application Tracker) into actual
Supabase tables. The Markdown files remain the human-readable
source-of-truth for *what* each field means; this file defines *how* it's
stored.

## Core Tables

**`funding_organizations`** — mirrors `FundingOrganizations.md`
- id, name, type (federal/state/corporate/foundation), url, cadence,
  access_method, status, last_swept_at

**`opportunities`** — mirrors the Opportunity Record Schema in
`GrantKnowledge.md`
- id, funding_org_id (FK), name, category, amount_min, amount_max,
  deadline, eligibility_summary, fit_score, status, source_id, created_at,
  updated_at

**`business_profiles`** — mirrors `BusinessProfiles.md`
- id, business_name, entity_type, industry, location, years_operating,
  employee_count, revenue_range, certifications (array), prior_grant_history

**`applications`** — mirrors `ApplicationTracker.md`
- id, opportunity_id (FK), business_profile_id (FK), status, fit_score,
  drafted_by, reviewed_by, compliance_notes, founder_decision,
  submitted_date (nullable — never set by any agent), outcome, updated_at

**`audit_log`** — feeds `AuditLogging.md` (Phase 7)
- id, run_type (hunter_sweep/manual), agent, action, result, error (nullable),
  created_at

## Constraints Worth Enforcing at the DB Level, Not Just the Agent Level

- `applications.submitted_date` should only be settable via a founder-facing
  UI action, not by any service-role API call agents use — enforce this
  with row-level security policy, not just convention, so Tier 4 is
  structurally guaranteed rather than merely agreed upon
- `funding_organizations.status` changes to `active` require the same
  protection — Tier 3, not agent-writable

## Open Decisions

- [ ] Shared Supabase project vs. dedicated — see `Architecture.md`
- [ ] Whether `business_profiles` needs multi-tenancy support now or can
  stay single-business until GrantAI's scope question (logged in
  `GOVERNANCE.md`) is resolved
