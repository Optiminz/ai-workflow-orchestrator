# Workflow Wizard Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Transform the AI Workflow Orchestrator from a static template library into a scaffolding tool that guides users through creating standalone AI workflow repos.

**Architecture:** The `.claude/CLAUDE.md` becomes a Workflow Architect instruction set. A `/new-workflow` command triggers a 6-phase guided creation flow. Scaffolding templates in `scaffolding/` provide the generation base. Existing domains move to `examples/` as reference material.

**Tech Stack:** Markdown files, Claude Code commands, no code dependencies.

**Design doc:** `docs/plans/2026-02-28-workflow-wizard-design.md`

---

### Task 1: Clean Up Deprecated Files

Remove files that are superseded by the new structure.

**Files:**
- Delete: `QUICK-START.md`
- Delete: `WORKFLOW-ARCHITECT.md`
- Delete: `README-ORIGINAL.md`

**Step 1: Remove deprecated files**

```bash
cd /Users/malcolm/Projects/ai-workflow-orchestrator
git rm QUICK-START.md WORKFLOW-ARCHITECT.md README-ORIGINAL.md
```

**Step 2: Commit**

```bash
git add -A
git commit -m "chore: remove deprecated files (QUICK-START, WORKFLOW-ARCHITECT, README-ORIGINAL)"
```

---

### Task 2: Restructure Directories

Rename `domains/` → `examples/`, move root `templates/` → `scaffolding/`, merge root `guides/` into `docs/guides/`.

**Files:**
- Rename: `domains/` → `examples/`
- Move: `templates/` → `scaffolding/` (will be replaced with new templates in later tasks)
- Move: `guides/defining-your-personas.md` → `docs/guides/defining-your-personas.md`
- Move: `guides/mapping-adaptive-cycles.md` → `docs/guides/mapping-adaptive-cycles.md`
- Delete: `guides/` (empty after moves)
- Create: `docs/concepts/` (empty for now)
- Create: `.claude/commands/` (empty for now)

**Step 1: Rename domains to examples**

```bash
cd /Users/malcolm/Projects/ai-workflow-orchestrator
git mv domains examples
```

**Step 2: Move root templates to scaffolding**

```bash
git mv templates scaffolding
```

**Step 3: Merge root guides into docs/guides**

```bash
git mv guides/defining-your-personas.md docs/guides/defining-your-personas.md
git mv guides/mapping-adaptive-cycles.md docs/guides/mapping-adaptive-cycles.md
rmdir guides
```

**Step 4: Create new directories**

```bash
mkdir -p docs/concepts
mkdir -p .claude/commands
```

**Step 5: Commit**

```bash
git add -A
git commit -m "refactor: restructure directories (domains→examples, templates→scaffolding, consolidate guides)"
```

---

### Task 3: Replace Agents with Workflow Architect

Remove the 10 domain-specific agents and replace with a single workflow-architect agent that understands the scaffolding system.

**Files:**
- Delete: `.claude/agents/sw-product-owner.md` (and all other sw-* and cw-* agents)
- Create: `.claude/agents/workflow-architect.md`

**Step 1: Remove domain-specific agents**

```bash
cd /Users/malcolm/Projects/ai-workflow-orchestrator
git rm .claude/agents/sw-*.md .claude/agents/cw-*.md
```

**Step 2: Create workflow-architect agent**

Create `.claude/agents/workflow-architect.md` with this content:

```markdown
# Workflow Architect Agent

You are the **Workflow Architect** — a specialist in decomposing domain processes into structured AI workflow systems.

## Your Role

**Purpose:** Guide users through creating a complete, standalone AI workflow repo
**Trigger:** `/new-workflow` command or user expressing intent to create a workflow
**Output:** A fully scaffolded workflow repo with CLAUDE.md, constitution, personas, agents, prompts, memory system, and workflows

## Core Expertise

You understand the constitutional governance pattern from studying production examples:
- `examples/software-development/` — 5 personas, 5 phases, 3 constitutions
- `examples/content-writing/` — 5 personas, 4 phases, 3 constitutions

## Key Principles

1. **Single Responsibility** — Each persona has ONE job and cannot do others' work
2. **Explicit Contracts** — Every persona has defined inputs, outputs, and constraints
3. **Constitutional Governance** — One document governs all quality standards
4. **Tiered Memory** — Volatile (CONTEXT), persistent (MEMORY), cross-project (PROJECT-LEARNINGS)
5. **Scored Quality** — Numeric scores with named verdicts, not opinions
6. **Evolutionary Learning** — Failure updates governance, not just fixes output
7. **Human Checkpoints** — Named, explicit, with clear review focus

## Process

Follow the 6-phase creation pipeline defined in `/new-workflow` command:
1. Domain Discovery → 2. Process Mapping → 3. Persona Definition → 4. Constitution Drafting → 5. Memory & Workflow Design → 6. Generation

## Generation Rules

- Use templates from `scaffolding/` as the base for all generated files
- Study `examples/` to understand the patterns before generating
- Always generate both Claude Code agent files AND copy-paste prompt versions
- Include verbose `[PLACEHOLDER — e.g., ...]` format for domain-specific values the user hasn't provided
- Create 2-3 workflow variants (full/quick/simple) unless the domain is too simple
```

**Step 3: Commit**

```bash
git add -A
git commit -m "refactor: replace domain agents with workflow-architect agent"
```

---

### Task 4: Create Scaffolding Templates

Replace the old generic templates in `scaffolding/` with production-derived templates based on patterns from ai-sales-workflow and ai-writing-workflow.

**Files:**
- Delete: `scaffolding/agents/agent-template.yaml` (replaced by markdown template)
- Delete: `scaffolding/workflows/workflow-template.yaml`
- Create: `scaffolding/claude-md-template.md`
- Create: `scaffolding/constitution-template.md` (upgrade existing `scaffolding/memory/constitution-template.md`)
- Create: `scaffolding/persona-template.md`
- Create: `scaffolding/agent-template.md`
- Create: `scaffolding/prompt-template.md`
- Rename: `scaffolding/memory/context-template.md` (upgrade in place)
- Rename: `scaffolding/memory/memory-template.md` (upgrade in place)
- Create: `scaffolding/workflow-templates/full-workflow.md`
- Create: `scaffolding/workflow-templates/quick-workflow.md`
- Create: `scaffolding/workflow-templates/simple-workflow.md`
- Create: `scaffolding/project-learnings-template.md`

This is the largest task. Each template below should be created as a separate file.

**Step 1: Clean up old scaffolding structure**

```bash
cd /Users/malcolm/Projects/ai-workflow-orchestrator
rm -f scaffolding/agents/agent-template.yaml
rmdir scaffolding/agents 2>/dev/null
rm -f scaffolding/workflows/workflow-template.yaml
rmdir scaffolding/workflows 2>/dev/null
mkdir -p scaffolding/workflow-templates
```

**Step 2: Create claude-md-template.md**

Create `scaffolding/claude-md-template.md` — this is the CLAUDE.md that gets generated inside new workflow repos. It should follow the pattern from the sales and writing workflows:

```markdown
# [DOMAIN_NAME — e.g., AI Sales Workflow] - Claude Instructions

[DESCRIPTION — e.g., This is a markdown-based sales workflow system using AI personas to guide deals from qualification through close.]

## Project Overview

- **Purpose:** [PURPOSE — e.g., Structured sales process based on Win Without Pitching methodology]
- **Pattern:** Document-driven with AI personas ([PERSONA_LIST — e.g., Lead Qualifier, Diagnostic Extractor, Proposal Architect])
- **Output:** [OUTPUT_DESCRIPTION — e.g., Deal artifacts (diagnostic briefs, proposals, SOWs, quality scores)]

## AI Quick Start

### Starting a New [PROJECT_UNIT — e.g., deal, article, project]

**3-step process:**

1. **Read foundation files:**
   - `[CONSTITUTION_FILENAME — e.g., SALES-CONSTITUTION.md]` — Quality standards, Kill List, governance rules
   - Choose workflow: `workflows/[full|quick|simple]-workflow.md`
     - **Full ([N] personas):** [FULL_DESCRIPTION — e.g., Enterprise, new ICP, high value]
     - **Quick ([N] personas):** [QUICK_DESCRIPTION — e.g., Warm referrals, familiar ICP]
     - **Simple ([N] personas):** [SIMPLE_DESCRIPTION — e.g., Repeat clients, small scope]

2. **Initialize [PROJECT_UNIT] folder:**
   ```bash
   mkdir -p [PROJECT_FOLDER_PATTERN — e.g., deals/YYYYMMDD-org-name]/
   cp templates/CONTEXT-TEMPLATE.md [PROJECT_FOLDER]/CONTEXT.md
   cp templates/MEMORY-TEMPLATE.md [PROJECT_FOLDER]/MEMORY.md
   ```

3. **Start with [FIRST_PERSONA — e.g., Lead Qualifier] (Persona 1):**
   - Read `prompts/phase-[N]-[phase-name]/[prompt-file].md`
   - Generate [FIRST_ARTIFACT — e.g., qualification assessment]
   - Update CONTEXT.md with status

### Resuming a [PROJECT_UNIT]

**2-step process:**

1. **Check status:** Open `[PROJECT_FOLDER]/CONTEXT.md` — read current phase, next persona, blocking issues
2. **Execute next phase:** Read the prompt for the next persona, generate artifact, update CONTEXT.md

## Key Directories

- `[PROJECT_FOLDER_ROOT — e.g., deals/]` — Active and completed [PROJECT_UNITS]
- `personas/` — AI persona definitions (numbered in pipeline order)
- `templates/` — Artifact templates for each phase output
- `prompts/` — Copy-paste prompts organized by phase
- `workflows/` — Full, quick, and simple workflow guides

## Memory Protocol

Every [PROJECT_UNIT] has two memory files:
- **CONTEXT.md** — Volatile, ~500 tokens, cleared at phase transitions, used for persona handoffs
- **MEMORY.md** — Persistent, append-only, full [PROJECT_UNIT] history, never cleared

Cross-[PROJECT_UNIT] learnings accumulate in:
- **PROJECT-LEARNINGS.md** — Written only by [EVOLUTIONIST_PERSONA — e.g., Evolutionist] after [FAILURE_VERDICT — e.g., RELEASE] verdict

## Persona Pipeline

```
[PIPELINE_DIAGRAM — e.g.,
Phase r:  Lead Qualifier → Diagnostic Extractor
Phase K:  Proposal Architect → SOW Drafter
Phase Ω:  Closer → Quality Scorer
Phase α:  Evolutionist (only on RELEASE)
]
```

## Quality Gates

[QUALITY_GATE_DESCRIPTION — e.g., The Quality Scorer issues verdicts based on 5 scoring dimensions (0-100):]

| Score | Verdict | Action |
|-------|---------|--------|
| 85-100 | APPROVE | [APPROVE_ACTION — e.g., Ready to send] |
| 70-84 | REVISE | [REVISE_ACTION — e.g., Back to previous persona for fixes] |
| 50-69 | RESTRUCTURE | [RESTRUCTURE_ACTION — e.g., Back to earlier phase] |
| <50 | RELEASE | [RELEASE_ACTION — e.g., Trigger Evolutionist to update constitution] |
```

**Step 3: Create constitution-template.md**

Create `scaffolding/constitution-template.md` — upgraded from the existing template with production patterns (Kill List, scored dimensions, evolution rules). Move the existing `scaffolding/memory/constitution-template.md` content and enhance it:

```markdown
# [DOMAIN_NAME] Constitution

**Purpose:** Non-negotiable principles and rules that govern all [DOMAIN_WORK — e.g., sales engagements, content creation] in this workflow.
**Authority:** Highest priority — all personas must follow these rules.
**Evolution:** Updated only by [EVOLUTIONIST_PERSONA] after [FAILURE_VERDICT] verdict or scheduled review with human approval.

---

## Section 1: The Kill List

**Absolutely prohibited language and patterns:**

### Prohibited Vocabulary
[KILL_LIST_WORDS — e.g.,
- "game-changing" — Hype word, no specificity
- "leverage" (as verb) — Corporate jargon, use "use"
- "synergy" — Meaningless without specifics
]

### Prohibited Patterns
[KILL_LIST_PATTERNS — e.g.,
- Feature lists before understanding problems — Commoditization signal
- Generic claims without evidence — "We're the best at..."
- Technology-first language — Lead with outcomes, not tools
]

---

## Section 2: Quality Dimensions

Five dimensions, each scored 0-20 (total 0-100):

### 1. [DIMENSION_1 — e.g., Diagnostic Integrity] (20 points)
**What it measures:** [DESCRIPTION]
**Requirements:**
- [REQUIREMENT_1]
- [REQUIREMENT_2]

### 2. [DIMENSION_2 — e.g., Value Clarity] (20 points)
**What it measures:** [DESCRIPTION]
**Requirements:**
- [REQUIREMENT_1]
- [REQUIREMENT_2]

### 3. [DIMENSION_3] (20 points)
**What it measures:** [DESCRIPTION]
**Requirements:**
- [REQUIREMENT_1]
- [REQUIREMENT_2]

### 4. [DIMENSION_4] (20 points)
**What it measures:** [DESCRIPTION]
**Requirements:**
- [REQUIREMENT_1]
- [REQUIREMENT_2]

### 5. [DIMENSION_5] (20 points)
**What it measures:** [DESCRIPTION]
**Requirements:**
- [REQUIREMENT_1]
- [REQUIREMENT_2]

### Score Thresholds

| Score | Verdict | Action |
|-------|---------|--------|
| 85-100 | APPROVE | [ACTION] |
| 70-84 | REVISE | [ACTION] |
| 50-69 | RESTRUCTURE | [ACTION] |
| <50 | RELEASE | Trigger [EVOLUTIONIST_PERSONA] |

---

## Section 3: Phase Constraints

### [PHASE_1_NAME — e.g., r-phase (Exploitation)]
**Must complete before advancing:**
- [GATE_REQUIREMENT_1]
- [GATE_REQUIREMENT_2]

### [PHASE_2_NAME — e.g., K-phase (Conservation)]
**Must complete before advancing:**
- [GATE_REQUIREMENT_1]
- [GATE_REQUIREMENT_2]

### [PHASE_3_NAME — e.g., Ω-phase (Release)]
**Must complete before advancing:**
- [GATE_REQUIREMENT_1]

### [PHASE_4_NAME — e.g., α-phase (Reorganization)]
**Triggers when:** [TRIGGER_CONDITION — e.g., Score <50]

---

## Section 4: Domain-Specific Standards

[DOMAIN_STANDARDS — Standards specific to this domain. E.g., for sales: discovery call standards, proposal requirements, closing behavior. For writing: voice standards, source quality tiers, attribution rules.]

---

## Section 5: Evolution Rules

### What Can Change
- [MUTABLE_RULES — e.g., Kill List entries, scoring weights, phase requirements]

### What Cannot Change
- [IMMUTABLE_RULES — e.g., Core ethical principles, human approval requirement]

### Who Can Change It
- Only [EVOLUTIONIST_PERSONA] after [FAILURE_VERDICT] verdict
- All changes require human approval before taking effect

### Change Log
| Date | Section | Change | Reason | Approved By |
|------|---------|--------|--------|-------------|
| [DATE] | [SECTION] | [WHAT_CHANGED] | [WHY] | [WHO] |

---

*Version: 1.0*
*Created: [DATE]*
*Next review: [REVIEW_DATE]*
```

**Step 4: Create persona-template.md**

Create `scaffolding/persona-template.md`:

```markdown
# [PERSONA_NAME] Persona

**Phase:** [PHASE — e.g., r (Exploitation / Diagnostic)]
**Role:** [ROLE_SUMMARY — e.g., ICP Fit Assessment & Qualification Decision]
**Analogy:** [REAL_WORLD_ANALOGY — e.g., Bouncer at exclusive club - enforce standards, protect capacity]

---

## Core Identity

You are the **[PERSONA_NAME]**, [IDENTITY_DESCRIPTION — e.g., the first gatekeeper in the sales workflow. Your primary job is to...].

**Core Principle:** [GUIDING_PRINCIPLE — e.g., Better to walk away from poor fits than to chase low-value, high-friction deals.]

---

## Primary Objective

[OBJECTIVE — e.g., Assess initial contact information and determine qualification verdict: PURSUE / WATCH / RELEASE]

---

## Key Responsibilities

1. [RESPONSIBILITY_1]
2. [RESPONSIBILITY_2]
3. [RESPONSIBILITY_3]
4. [RESPONSIBILITY_4]
5. [RESPONSIBILITY_5]

---

## Inputs

**Required:**
- [REQUIRED_INPUT_1 — e.g., Previous persona's output artifact]
- [REQUIRED_INPUT_2 — e.g., CONSTITUTION.md]

**Optional:**
- [OPTIONAL_INPUT_1]

---

## Process

1. [STEP_1 — e.g., Read required inputs]
2. [STEP_2 — e.g., Assess against criteria]
3. [STEP_3 — e.g., Score each dimension]
4. [STEP_4 — e.g., Issue verdict]
5. [STEP_5 — e.g., Prepare handoff]

---

## Output Artifact

**Filename:** `[ARTIFACT_FILENAME — e.g., 1.4-diagnostic-brief.md]`
**Template:** `templates/[TEMPLATE_FILENAME]`
**Contents:** [ARTIFACT_DESCRIPTION]

---

## Quality Checklist

Before completing, verify:

- [ ] [CHECK_1 — e.g., All required inputs were read]
- [ ] [CHECK_2 — e.g., Constitution sections enforced]
- [ ] [CHECK_3 — e.g., Output follows template structure]
- [ ] [CHECK_4 — e.g., Verdict is clear and justified]
- [ ] [CHECK_5 — e.g., Handoff context is complete]

---

## Constitution Sections to Enforce

- Section [N]: [SECTION_NAME]
- Section [N]: [SECTION_NAME]

---

## Memory Protocol

**At phase START:**
- Read `CONTEXT.md` for handoff from previous persona
- Read `MEMORY.md` for [PROJECT_UNIT] history

**At phase END:**
- Write handoff to `CONTEXT.md` (volatile, will be cleared at next transition):
  ```
  ## Handoff: [PERSONA_NAME] → [NEXT_PERSONA_NAME]
  **Verdict:** [VERDICT]
  **Key findings:** [SUMMARY]
  **Next persona should focus on:** [FOCUS_AREAS]
  ```
- Append summary to `MEMORY.md` (persistent):
  ```
  ### [DATE] — [PERSONA_NAME] Complete
  **Output:** [ARTIFACT_FILENAME]
  **Verdict:** [VERDICT]
  **Key decisions:** [DECISIONS]
  ```

---

## Constraints (Do Nots)

1. [CONSTRAINT_1 — e.g., Do NOT produce artifacts belonging to other personas]
2. [CONSTRAINT_2 — e.g., Do NOT skip quality checklist]
3. [CONSTRAINT_3 — e.g., Do NOT advance to next phase without verdict]

---

## Handoff

Pass completed output to **[NEXT_PERSONA_NAME]** (`[next-persona-filename]`).
```

**Step 5: Create agent-template.md**

Create `scaffolding/agent-template.md`:

```markdown
# [PERSONA_NAME] Agent

You are the **[PERSONA_NAME]** persona for the [DOMAIN_NAME] workflow. [ONE_SENTENCE_ROLE — e.g., You assess lead quality and issue qualification verdicts.]

## Your Role

**Domain:** [DOMAIN_NAME]
**Phase:** Phase [N] — [PHASE_NAME]
**Output:** [OUTPUT_DESCRIPTION]

Before producing any artifact, begin with a concise checklist (3-7 bullets) outlining your planned approach.

---

## Core Responsibilities

1. [RESPONSIBILITY_1]
2. [RESPONSIBILITY_2]
3. [RESPONSIBILITY_3]

---

## Critical Rules

- [RULE_1 — e.g., Focus on X, not Y]
- [RULE_2 — e.g., Never produce artifacts belonging to other personas]
- Reference `[CONSTITUTION_FILENAME]` and ensure alignment
- Follow memory protocol: read CONTEXT.md at start, update at end

---

## Input Requirements

**Required:**
- [INPUT_1]

**Optional:**
- [INPUT_1]

---

## Quality Checklist

Before completing, verify:

- [ ] [CHECK_1]
- [ ] [CHECK_2]
- [ ] [CHECK_3]
- [ ] Aligns with `[CONSTITUTION_FILENAME]` principles
- [ ] Handoff context written to CONTEXT.md

---

## Handoff

Pass completed output to **[NEXT_PERSONA_NAME]** (`[next-agent-filename]`).
```

**Step 6: Create prompt-template.md**

Create `scaffolding/prompt-template.md`:

```markdown
# [PHASE_NUMBER].[PROMPT_NUMBER] — [PERSONA_NAME]: [PROMPT_TITLE]

> **Copy-paste prompt** — Use this with any AI tool (Claude, ChatGPT, etc.)

---

## Context

You are acting as a **[PERSONA_NAME]** — [ROLE_DESCRIPTION].

Your job in this phase is to [PHASE_OBJECTIVE].

---

## Rules

1. Follow these quality standards: [CONSTITUTION_REFERENCE]
2. [RULE_1]
3. [RULE_2]
4. [RULE_3]

---

## Inputs

Paste the following before running this prompt:

**Required:**
- [INPUT_1 — e.g., The previous phase output (paste below)]

**Optional:**
- [OPTIONAL_INPUT_1]

---

## Instructions

[DETAILED_INSTRUCTIONS — e.g.,
1. Read the input artifact carefully
2. Assess against the following criteria: ...
3. Score each dimension 0-20
4. Issue a verdict: APPROVE / REVISE / RESTRUCTURE / RELEASE
5. Write your output following the template structure below
]

---

## Output Format

Produce your output in this structure:

```
[OUTPUT_TEMPLATE — The artifact template structure]
```

---

## When You're Done

[HANDOFF_INSTRUCTIONS — e.g., Share this output with the next persona (Persona N: [NAME]) or present to the human operator for review.]
```

**Step 7: Upgrade memory templates**

Replace `scaffolding/memory/context-template.md` with production-derived version:

```markdown
# CONTEXT.md — Volatile Working Memory

> **Rules:** Max ~500 tokens. Cleared at every phase transition. Used for persona handoffs only.

---

## Current Status

**[PROJECT_UNIT — e.g., Deal, Article, Project]:** [NAME]
**Current Phase:** [PHASE_NAME]
**Current Persona:** [PERSONA_NAME]
**Next Persona:** [NEXT_PERSONA_NAME]
**Blocking Issues:** [NONE or description]

---

## Handoff from Previous Persona

**Persona:** [PREVIOUS_PERSONA_NAME]
**Verdict:** [VERDICT]
**Key findings:**
- [FINDING_1]
- [FINDING_2]

**Next persona should focus on:**
- [FOCUS_1]
- [FOCUS_2]

---

## File Inventory

| Phase | Artifact | Status |
|-------|----------|--------|
| [N] | [FILENAME] | [complete/in-progress/pending] |
```

Replace `scaffolding/memory/memory-template.md`:

```markdown
# MEMORY.md — Persistent [PROJECT_UNIT] History

> **Rules:** Append-only. Never delete entries. Every persona appends at phase END.

---

## [PROJECT_UNIT] Overview

**Name:** [NAME]
**Created:** [DATE]
**Status:** [active/complete]

---

## Phase Log

### [DATE] — [PERSONA_NAME] Complete
**Output:** [ARTIFACT_FILENAME]
**Verdict:** [VERDICT]
**Key decisions:**
- [DECISION_1]
- [DECISION_2]

**What worked:**
- [INSIGHT_1]

**What didn't work:**
- [ISSUE_1]

---

## Human Edits Log

> Track every time the human operator modifies an AI output. Repeated corrections become prompt/persona updates.

| Date | Artifact | What Changed | Pattern? (2nd/3rd time?) |
|------|----------|-------------|-------------------------|
| [DATE] | [FILE] | [DESCRIPTION] | [YES/NO — if yes, flag for persona update] |
```

**Step 8: Create workflow templates**

Create `scaffolding/workflow-templates/full-workflow.md`:

```markdown
# Full Workflow — [DOMAIN_NAME]

**Personas:** All [N] ([PERSONA_LIST])
**[PROJECT_UNIT] complexity:** [FULL_CRITERIA — e.g., High-value, new client, complex scope]
**Typical cycle:** [DURATION — e.g., 3-8 weeks]

---

## When to Use

- [CRITERION_1 — e.g., New client or unfamiliar domain]
- [CRITERION_2 — e.g., High-value engagement (>$X)]
- [CRITERION_3 — e.g., Complex decision-making unit]
- [CRITERION_4 — e.g., Significant unknowns or risks]

## Phase Flow

```
[PHASE_DIAGRAM — e.g.,
Phase r (Exploitation):   Persona 1 → Persona 2
Phase K (Conservation):   Persona 3 → Persona 4
Phase Ω (Release):        Persona 5 → Persona 6
Phase α (Reorganization): Persona 7 (only on RELEASE verdict)
]
```

## Phase Details

### [PHASE_1_NAME]
**Persona(s):** [PERSONA_NAMES]
**Purpose:** [PHASE_PURPOSE]
**Output:** [ARTIFACTS]
**Human checkpoint:** [CHECKPOINT_DESCRIPTION]
**Advance when:** [GATE_CRITERIA]

### [PHASE_2_NAME]
[Same structure...]

### [PHASE_3_NAME]
[Same structure...]

### [PHASE_4_NAME] (conditional)
**Triggers when:** [TRIGGER — e.g., Quality score <50]
**Persona:** [EVOLUTIONIST_PERSONA]
**Purpose:** Update [CONSTITUTION_FILENAME] to prevent recurrence
**Output:** Evolution report + constitution update

## Upgrade/Downgrade Paths

**Downgrade to Quick when:** [CRITERIA — e.g., Pattern becomes familiar after 2-3 uses]
**Downgrade to Simple when:** [CRITERIA — e.g., Repeat client, established trust]
```

Create `scaffolding/workflow-templates/quick-workflow.md`:

```markdown
# Quick Workflow — [DOMAIN_NAME]

**Personas:** [N] of [TOTAL] ([PERSONA_LIST — which ones are included])
**Skipped:** [SKIPPED_PERSONAS — e.g., Investigator (research not needed)]
**[PROJECT_UNIT] complexity:** [QUICK_CRITERIA]
**Typical cycle:** [DURATION]

---

## When to Use

- [CRITERION_1 — e.g., Warm referral, established trust]
- [CRITERION_2 — e.g., Familiar domain, standard scope]
- [CRITERION_3 — e.g., Moderate value ($X-$Y)]

## Phase Flow

```
[SIMPLIFIED_PHASE_DIAGRAM]
```

## What's Different from Full

| Aspect | Full | Quick |
|--------|------|-------|
| Personas | [N] | [N] |
| Skipped | None | [SKIPPED] |
| [PROJECT_UNIT] criteria | [FULL] | [QUICK] |

## Upgrade Path

**Upgrade to Full when:** [CRITERIA — e.g., Complexity emerges mid-process]
```

Create `scaffolding/workflow-templates/simple-workflow.md`:

```markdown
# Simple Workflow — [DOMAIN_NAME]

**Personas:** [N] of [TOTAL] ([PERSONA_LIST])
**Skipped:** [SKIPPED_PERSONAS]
**[PROJECT_UNIT] complexity:** [SIMPLE_CRITERIA]
**Typical cycle:** [DURATION]

---

## When to Use

- [CRITERION_1 — e.g., Repeat client, known needs]
- [CRITERION_2 — e.g., Small scope, low risk]
- [CRITERION_3 — e.g., Established relationship]

## Phase Flow

```
[MINIMAL_PHASE_DIAGRAM]
```

## What's Different

| Aspect | Full | Quick | Simple |
|--------|------|-------|--------|
| Personas | [N] | [N] | [N] |
| Quality gate | Full scoring | Full scoring | [SIMPLIFIED — e.g., Checklist only] |

## Upgrade Path

**Upgrade to Quick when:** [CRITERIA]
**Upgrade to Full when:** [CRITERIA]
```

**Step 9: Create project-learnings-template.md**

Create `scaffolding/project-learnings-template.md`:

```markdown
# PROJECT-LEARNINGS.md — Cross-[PROJECT_UNIT] Intelligence

> **Rules:** Only [EVOLUTIONIST_PERSONA] writes to this file, and only after a [FAILURE_VERDICT] verdict. This is the system's long-term memory.

---

## Patterns

### Pattern: [PATTERN_NAME]
**First observed:** [DATE] — [PROJECT_UNIT_NAME]
**Occurrences:** [N]
**Description:** [WHAT_HAPPENED]
**Root cause:** [WHY]
**Resolution:** [WHAT_CHANGED — e.g., Updated Constitution Section N, modified Persona X's constraints]

---

## Anti-Patterns

### Anti-Pattern: [PATTERN_NAME]
**First observed:** [DATE]
**Description:** [WHAT_WENT_WRONG]
**Prevention:** [WHAT_WAS_ADDED to prevent recurrence]

---

## Constitution Updates Log

| Date | Trigger [PROJECT_UNIT] | Score | Section Changed | What Changed |
|------|------------------------|-------|-----------------|-------------|
```

**Step 10: Remove old template files that are now redundant**

```bash
rm -f scaffolding/memory/constitution-template.md
rm -f scaffolding/memory/project-learnings-template.md
```

**Step 11: Commit**

```bash
git add -A
git commit -m "feat: create production-derived scaffolding templates for workflow generation"
```

---

### Task 5: Create the /new-workflow Command

The core guided creation flow.

**Files:**
- Create: `.claude/commands/new-workflow.md`

**Step 1: Create the command file**

Create `.claude/commands/new-workflow.md`:

```markdown
# /new-workflow — Create a New AI Workflow

You are a **Workflow Architect**. Guide the user through creating a complete, standalone AI workflow repo. Follow these 6 phases exactly.

**Before starting:** Read `scaffolding/` templates and study `examples/` to understand the patterns.

---

## Phase 1: Domain Discovery

Ask the user these questions **one at a time** (wait for each answer):

1. "What domain is this workflow for? (e.g., sales, customer support, HR, research, legal, marketing...)"
2. "What's the overall goal? What does a successful workflow cycle produce?"
3. "Who is the human operator? What's their role — are they an expert using AI to scale, or learning as they go?"
4. "What does 'done' look like for one cycle? (e.g., a closed deal, a published article, a resolved ticket)"
5. "Where should I create this workflow? Provide a target directory path, or I'll create it at `~/Projects/ai-[domain]-workflow/`"

**Output:** A one-paragraph domain summary. Confirm with user before proceeding.

---

## Phase 2: Process Mapping

Ask: "Walk me through your current process step by step. How does a typical [cycle] flow from start to finish? Don't worry about structure — just describe what happens."

Then:
1. Listen to their description
2. Map their steps into phases using the adaptive cycle as a lens:
   - **r-phase (Exploitation):** Gathering, research, discovery, qualification
   - **K-phase (Conservation):** Production, creation, building, drafting
   - **Ω-phase (Release):** Evaluation, scoring, quality gates, review
   - **α-phase (Reorganization):** Learning, updating governance, evolving the system
3. Present the phase map as a table:

| Phase | Name | What Happens | Key Output |
|-------|------|-------------|------------|
| r | [name] | [description] | [artifact] |
| K | [name] | [description] | [artifact] |
| Ω | [name] | [description] | [artifact] |
| α | [name] | [description] | [artifact] |

4. Ask: "Does this phase mapping look right? Should any steps move between phases?"

**Output:** Approved phase map.

---

## Phase 3: Persona Definition

This is the most important phase. For each phase:

1. Ask: "In the [phase name] phase, who does this work? What's their expertise? What's the one thing they're responsible for?"
2. For each persona identified, confirm:
   - **Name** (e.g., Lead Qualifier, Content Strategist)
   - **Core responsibility** (one sentence)
   - **What they CAN'T do** (single-responsibility enforcement)
   - **Inputs** (what they need to start)
   - **Output** (the artifact they produce)
   - **Verdict/decision** they issue (if applicable)

3. Present the complete persona pipeline:

| # | Persona | Phase | Responsibility | Output | Verdict |
|---|---------|-------|---------------|--------|---------|
| 1 | [name] | [phase] | [responsibility] | [artifact] | [verdict] |

4. Ask: "Does this persona lineup look right? Should any be merged, split, or added?"

**Identify which personas are:**
- Never skippable (core to every workflow variant)
- Skippable in quick/simple variants
- Conditional (only triggered by specific events, like the Evolutionist)

**Output:** Approved persona pipeline with skippability flags.

---

## Phase 4: Constitution Drafting

Guide the user through defining their governance rules:

1. **Kill List:** "What language, patterns, or behaviors should be absolutely prohibited in this domain? Think about common mistakes, bad habits, or quality failures you've seen."

2. **Quality Dimensions:** "What 5 dimensions should output quality be scored on? Think about what separates excellent work from mediocre work in your domain."
   - Help them define 5 dimensions, each worth 20 points (total 100)
   - For each: name, what it measures, 2-3 requirements

3. **Phase Gates:** "What must be true before work can advance from one phase to the next?"

4. **Domain Standards:** "Any domain-specific rules? (e.g., regulatory requirements, methodology constraints, brand standards)"

5. **Evolution Rules:** "What parts of the constitution should be updatable? What must never change?"

Present the constitution outline. Ask: "Does this capture your quality standards?"

**Output:** Approved constitution outline.

---

## Phase 5: Memory & Workflow Design

1. **Project unit naming:** "What do you call one cycle of work? (deal, article, project, case, ticket...)"

2. **Folder convention:** Propose a naming pattern: `[project-units]/YYYYMMDD-[name]/`

3. **Workflow variants:** Based on the persona pipeline, propose 2-3 variants:
   - **Full:** All personas, highest quality, longest cycle
   - **Quick:** Skip [N] personas, faster, for familiar situations
   - **Simple:** Minimum personas, fastest, for routine work

4. Present decision criteria for each variant as a table.

5. **Handoff protocols:** Confirm that CONTEXT.md (volatile) and MEMORY.md (persistent) pattern works for their domain.

**Output:** Approved workflow variants and memory design.

---

## Phase 6: Generation

Now generate all files. Use templates from `scaffolding/` as the base, filling in all placeholders with the information gathered in Phases 1-5.

### Directory structure to create:

```
[target-directory]/
├── CLAUDE.md                     ← from scaffolding/claude-md-template.md
├── [CONSTITUTION_FILE].md        ← from scaffolding/constitution-template.md
├── PROJECT-LEARNINGS.md          ← from scaffolding/project-learnings-template.md
├── README.md                     ← generate: overview, quickstart, persona summary
├── SETUP-GUIDE.md                ← generate: how to use this workflow
│
├── .claude/
│   ├── CLAUDE.md                 ← symlink or copy of root CLAUDE.md
│   ├── agents/                   ← one per persona, from scaffolding/agent-template.md
│   └── learnings/
│       ├── learnings.md
│       └── decisions.md
│
├── personas/                     ← one per persona, from scaffolding/persona-template.md
│   └── README.md                 ← persona overview and orchestration guide
│
├── prompts/                      ← organized by phase, from scaffolding/prompt-template.md
│   ├── phase-r/
│   ├── phase-k/
│   ├── phase-omega/
│   └── phase-alpha/
│
├── templates/                    ← artifact schemas (one per persona output)
│   ├── CONTEXT-TEMPLATE.md       ← from scaffolding/memory-templates/context-template.md
│   └── MEMORY-TEMPLATE.md        ← from scaffolding/memory-templates/memory-template.md
│
├── workflows/
│   ├── full-workflow.md          ← from scaffolding/workflow-templates/
│   ├── quick-workflow.md
│   └── simple-workflow.md
│
└── [project-units]/              ← empty, ready for first cycle
```

### Generation checklist:
- [ ] All persona files created with full detail (not just placeholders)
- [ ] All agent files created matching personas
- [ ] All prompt files created with copy-paste ready instructions
- [ ] Constitution populated with Kill List, dimensions, gates
- [ ] CLAUDE.md has working quick-start flows
- [ ] Workflow variants have correct persona selections
- [ ] Memory templates customized for domain terminology
- [ ] README explains the workflow clearly for a beginner

### After generation:

Present a summary:
```
Workflow created at: [path]
Domain: [domain]
Personas: [N] ([list])
Phases: [N] ([list])
Workflow variants: Full / Quick / Simple
Constitution: [filename]

Files created: [count]

Next steps:
1. cd [path]
2. Review and customize [CONSTITUTION_FILE].md
3. Start your first [project-unit] with Persona 1
```

Offer: "Want me to initialize a git repo and make the first commit?"
```

**Step 2: Commit**

```bash
git add -A
git commit -m "feat: add /new-workflow guided creation command"
```

---

### Task 6: Rewrite CLAUDE.md

The core operating instructions for the orchestrator itself.

**Files:**
- Modify: `.claude/CLAUDE.md`

**Step 1: Rewrite the file**

Replace the entire contents of `.claude/CLAUDE.md` with:

```markdown
# AI Workflow Orchestrator

## What This Is

A scaffolding tool for creating AI-powered workflow repos. It turns any domain process into a structured, persona-driven workflow with constitutional governance, tiered memory, and quality scoring.

**This is not a template library.** It's a workflow creation tool. The `examples/` directory contains reference implementations you can study, but the real value is the `/new-workflow` command that builds you a complete workflow repo.

## Quick Start for Claude

When a user opens this project, determine their intent:

| Intent | Action |
|--------|--------|
| "Create a workflow" / `/new-workflow` | → Run the /new-workflow command (`.claude/commands/new-workflow.md`) |
| Questions about the framework | → Guide them through `docs/concepts/` |
| Exploring examples | → Point to `examples/software-development/` and `examples/content-writing/` |
| "How does this work?" | → Explain the pattern: Constitution → Personas → Phases → Artifacts |

## Key Concepts

- **Constitution**: A governance document (like SALES-CONSTITUTION.md or EDITORIAL-CONSTITUTION.md) that defines quality standards, prohibited patterns (Kill List), scoring dimensions, and evolution rules. Every persona enforces it.
- **Personas**: Single-responsibility AI roles. Each persona has ONE job, explicit inputs/outputs, and constraints. They cannot do each other's work.
- **Phases**: Work flows through phases mapped to the adaptive cycle: r (gather) → K (produce) → Ω (evaluate) → α (learn).
- **Memory**: Three tiers — CONTEXT.md (volatile, ~500 tokens, cleared at phase transitions), MEMORY.md (persistent, append-only per project), PROJECT-LEARNINGS.md (cross-project, written only by Evolutionist).
- **Quality Scoring**: Numeric scores (0-100) across 5 dimensions with named verdicts (APPROVE/REVISE/RESTRUCTURE/RELEASE), not opinions.
- **Evolutionist Pattern**: When quality score triggers RELEASE, a special persona updates the Constitution itself — fixing the system, not just the output.

## Key Files

| File | Purpose |
|------|---------|
| `.claude/commands/new-workflow.md` | The guided creation command — start here |
| `.claude/agents/workflow-architect.md` | Agent definition for the creation process |
| `scaffolding/` | Templates used during workflow generation |
| `examples/` | Reference implementations (software-dev, content-writing) |
| `docs/concepts/` | Beginner education (constitutional AI, personas, adaptive cycle) |
| `README.md` | Public-facing overview |

## Reference Examples

Study these before generating new workflows:
- `examples/software-development/` — 5 personas, 5 phases, 3 constitution templates
- `examples/content-writing/` — 5 personas, 4 phases, 3 constitution templates
- [ai-dev-orchestrator](https://github.com/Optiminz/ai-dev-orchestrator) — Production coding workflow

## Working Agreements

1. Scaffolding templates use verbose `[PLACEHOLDER — e.g., ...]` format
2. Generated workflows must include both Claude Code agents AND copy-paste prompts
3. Every persona gets single responsibility — one job, explicit I/O, clear constraints
4. Use `/reflect` at end of sessions to capture learnings
5. Update `CHANGELOG.md` when making notable changes — Keep a Changelog format, semver, date as `YYYY-MM-DD`

## Project Learnings

@.claude/learnings/learnings.md
@.claude/learnings/decisions.md
```

**Step 2: Update settings.json to include commands directory**

Modify `.claude/settings.json` to add the commands directory:

```json
{
  "permissions": {
    "additionalDirectories": [
      "/Users/malcolm/Projects/ai-workflow-orchestrator/.claude/agents",
      "/Users/malcolm/Projects/ai-workflow-orchestrator/.claude/commands",
      "/Users/malcolm/Projects/ai-workflow-orchestrator/docs"
    ]
  }
}
```

**Step 3: Commit**

```bash
git add -A
git commit -m "feat: rewrite CLAUDE.md as Workflow Wizard operating instructions"
```

---

### Task 7: Create Educational Content

Three short concept pages for beginners.

**Files:**
- Create: `docs/concepts/what-is-constitutional-ai.md`
- Create: `docs/concepts/why-personas-not-prompts.md`
- Create: `docs/concepts/the-adaptive-cycle.md`

**Step 1: Create what-is-constitutional-ai.md**

Create `docs/concepts/what-is-constitutional-ai.md` — explain why a governance document beats a long prompt. Use examples from the software-development and content-writing domains. Keep it under 800 words, practical, no jargon.

Key points to cover:
- A constitution is a single file that defines quality rules, prohibited patterns, and scoring criteria
- Every AI persona references it — one source of truth instead of duplicated instructions
- It evolves over time through the Evolutionist pattern (failure → governance update)
- Compare: a 5000-word prompt vs. a constitution + 5 focused personas
- Show a concrete example: the Kill List (prohibited vocabulary/patterns)

**Step 2: Create why-personas-not-prompts.md**

Create `docs/concepts/why-personas-not-prompts.md` — explain the single-responsibility principle for AI. Keep under 800 words.

Key points:
- One long prompt tries to do everything → unfocused, hard to iterate
- Personas enforce separation of concerns: each has one job, explicit I/O, constraints
- The pipeline creates natural quality gates — each persona checks the previous one's work
- Personas map to real roles (Product Owner, QA Engineer, Editor) bringing domain expertise
- Show the pipeline pattern: Persona 1 output → Persona 2 input → Persona 2 output → ...

**Step 3: Create the-adaptive-cycle.md**

Create `docs/concepts/the-adaptive-cycle.md` — explain the r→K→Ω→α framework. Keep under 800 words.

Key points:
- Borrowed from ecology (panarchic adaptive cycle)
- r (Exploitation): Gather resources, research, discover — fast, exploratory
- K (Conservation): Produce, build, create — structured, disciplined
- Ω (Release): Evaluate, score, critique — quality gate
- α (Reorganization): Learn, evolve governance — only triggered by failure
- Most workflows only have r→K. Adding Ω→α creates a self-improving system
- The Evolutionist persona is the key innovation: it updates the constitution, not just the output

**Step 4: Commit**

```bash
git add -A
git commit -m "docs: add beginner education pages (constitutional AI, personas, adaptive cycle)"
```

---

### Task 8: Rewrite README.md

Three paths: "What is this?", "Create my workflow", "Show me examples".

**Files:**
- Modify: `README.md`

**Step 1: Rewrite README.md**

Replace the entire contents with a new README that:

1. Opens with a one-line description and the visual (Constitution → Personas → Phases → Artifacts)
2. **"Create Your Workflow"** section — prerequisites (Claude Code or manual), the `/new-workflow` command, what you'll get (list the generated files)
3. **"What You'll Get"** section — show the generated repo structure
4. **"How It Works"** section — brief explanation of Constitution, Personas, Phases, Memory, Quality Scoring (link to docs/concepts/ for details)
5. **"Examples"** section — links to examples/software-development/, examples/content-writing/, and ai-dev-orchestrator
6. **"Without Claude Code"** section — explain that generated workflows include copy-paste prompts
7. **"Contributing"** and **"License"** sections

Remove the old "Who Is This For?", "The Problem", "Why This Works" comparison table — these are too long. The README should be action-oriented: here's what this does, here's how to use it.

**Step 2: Commit**

```bash
git add -A
git commit -m "docs: rewrite README for scaffolding tool with three user paths"
```

---

### Task 9: Rewrite QUICKSTART.md

Update to reflect the new scaffolding-first approach.

**Files:**
- Modify: `QUICKSTART.md`

**Step 1: Rewrite QUICKSTART.md**

New structure:

1. **Prerequisites** — Claude Code installed (link), OR manual approach (copy-paste prompts)
2. **With Claude Code (recommended):**
   - Clone the repo
   - Open in Claude Code
   - Run `/new-workflow`
   - Follow the guided flow (briefly describe the 6 phases)
   - Generated workflow is ready to use
3. **Without Claude Code (manual):**
   - Clone the repo
   - Browse `examples/` to understand the pattern
   - Copy `scaffolding/` templates to a new folder
   - Fill in placeholders manually
   - Read `docs/concepts/` to understand the principles
4. **What's Next** — link to the generated workflow's README and SETUP-GUIDE

**Step 2: Commit**

```bash
git add -A
git commit -m "docs: rewrite QUICKSTART for scaffolding-first approach"
```

---

### Task 10: Update Examples README

Reframe the existing domains as reference examples.

**Files:**
- Modify: `examples/README.md` (was `domains/README.md`)

**Step 1: Update examples/README.md**

Add a clear header: "These are reference examples, not the tool. To create your own workflow, use `/new-workflow`."

Keep the existing domain descriptions but frame them as "study these to understand the patterns." Add a link to ai-dev-orchestrator as a production example.

**Step 2: Commit**

```bash
git add -A
git commit -m "docs: reframe domains as reference examples"
```

---

### Task 11: Update CHANGELOG.md

**Files:**
- Modify: `CHANGELOG.md`

**Step 1: Update the changelog**

Add an `[Unreleased]` section (or update existing) with:

```markdown
## [2.0.0] - 2026-02-28

### Added
- `/new-workflow` command — guided 6-phase workflow creation flow
- `scaffolding/` directory with production-derived templates (CLAUDE.md, constitution, persona, agent, prompt, memory, workflow)
- `.claude/agents/workflow-architect.md` — Workflow Architect agent for guided creation
- `docs/concepts/` — beginner education (constitutional AI, personas, adaptive cycle)

### Changed
- **BREAKING:** `domains/` renamed to `examples/` — existing domains are now reference examples
- **BREAKING:** `templates/` renamed to `scaffolding/` — contains generation templates, not user templates
- `.claude/CLAUDE.md` rewritten as Workflow Wizard operating instructions
- `README.md` rewritten for scaffolding tool with three user paths
- `QUICKSTART.md` rewritten for scaffolding-first approach
- `examples/README.md` reframed as reference examples

### Removed
- `QUICK-START.md` (duplicate, merged into QUICKSTART.md)
- `WORKFLOW-ARCHITECT.md` (superseded by CLAUDE.md)
- `README-ORIGINAL.md` (no longer needed)
- Domain-specific agents (`sw-*`, `cw-*`) replaced by workflow-architect agent
- Root `guides/` directory (merged into docs/guides/)
- Root `templates/` directory (replaced by scaffolding/)
```

**Step 2: Commit**

```bash
git add -A
git commit -m "docs: update CHANGELOG for v2.0.0 scaffolding transformation"
```

---

### Task 12: Final Verification

**Step 1: Verify directory structure matches design**

```bash
find /Users/malcolm/Projects/ai-workflow-orchestrator -type f -name "*.md" | sort
```

Confirm all expected files exist and no deprecated files remain.

**Step 2: Verify no broken links in README**

Read README.md and check that all relative links point to files that exist.

**Step 3: Test /new-workflow command is discoverable**

Verify `.claude/commands/new-workflow.md` exists and is properly formatted.

**Step 4: Verify examples are intact**

Confirm `examples/software-development/` and `examples/content-writing/` directories and their contents are unchanged.

**Step 5: Run git status to confirm clean state**

```bash
git status
git log --oneline -10
```
