# Architecture

**Status:** Draft — founder review required
**Phase:** 6 — Engineering

## Purpose

Formalizes the conceptual pipeline from `AutomationWorkflow.md` into an
actual system design — matching BAE's standard stack (Lovable/React+Vite
frontend, Supabase backend, Stripe if billing applies, Resend for email,
Anthropic API for agent reasoning) rather than introducing a new stack for
this one module.

## High-Level Components

```
┌─────────────────────────────────────────────────┐
│  Scheduler (Grant Hunter trigger)                │
│  — cron / GitHub Action, per Deployment.md       │
└───────────────────┬───────────────────────────────┘
                     ▼
┌─────────────────────────────────────────────────┐
│  Agent Layer (Anthropic API calls)               │
│  Hunter, Finder, Writer, Reviewer, Research,     │
│  Compliance, Executive Advisor                   │
└───────────────────┬───────────────────────────────┘
                     ▼
┌─────────────────────────────────────────────────┐
│  Data Layer (Supabase)                           │
│  Opportunities, BusinessProfiles, Applications,  │
│  AuditLog — see DatabaseSchema.md                │
└───────────────────┬───────────────────────────────┘
                     ▼
┌─────────────────────────────────────────────────┐
│  Frontend (Lovable/React+Vite)                   │
│  Founder-facing dashboard, Executive Advisor      │
│  view, ApplicationTracker UI                      │
└─────────────────────────────────────────────────┘
```

## Design Principles

1. **Agents are stateless callers, Supabase holds state.** No agent keeps
   memory of its own between runs — every read/write goes through the data
   layer, consistent with BAEOS's read-before-write Memory Protocol.
2. **Scheduler triggers Hunter; nothing else runs unprompted.** Every other
   agent is called synchronously by Hunter or by a founder action in the
   frontend — no other background processes.
3. **Tier 4 actions have no API path.** There is no function in this
   architecture that submits an application — submission happens outside
   the system, by the founder, on the funder's own portal. The tracker
   records that it happened; it doesn't cause it.

## Open Decisions

- [ ] Single Supabase project shared with other BAE apps, or dedicated
  project for GrantAI — affects `DatabaseSchema.md` and `Security.md`
