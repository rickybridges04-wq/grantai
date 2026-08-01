# GrantAI — Consolidated Open Decisions Checklist

**Purpose:** Every open decision flagged across all 7 phases (35 files),
grouped by theme so it's one pass instead of thirty-five. Check items off
as they're decided — this file itself isn't part of the BAEOS doc
structure, it's a working checklist for founder review before build starts.

## 1. Scope & Governance
*(source: GOVERNANCE.md, EligibilityEngine.md, BusinessProfiles.md)*

- [ ] Does GrantAI operate under full BAEOS governance, or a lighter
  subset — mirrors the same open question BAEOS already has for BHI
- [ ] Which business(es) does GrantAI serve at launch — BHI only, or any
  qualifying BAE portfolio company
- [ ] Who reviews Tier 3/4 decisions if you're unavailable — backup
  approver, or does the queue simply wait
- [ ] Where the authoritative `BusinessProfiles.md` entry is maintained,
  and who updates it when the business's status changes

## 2. Business & Content Data (blank by design — needs you, not a decision)
*(source: BusinessProfiles.md, CommercializationPlans.md)*

- [ ] Populate real `BusinessProfiles.md` data (entity type, revenue range,
  certifications, prior grant history)
- [ ] Confirm what prior commercialization outcomes (if any) are
  appropriate to reference in proposals

## 3. Scoring & Thresholds
*(source: ScoringSystem.md, MatchingAlgorithm.md, GrantHunter-Agent.md,
AutomationWorkflow.md)*

- [ ] Confirm the 70-point Hunter auto-draft threshold (currently a
  starting recommendation, uncalibrated)
- [ ] Set the draft-in-flight cap before Hunter stops auto-drafting and
  just flags instead — interacts with the threshold above
- [ ] Relative weighting of the five match factors in
  `MatchingAlgorithm.md` — needs real sweep data to calibrate
- [ ] What happens to a "review-failed" draft — one automatic revision
  pass then stop, or stop immediately for founder input

## 4. Sources & Funding Data
*(source: FundingOrganizations.md, BudgetTemplates.md)*

- [ ] Every source in `FundingOrganizations.md` is currently **Pending
  founder approval** — nothing sweeps until Federal/State rows (at least)
  are reviewed and activated
- [ ] Research and name 3–5 specific Corporate programs before that
  category goes live (no generic search source)
- [ ] Research and name specific Foundation programs before that category
  goes live (mission-fit driven, not broad search)
- [ ] Confirm whether matching funds are realistically available for
  grants that require them

## 5. Knowledge Base Mechanics
*(source: ProposalTemplates.md, ApplicationTracker.md, DocumentGeneration.md)*

- [ ] Build first real proposal templates against actual funder
  requirements once specific sources are activated (not genericized in
  advance)
- [ ] How "outcome" gets recorded on a submitted application — manual
  update, or Hunter periodically checks for award announcements
- [ ] Which output document formats need support at launch (PDF, Word,
  form-ready text) — depends on which funders go live first

## 6. Infrastructure
*(source: Architecture.md, DatabaseSchema.md, API.md, Security.md,
Testing.md)*

- [ ] Shared Supabase project (with other BAE apps) vs. dedicated project
  for GrantAI — this decision cascades into Security.md's RLS policies and
  DatabaseSchema.md's multi-tenancy question
- [ ] Whether `business_profiles` needs multi-tenancy support now, or can
  stay single-business until the Scope decision (#1) is resolved
- [ ] Confirm GrantAI's API stays internal-only, or needs external access
  later (relevant if GrantAI becomes its own offered product per the
  Stage 3 vision in `VISION.md`)
- [ ] Separate Supabase project/branch for testing vs. production, so
  Hunter test runs don't pollute real data

## 7. Deployment & Operations
*(source: Deployment.md, StandardOperatingProcedures.md, QualityControl.md,
ContinuousLearning.md, AuditLogging.md, Metrics.md)*

- [ ] Exact cron cadence per source category — needs sources activated
  first (Federal/State likely daily, Corporate/Foundation likely weekly)
- [ ] Digest notification path — email via Resend, in-app, or both
- [ ] Confirm actual weekly/monthly review cadence once real sweep volume
  is known
- [ ] Minimum sample size before scoring/eligibility quality claims are
  meaningful rather than anecdotal
- [ ] How much outcome history is needed before a threshold change in
  `ScoringSystem.md` is justified
- [ ] Audit log retention period — indefinite, or archived after some
  period
- [ ] Set real win-rate/volume targets — deliberately not set yet;
  recommend waiting for one full quarter of live data

## Suggested Order of Attack

1. **Scope & Governance (#1)** first — several other decisions (multi-
   tenancy, business profile ownership) cascade from this
2. **Sources (#4)** — nothing else runs until at least Federal/State
   sources are activated
3. **Business & Content Data (#2)** — needed before any real draft can be
   produced
4. **Scoring & Thresholds (#3)** and **Infrastructure (#6)** in parallel —
   these inform each other but don't block each other
5. **Knowledge Base Mechanics (#5)** and **Deployment & Operations (#7)**
   last — these are easiest to finalize once everything above is settled
