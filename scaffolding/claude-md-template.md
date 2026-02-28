# Project: [PLACEHOLDER — e.g., AI Sales Workflow, AI Writing Workflow, AI Research Workflow]

## Project Overview

**Purpose:** [PLACEHOLDER — e.g., Qualify inbound leads and generate personalised outreach sequences using a multi-persona pipeline]

**Pattern:** Multi-persona pipeline — each persona handles one phase, passes a structured artifact to the next.

**Output:** [PLACEHOLDER — e.g., Qualified lead profile + personalised email sequence ready to send]

**Workflow variant:** [PLACEHOLDER — e.g., Full (all personas), Quick (skip research), Simple (minimal pipeline)]

---

## AI Quick Start

### Starting a New [PLACEHOLDER — e.g., Lead, Article, Research Report, Project]

**Step 1 — Open a fresh AI session**

Paste this at the start of every new session:

```
You are working on the [PLACEHOLDER — e.g., AI Sales Workflow] project.

Read these files before starting:
- CONSTITUTION.md (non-negotiable rules — read first, always)
- memory/CONTEXT.md (current state — what phase are we in?)
- memory/MEMORY.md (project history — what's happened so far?)
- memory/PROJECT-LEARNINGS.md (cross-project patterns — what have we learned?)

Confirm you have read all four files, then tell me:
1. The current phase and active persona
2. Any blocking issues from CONTEXT.md
3. One relevant pattern from PROJECT-LEARNINGS.md (if any exist yet)

Wait for my instructions.
```

**Step 2 — Run the active persona**

Copy the persona prompt from `personas/[PLACEHOLDER — e.g., 01-qualifier].md` and paste it into the AI session. Provide the required inputs listed in the persona file.

**Step 3 — Review output and checkpoint**

- Read the output artifact
- Check against the quality checklist at the bottom of the persona file
- If APPROVED: copy the artifact to the `artifacts/` folder with proper naming convention
- If REVISE: tell the AI what to fix and re-run
- Update `memory/MEMORY.md` with what happened

---

### Resuming a [PLACEHOLDER — e.g., Lead, Article] In Progress

**Step 1 — Load context**

```
You are resuming work on the [PLACEHOLDER — e.g., AI Sales Workflow] project.

Read these files:
- CONSTITUTION.md
- memory/CONTEXT.md
- memory/MEMORY.md (last 5 entries minimum)

Tell me where we left off and what the next step is.
```

**Step 2 — Continue from the active persona**

The active persona will be recorded in `memory/CONTEXT.md`. Pick up from there.

---

## Key Directories

```
[PLACEHOLDER — e.g., ai-sales-workflow]/
├── CONSTITUTION.md              ← Non-negotiable rules (read first, always)
├── CLAUDE.md                    ← This file
├── personas/                    ← One file per pipeline persona
│   ├── 01-[PLACEHOLDER — e.g., qualifier].md
│   ├── 02-[PLACEHOLDER — e.g., researcher].md
│   ├── 03-[PLACEHOLDER — e.g., strategist].md
│   ├── 04-[PLACEHOLDER — e.g., copywriter].md
│   └── 05-[PLACEHOLDER — e.g., critic].md
├── prompts/                     ← Copy-paste prompts for each persona
│   ├── 01-[PLACEHOLDER — e.g., qualify-lead].md
│   ├── 02-[PLACEHOLDER — e.g., research-lead].md
│   └── ...
├── memory/                      ← Project memory files (do not delete)
│   ├── CONTEXT.md               ← Volatile: current phase state (~500 tokens max)
│   ├── MEMORY.md                ← Persistent: full project history (append-only)
│   └── PROJECT-LEARNINGS.md    ← Cross-project patterns (updated after failures)
└── artifacts/                   ← All AI-generated outputs
    ├── [PLACEHOLDER — e.g., 01-01-lead-profile-v1.md]
    └── [PLACEHOLDER — e.g., 01-04-email-sequence-v1.md]
```

**Artifact naming convention:** `[PROJECT#]-[PERSONA#]-[artifact-type]-v[VERSION].md`

Examples:
- `01-01-lead-profile-v1.md` — Project 01, Persona 01, first version
- `01-04-email-sequence-v2.md` — Project 01, Persona 04, second iteration after revision

---

## Memory Protocol

The project uses a three-file memory system to prevent context saturation and preserve decisions across sessions.

### CONTEXT.md — Volatile (~500 tokens max)

**What it is:** Working memory for the current phase. Think of it as a whiteboard — written on during a phase, wiped at phase transition.

**When to read:** At the start of every AI session (after CONSTITUTION.md).

**When to update:** After each persona completes, record:
- Current phase and active persona
- Key decisions made this phase
- Any blocking issues
- What the next persona needs to know

**When to clear:** At phase boundaries (e.g., r→K, K→Ω). Summarise important decisions to MEMORY.md first, then clear CONTEXT.md.

### MEMORY.md — Persistent (append-only, never delete)

**What it is:** The full project history. Every persona run, every artifact, every human decision.

**When to read:** At the start of sessions when you need context beyond the current phase.

**When to update:** After every significant event — persona completion, artifact creation, human approval/rejection, phase transition.

**Format:**
```markdown
## [YYYY-MM-DD] — [Persona Name] ([Phase])
- What was produced
- Key decisions made
- **Artifact:** [filename]
- **Verdict:** [APPROVED / REVISED / REJECTED]
- **Human notes:** "[any feedback]"
```

**Rule:** Append only. Never modify past entries.

### PROJECT-LEARNINGS.md — Cross-Project Intelligence

**What it is:** Patterns extracted from multiple projects. What works, what doesn't, what triggers constitution updates.

**When to read:** At session start, skim for relevant patterns before running a persona.

**When to update:** Only after a RESTRUCTURE or RELEASE verdict (score <70). The final persona in the pipeline (Evolutionist / Critic) is responsible for writing learnings.

---

## Persona Pipeline

```
[PHASE 1: r — Growth/Exploration]
        │
        ▼
[PLACEHOLDER — e.g., 01 — Qualifier]
Defines the opportunity. What are we working with?
        │
        ▼
[PLACEHOLDER — e.g., 02 — Researcher]  ← optional, skip for Quick/Simple
Deep context gathering.
        │
        ▼
[PHASE 2: K — Conservation/Production]
        │
        ▼
[PLACEHOLDER — e.g., 03 — Strategist]
Plans the approach.
        │
        ▼
[PLACEHOLDER — e.g., 04 — [Creator / Writer / Builder]]
Produces the primary output artifact.
        │
        ▼
[PLACEHOLDER — e.g., 05 — Editor / Validator]
Checks quality, enforces constitution.
        │
        ▼
[PHASE 3: Ω — Release/Quality Gate]
        │
        ▼
[PLACEHOLDER — e.g., 06 — Critic]
Scores against 5 dimensions. Issues final verdict.
        │
        ├─ Score ≥85 → APPROVE → Human reviews → Ship
        ├─ Score 70–84 → REVISE → Back to [Creator]
        ├─ Score 50–69 → RESTRUCTURE → Back to [Strategist]
        └─ Score <50 → RELEASE → α-phase triggers
                                │
                                ▼
                    [PHASE 4: α — Evolution]
                    [PLACEHOLDER — e.g., 07 — Evolutionist]
                    Updates constitution + learnings.
                    Returns to r-phase for next project.
```

---

## Quality Gates

The Critic persona scores every output against five dimensions (0–20 points each, 100 total).

| Score Range | Verdict | Action |
|-------------|---------|--------|
| 85–100 | APPROVE | Human reviews. If approved, ship. |
| 70–84 | REVISE | Return to [PLACEHOLDER — e.g., Copywriter]. Fix specific issues. |
| 50–69 | RESTRUCTURE | Return to [PLACEHOLDER — e.g., Strategist]. Fundamental approach problem. |
| <50 | RELEASE | Trigger evolution. Update constitution. Start next project fresh. |

**Scoring dimensions** (defined in CONSTITUTION.md):
1. [PLACEHOLDER — e.g., Fit Accuracy] — 0–20
2. [PLACEHOLDER — e.g., Personalisation Depth] — 0–20
3. [PLACEHOLDER — e.g., Strategic Alignment] — 0–20
4. [PLACEHOLDER — e.g., Tone and Voice] — 0–20
5. [PLACEHOLDER — e.g., Actionability] — 0–20

---

## Human Checkpoints

Not every persona requires human review. Mandatory checkpoints are marked in each persona file.

**Mandatory checkpoints** (do not skip):
- [PLACEHOLDER — e.g., After Qualifier — confirm the lead is worth pursuing before research]
- [PLACEHOLDER — e.g., After Critic — final approval before sending]

**Optional checkpoints** (review if time permits):
- [PLACEHOLDER — e.g., After Strategist — validate approach before writing]

---

## Getting Help

- **Stuck on a persona?** Re-read the persona file. The "Constraints" section usually explains the issue.
- **AI ignoring the constitution?** Paste the relevant CONSTITUTION.md section directly into the prompt.
- **Context getting messy?** Clear CONTEXT.md, summarise key decisions to MEMORY.md, start a fresh session.
- **Recurring failures?** Check PROJECT-LEARNINGS.md. If the pattern is new, add it after completing the α-phase.

---

*Project created using [AI Workflow Orchestrator](https://github.com/[PLACEHOLDER — e.g., your-org/ai-workflow-orchestrator])*
*Template version: 1.0*
