# Design: Workflow Wizard — Transform Orchestrator into a Scaffolding Tool

**Date:** 2026-02-28
**Status:** Approved

## Problem

The AI Workflow Orchestrator is a template library with two domain examples (software-development, content-writing). It's useful as reference material but doesn't actively help anyone create a new workflow. Meanwhile, Malcolm's production workflows (ai-sales-workflow, ai-writing-workflow) prove that the real value is in Claude operating within a structured system — not in static templates.

## Two User Groups

1. **Malcolm** — Wants to quickly scaffold new domain workflows (like sales, writing) without copying and adapting an existing one manually
2. **Beginners** — People who use AI but don't have structured workflows. Need both education on WHY constitutional governance works and HOW to set one up

## Design Decision

**Approach: "Workflow Wizard" CLAUDE.md** — Rewrite the CLAUDE.md to make Claude itself the scaffolding tool. A `/new-workflow` command triggers a guided discovery flow that generates a complete standalone workflow repo.

## Repo Structure (After)

```
ai-workflow-orchestrator/
├── README.md                          # Rewritten for two audiences
├── QUICKSTART.md                      # "Create your first workflow in 10 minutes"
├── CONTRIBUTING.md                    # Updated
├── CHANGELOG.md
├── LICENSE
│
├── .claude/
│   ├── CLAUDE.md                      # THE CORE: Workflow Wizard instructions
│   ├── settings.json
│   ├── agents/                        # Kept — workflow-architect agent + generated domain agents
│   ├── commands/
│   │   └── new-workflow.md            # /new-workflow guided creation command
│   └── learnings/
│
├── scaffolding/                       # Templates Claude fills during creation
│   ├── claude-md-template.md          # CLAUDE.md for generated repos
│   ├── constitution-template.md       # Domain-agnostic constitution base
│   ├── persona-template.md            # Single persona file template
│   ├── prompt-template.md             # Phase prompt template
│   ├── agent-template.md              # Claude Code agent template
│   ├── memory-templates/
│   │   ├── context-template.md        # Volatile handoff memory
│   │   └── memory-template.md         # Persistent project memory
│   ├── workflow-templates/
│   │   ├── full-workflow.md
│   │   ├── quick-workflow.md
│   │   └── simple-workflow.md
│   └── project-learnings-template.md
│
├── examples/                          # Renamed from domains/ — reference only
│   ├── README.md                      # "These are examples, not the tool"
│   ├── software-development/          # Existing, kept as-is
│   └── content-writing/               # Existing, kept as-is
│
├── docs/
│   ├── concepts/                      # Beginner education
│   │   ├── what-is-constitutional-ai.md
│   │   ├── why-personas-not-prompts.md
│   │   └── the-adaptive-cycle.md
│   ├── guides/                        # Existing guides, reorganized
│   ├── architecture/                  # Existing
│   └── plans/                         # Design docs
│
└── core/                              # Framework theory (existing)
```

## Key Changes

### What's New
- `.claude/CLAUDE.md` — Complete rewrite as Workflow Wizard operating instructions
- `.claude/commands/new-workflow.md` — Guided creation command (6-phase flow)
- `scaffolding/` — Generation templates derived from production workflow patterns
- `docs/concepts/` — 3 short educational pages for beginners
- `examples/README.md` — Framing existing domains as reference examples

### What's Removed
- `QUICK-START.md` (duplicate — merge useful bits into QUICKSTART.md)
- `WORKFLOW-ARCHITECT.md` (superseded by CLAUDE.md creation mode)
- `README-ORIGINAL.md` (no longer needed)
- Domain-specific agents in `.claude/agents/` (replaced with workflow-architect agent)
- `guides/` at root (merged into docs/guides/)
- `templates/` at root (merged into scaffolding/)

### What's Renamed
- `domains/` → `examples/`

### What Stays
- `examples/software-development/` and `examples/content-writing/` — as-is
- `core/` — framework theory
- `docs/architecture/` and `docs/guides/`
- `CONTRIBUTING.md`, `CHANGELOG.md`, `LICENSE`

## CLAUDE.md Design

Two modes of operation:

### Mode 1: Workflow Creation
Claude acts as a Workflow Architect. Detects creation intent from user messages or `/new-workflow` command. Runs the 6-phase creation pipeline.

### Mode 2: Learning/Browsing
Claude helps users explore examples and understand the framework. Points to docs/concepts/ for beginners.

### Key Operating Principles (from production workflows)
- Personas have ONE job and cannot do others' work
- Every persona has explicit inputs, outputs, and constraints
- The Constitution is the single source of truth for quality
- Memory has tiers: volatile (CONTEXT), persistent (MEMORY), cross-project (PROJECT-LEARNINGS)
- Quality is scored numerically with named verdicts, not opinions
- Failure has a defined path (Evolutionist pattern — update governance, not just fix output)
- Human checkpoints are named and explicit

## /new-workflow Command: 6-Phase Creation Pipeline

### Phase 1: Domain Discovery (conversational)
- What domain? What's the goal?
- Who is the human operator?
- What does "done" look like for one cycle?

### Phase 2: Process Mapping (collaborative)
- User describes their current process step by step
- Claude maps steps into phases (typically 3-7)
- Applies adaptive cycle lens: exploitation → conservation → release → reorganization
- Presents phase map for approval

### Phase 3: Persona Definition (the core step)
- For each phase: "Who does this work? What's their expertise?"
- Maps human roles → AI personas (name, responsibility, inputs, outputs, constraints)
- Enforces single-responsibility principle
- Generates persona files AND matching Claude Code agent files
- This is the key innovation: understand the process → define the roles → create the agents

### Phase 4: Constitution Drafting (governance)
- Quality standards: What makes output good? Bad?
- Prohibited patterns (Kill List)
- Brand/voice requirements (if applicable)
- Scoring dimensions (what gets measured?)
- Generates constitution with verbose placeholders for domain-specific details

### Phase 5: Memory & Workflow Design
- Designs CONTEXT/MEMORY/PROJECT-LEARNINGS templates for the domain
- Creates 2-3 workflow variants (full/quick/simple) with decision criteria
- Defines handoff protocols between personas

### Phase 6: Generation
- Creates target directory structure (standalone repo or specified location)
- Generates all files from scaffolding templates + conversation context
- Includes copy-paste prompt versions for non-Claude-Code users
- Produces README.md and SETUP-GUIDE.md
- Shows summary of what was created

## README Design

Three paths:

1. **"What is this?"** — 30-second explanation, visual of Constitution → Personas → Phases → Artifacts, links to docs/concepts/
2. **"Create my workflow"** — Prerequisites (Claude Code), single command (`/new-workflow`), what you'll get
3. **"Show me examples"** — Links to examples/, link to ai-dev-orchestrator as production reference

## Educational Content (docs/concepts/)

Three short pages (500-800 words each), practical, with examples:

1. **What is constitutional AI?** — Why a governance doc beats a long prompt
2. **Why personas, not prompts?** — Single-responsibility principle for AI
3. **The adaptive cycle** — Why workflows should include evaluation and learning phases

## Scaffolding Templates

Derived from patterns proven in ai-sales-workflow and ai-writing-workflow:

- **claude-md-template.md** — CLAUDE.md for generated repos (quick-start flows, persona references, memory protocol, key principles)
- **constitution-template.md** — Kill List + Quality Dimensions + Phase Constraints + Change Log sections
- **persona-template.md** — Core Identity, Objective, Inputs, Process, Output, Quality Checklist, Constitution Refs, Memory Protocol, Handoff, Constraints
- **agent-template.md** — Condensed persona for Claude Code agent (role, phase, responsibilities, rules, checklist, handoff)
- **prompt-template.md** — Copy-paste prompt with role context, instructions, input slots
- **Memory templates** — CONTEXT (volatile, ~500 tokens, cleared at phase transition) and MEMORY (persistent, append-only)
- **Workflow templates** — Full/Quick/Simple variants with persona selection and decision criteria

## Success Criteria

1. Malcolm can scaffold a new domain workflow in a single Claude Code session
2. A beginner can clone the repo, run `/new-workflow`, and have a working workflow repo within 30 minutes
3. Generated workflows include both Claude Code agents AND copy-paste prompts
4. The creation flow produces workflows structurally consistent with ai-sales-workflow and ai-writing-workflow
5. Examples remain browsable without running the scaffolding tool
