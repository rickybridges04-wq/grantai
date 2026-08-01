# GrantAI — Complete File List & GitHub Commit Guide

**36 files total.** This is the full inventory plus copy-paste git commands
to commit everything in the same phase order it was built, so your commit
history reads as a build log rather than one giant dump.

Assumes you've cloned the repo locally and all 36 files (from this chat's
outputs) are sitting somewhere on your machine, e.g. `~/Downloads/grantai-files/`.
Adjust paths as needed.

---

## Full File Inventory

**Root (1 file)**
- `AGENTS.md`

**Phase 1 — Foundation (5 files)** → `docs/`
- `README.md`
- `GOVERNANCE.md`
- `MISSION.md`
- `VISION.md`
- `ROADMAP.md`

**Phase 2 — Agent Specifications (7 files)** → `docs/agents/`
- `GrantHunter-Agent.md`
- `GrantFinder-Agent.md`
- `GrantWriter-Agent.md`
- `GrantReviewer-Agent.md`
- `GrantResearch-Agent.md`
- `GrantCompliance-Agent.md`
- `ExecutiveGrantAdvisor-Agent.md`

**Phase 3 — Knowledge Base (6 files)** → `docs/knowledge/`
- `FundingOrganizations.md`
- `GrantKnowledge.md`
- `FederalGrants.md`
- `StateGrants.md`
- `CorporateGrants.md`
- `FoundationGrants.md`

**Phase 4 — Intelligence Engine (5 files)** → `docs/intelligence/`
- `EligibilityEngine.md`
- `MatchingAlgorithm.md`
- `ScoringSystem.md`
- `DocumentGeneration.md`
- `AutomationWorkflow.md`

**Phase 5 — Application System (5 files)** → `docs/application/`
- `ProposalTemplates.md`
- `BusinessProfiles.md`
- `BudgetTemplates.md`
- `CommercializationPlans.md`
- `ApplicationTracker.md`

**Phase 6 — Engineering (6 files)** → `docs/engineering/`
- `Architecture.md`
- `DatabaseSchema.md`
- `API.md`
- `Security.md`
- `Testing.md`
- `Deployment.md`

**Phase 7 — Operations (5 files)** → `docs/operations/`
- `StandardOperatingProcedures.md`
- `QualityControl.md`
- `ContinuousLearning.md`
- `AuditLogging.md`
- `Metrics.md`

**Checklist (1 file)** → `docs/`
- `OPEN_DECISIONS.md`

**Total: 1 + 5 + 7 + 6 + 5 + 5 + 6 + 5 + 1 = 36 files** ✓

---

## Commit Plan — One Commit Per Phase

### Step 0 — One-time setup

```bash
cd ~/path/to/grantai          # or wherever you cloned/init'd the repo
mkdir -p docs/agents docs/knowledge docs/intelligence docs/application docs/engineering docs/operations
```

### Phase 1 — Foundation

```bash
# copy README.md, GOVERNANCE.md, MISSION.md, VISION.md, ROADMAP.md into docs/
cp ~/Downloads/grantai-files/{README,GOVERNANCE,MISSION,VISION,ROADMAP}.md docs/

git add docs/README.md docs/GOVERNANCE.md docs/MISSION.md docs/VISION.md docs/ROADMAP.md
git commit -m "GrantAI Phase 1: Foundation (README, GOVERNANCE, MISSION, VISION, ROADMAP)"
git push
```

### Phase 2 — Agent Specifications

```bash
cp ~/Downloads/grantai-files/*-Agent.md docs/agents/

git add docs/agents/
git commit -m "GrantAI Phase 2: Agent Specifications (7 agents, GrantHunter as flagship)"
git push
```

### Phase 3 — Knowledge Base

```bash
cp ~/Downloads/grantai-files/{GrantKnowledge,FundingOrganizations,FederalGrants,StateGrants,CorporateGrants,FoundationGrants}.md docs/knowledge/

git add docs/knowledge/
git commit -m "GrantAI Phase 3: Knowledge Base (funder allow-list + category files)"
git push
```

### Phase 4 — Intelligence Engine

```bash
cp ~/Downloads/grantai-files/{EligibilityEngine,MatchingAlgorithm,ScoringSystem,DocumentGeneration,AutomationWorkflow}.md docs/intelligence/

git add docs/intelligence/
git commit -m "GrantAI Phase 4: Intelligence Engine (eligibility, matching, scoring, workflow)"
git push
```

### Phase 5 — Application System

```bash
cp ~/Downloads/grantai-files/{ProposalTemplates,BusinessProfiles,BudgetTemplates,CommercializationPlans,ApplicationTracker}.md docs/application/

git add docs/application/
git commit -m "GrantAI Phase 5: Application System (templates, profiles, tracker)"
git push
```

### Phase 6 — Engineering (includes root AGENTS.md)

```bash
cp ~/Downloads/grantai-files/{Architecture,DatabaseSchema,API,Security,Testing,Deployment}.md docs/engineering/
cp ~/Downloads/grantai-files/AGENTS.md .          # note: repo root, not docs/

git add docs/engineering/ AGENTS.md
git commit -m "GrantAI Phase 6: Engineering (architecture, DB schema, API, security, testing, deployment) + root AGENTS.md router"
git push
```

### Phase 7 — Operations (final phase)

```bash
cp ~/Downloads/grantai-files/{StandardOperatingProcedures,QualityControl,ContinuousLearning,AuditLogging,Metrics}.md docs/operations/

git add docs/operations/
git commit -m "GrantAI Phase 7: Operations (SOPs, QC, continuous learning, audit logging, metrics) — roadmap complete"
git push
```

### Checklist file

```bash
cp ~/Downloads/grantai-files/OPEN_DECISIONS.md docs/

git add docs/OPEN_DECISIONS.md
git commit -m "GrantAI: consolidated open-decisions checklist across all 7 phases"
git push
```

---

## End State — Full Tree

```
grantai/
├── AGENTS.md
└── docs/
    ├── README.md
    ├── GOVERNANCE.md
    ├── MISSION.md
    ├── VISION.md
    ├── ROADMAP.md
    ├── OPEN_DECISIONS.md
    ├── agents/
    │   ├── GrantHunter-Agent.md
    │   ├── GrantFinder-Agent.md
    │   ├── GrantWriter-Agent.md
    │   ├── GrantReviewer-Agent.md
    │   ├── GrantResearch-Agent.md
    │   ├── GrantCompliance-Agent.md
    │   └── ExecutiveGrantAdvisor-Agent.md
    ├── knowledge/
    │   ├── GrantKnowledge.md
    │   ├── FundingOrganizations.md
    │   ├── FederalGrants.md
    │   ├── StateGrants.md
    │   ├── CorporateGrants.md
    │   └── FoundationGrants.md
    ├── intelligence/
    │   ├── EligibilityEngine.md
    │   ├── MatchingAlgorithm.md
    │   ├── ScoringSystem.md
    │   ├── DocumentGeneration.md
    │   └── AutomationWorkflow.md
    ├── application/
    │   ├── ProposalTemplates.md
    │   ├── BusinessProfiles.md
    │   ├── BudgetTemplates.md
    │   ├── CommercializationPlans.md
    │   └── ApplicationTracker.md
    ├── engineering/
    │   ├── Architecture.md
    │   ├── DatabaseSchema.md
    │   ├── API.md
    │   ├── Security.md
    │   ├── Testing.md
    │   └── Deployment.md
    └── operations/
        ├── StandardOperatingProcedures.md
        ├── QualityControl.md
        ├── ContinuousLearning.md
        ├── AuditLogging.md
        └── Metrics.md
```

## If You're Using GitHub's Web UI Instead of Git CLI

Same order, same grouping — just use "Add file → Upload files" once per
phase, targeting the folder path shown in each phase section above (GitHub
will create the folder automatically the first time you upload into a path
that doesn't exist yet). Commit message box on the upload screen = the
`git commit -m "..."` message shown above for that phase.
