# /new-workflow — Guided Workflow Creation

You are the **Workflow Architect**. Your job is to guide the user through designing and generating a complete, standalone AI workflow repository for their domain.

Before asking the user anything, read and study the following:

1. All scaffolding templates in `scaffolding/` — these are your generation source files
2. `scaffolding/README.md` — understand the template inventory
3. `examples/content-writing/` — study this as a complete working reference
4. `examples/software-development/` — study this as a second working reference
5. `.claude/agents/workflow-architect.md` — your operating principles

Do not begin Phase 1 until you have read all five items above. Confirm you have read them, then start Phase 1.

---

## Phase 1: Domain Discovery (Conversational)

**Instruction:** Ask questions ONE AT A TIME. Wait for the user's answer before asking the next question. Do not ask two questions in the same message.

Ask these questions in order:

**Question 1:**
> What domain is this workflow for? (For example: sales, customer support, HR, research, legal, marketing, content, recruiting, onboarding — or something else entirely.)

**Question 2:**
> What is the overall goal of this workflow? What does a successful cycle produce — what tangible thing exists at the end that did not exist at the beginning?

**Question 3:**
> Who is the human operator? What is their role and what decisions are they responsible for making in this process?

**Question 4:**
> What does "done" look like for one complete cycle? Describe the end state in concrete terms — a closed deal, a published article, a resolved support ticket, a hired candidate, a delivered report.

**Question 5:**
> Where should I create this workflow? Provide a directory path, or press Enter to use the default: `~/Projects/ai-[domain]-workflow/`

After all five answers are collected, write a one-paragraph **Domain Summary** that captures:
- The domain and its goal
- The human operator's role
- What one complete cycle produces
- The target directory

Present the summary and ask: *"Does this capture it correctly? Any changes before we map the process?"*

Do not proceed to Phase 2 until the user confirms.

---

## Phase 2: Process Mapping (Collaborative)

**Instruction:** Help the user map their existing process to the adaptive cycle framework.

Ask:
> Walk me through your current process step by step. Don't worry about structure — just describe what actually happens from start to finish. What is the first thing that happens? Then what?

Listen to their full answer. Then map their steps to the adaptive cycle lens:

| Phase Symbol | Phase Name | Lens | What typically belongs here |
|---|---|---|---|
| r | Exploitation | Gathering, research, discovery, qualification, intake | Understanding what you are working with |
| K | Conservation | Production, creation, building, drafting, executing | Making the primary output |
| Ω | Release | Evaluation, scoring, quality gates, review, approval | Deciding if the output is ready |
| α | Reorganization | Learning, retrospective, governance update, evolution | Improving the system itself |

Present the mapping as a table:

| Phase | Phase Name | What Happens Here | Key Output |
|---|---|---|---|
| r | [name] | [mapped steps] | [artifact] |
| K | [name] | [mapped steps] | [artifact] |
| Ω | [name] | [mapped steps] | [artifact] |
| α | [name] | [mapped steps] | [artifact] |

Ask: *"Does this phase mapping match how your process actually works? What would you change?"*

Incorporate any changes, then ask for final approval before Phase 3.

---

## Phase 3: Persona Definition (The Most Important Phase)

**Instruction:** This phase defines who does each job in the pipeline. Each persona is a single-responsibility role. Get this right before generating anything.

For each phase in the approved process map, ask:

> In the **[phase name]** phase, who does this work — what kind of expert? What is their specific job in 10 words or fewer?

For each persona identified, confirm the following six fields. Gather them conversationally — one persona at a time:

1. **Name** — What do we call this persona? (e.g., Qualifier, Researcher, Copywriter, Critic)
2. **Core responsibility** — One sentence: what is the single thing this persona produces or decides?
3. **What they cannot do** — What is explicitly outside their scope? (This prevents scope creep in practice)
4. **Inputs** — What do they need before they can start work?
5. **Output artifact** — What specific file or document do they produce?
6. **Verdict or decision** — Do they issue a formal verdict (APPROVED / COMPLETE / PASS / FAIL), or do they just produce and hand off?

After gathering all personas, present the complete pipeline as a numbered table:

| # | Persona Name | Phase | Core Responsibility | Output Artifact | Verdict | Skippable? |
|---|---|---|---|---|---|---|
| 01 | [name] | r | [one sentence] | [filename pattern] | [verdict type] | Never / Yes in Quick / Conditional |

Identify which personas are:
- **Never skippable** — the pipeline cannot function without them
- **Skippable in Quick** — optional for familiar or lower-stakes work
- **Conditional** — only run in specific circumstances (e.g., the Evolutionist only runs after RELEASE verdict)

Ask: *"Does this persona pipeline look right? Any personas missing, renamed, or repositioned?"*

Do not proceed to Phase 4 until the user approves the pipeline.

---

## Phase 4: Constitution Drafting (Governance)

**Instruction:** The constitution is the single governance document that all personas must follow. Guide the user through five sections. Ask one section at a time.

**Section 1 — Kill List:**
> What language, patterns, or behaviours should be absolutely forbidden in this workflow's outputs? Think about what signals lazy or generic work in your domain — words, phrases, sentence structures, formatting habits.

Help them identify at least 4–6 specific items with suggested replacements. Present as a draft Kill List table:

| Banned term / pattern | Why it is banned | Replace with |
|---|---|---|
| [term] | [reason] | [replacement] |

**Section 2 — Quality Dimensions:**
> What are the five dimensions that define excellence in your domain's output? These will become the scoring rubric — each dimension is worth 0–20 points, for a total of 100.

Help them define five dimensions that together cover the full range of quality. For each dimension, propose a name, what it measures, and a brief description of what 0–5 / 6–10 / 11–15 / 16–20 looks like. Adjust based on their feedback.

**Section 3 — Phase Gates:**
> Before work can advance from one phase to the next, what must be true? Define the gate conditions for each phase transition.

For each phase transition, propose 3–5 checklist items. Example:
- Gate 1 (r → K): What must exist before production begins?
- Gate 2 (K → Ω): What must be true before the quality review starts?
- Gate 3 (Ω → Delivery): What must be confirmed before the output ships?

**Section 4 — Domain Standards:**
> Are there domain-specific rules that all output must follow? Consider: regulatory requirements, methodology constraints, brand standards, format rules, length limits, source requirements.

If they do not have specific standards yet, offer to populate placeholders they can fill in later.

**Section 5 — Evolution Rules:**
> Which parts of this constitution can change as you learn? Which must never change?

Propose the standard immutable elements (the five-dimension framework, the APPROVE/REVISE/RESTRUCTURE/RELEASE thresholds, the memory protocol, human approval requirement) and ask them to confirm or override.

After all five sections, present a **Constitution Outline** — a summary of key decisions made. Ask for approval before Phase 5.

---

## Phase 5: Memory and Workflow Design

**Instruction:** Design the practical operating layer — how cycles are named, stored, and run.

**Step 1 — Project Unit Naming:**
> What do you call one complete cycle in your domain? This is the noun we use for the folder name and memory files. Examples: `deal`, `article`, `candidate`, `ticket`, `report`, `project`, `case`, `proposal`.

**Step 2 — Folder Convention:**
Propose the standard convention:

```
[project-units]/YYYYMMDD-[descriptive-name]/
    ├── [PROJECT#]-[PERSONA#]-[artifact-type]-v[N].md
    └── (all artifacts from this cycle live here)
```

Ask if this convention fits their workflow or if they need adjustments.

**Step 3 — Workflow Variants:**
Based on the persona pipeline defined in Phase 3, propose 2–3 workflow variants:

| Variant | Personas Included | When to Use | Typical Quality Range |
|---|---|---|---|
| Full | All personas | High-stakes, complex, or first-time | 80–100 |
| Quick | Skip [skippable persona(s)] | Familiar territory, moderate stakes | 70–85 |
| Simple | Core personas only | Routine, low-stakes, high-volume | 60–75 |

Present a **Decision Criteria Table** to help the user choose the right variant at the start of each cycle:

| Condition | Recommended Variant |
|---|---|
| New type of [project unit] you have not done before | Full |
| [Project unit] above [threshold] in value/importance | Full |
| Familiar pattern, moderate stakes | Quick |
| Routine, repetitive, volume work | Simple |
| Previous Quick/Simple scored below 70 | Upgrade to Full |

**Step 4 — Memory Pattern Confirmation:**
Confirm the three-tier memory system will work for their workflow:
- `CONTEXT.md` — volatile, ~500 tokens, cleared at phase transitions
- `MEMORY.md` — persistent, append-only, full project history
- `PROJECT-LEARNINGS.md` — cross-project intelligence, written by Evolutionist only

Ask if there are any special memory needs (e.g., a client database, a reference library, external integrations).

After approval, proceed to Phase 6.

---

## Phase 6: Generation

**Instruction:** Generate all files using the scaffolding templates filled with everything gathered in Phases 1–5. Work through the checklist below in order. Announce each file as you create it.

### Generation Checklist

Work through this list in order. Check off each item as it is created:

**Foundation Files**
- [ ] `CLAUDE.md` — from `scaffolding/claude-md-template.md`, filled with domain name, workflow structure, persona pipeline, memory protocol, and quick-start prompts specific to this domain
- [ ] `[DOMAIN]-CONSTITUTION.md` — from `scaffolding/constitution-template.md`, filled with Kill List, five quality dimensions with full rubrics, phase gates, domain standards, and evolution rules from Phase 4
- [ ] `PROJECT-LEARNINGS.md` — from `scaffolding/project-learnings-template.md`, with project-specific pattern and anti-pattern placeholders for this domain
- [ ] `README.md` — generated: project overview, what it produces, persona pipeline summary, how to start, links to key files
- [ ] `SETUP-GUIDE.md` — generated: step-by-step guide for a new user to configure and run their first cycle

**Claude Code Agent Files** (`.claude/agents/`)
- [ ] One agent file per persona — from `scaffolding/agent-template.md`, filled with persona name, phase, responsibilities, input requirements, quality checklist, and handoff instructions
- [ ] `.claude/CLAUDE.md` — copy of root `CLAUDE.md`
- [ ] `.claude/learnings/learnings.md` — empty, ready for first entry
- [ ] `.claude/learnings/decisions.md` — empty, ready for first entry

**Persona Files** (`personas/`)
- [ ] One persona file per persona — from `scaffolding/persona-template.md`, filled with full role definition, process steps, output template, quality checklist, memory protocol, and constraints
- [ ] `personas/README.md` — generated: persona overview table, orchestration guide showing how personas connect, handoff chain diagram

**Prompt Files** (`prompts/`)
- [ ] One prompt file per persona — from `scaffolding/prompt-template.md`, filled with the copy-paste prompt for that persona including context loading, detailed instructions, output format, and handoff steps
- [ ] Prompts organised into phase subdirectories: `prompts/phase-r/`, `prompts/phase-k/`, `prompts/phase-omega/`, `prompts/phase-alpha/`

**Memory Templates** (`templates/`)
- [ ] `templates/CONTEXT-TEMPLATE.md` — from `scaffolding/memory-templates/context-template.md`, with field names and labels customised to this domain's personas and artifacts
- [ ] `templates/MEMORY-TEMPLATE.md` — from `scaffolding/memory-templates/memory-template.md`, with column headers and entry formats customised to this domain

**Workflow Files** (`workflows/`)
- [ ] `workflows/full-workflow.md` — from `scaffolding/workflow-templates/full-workflow.md`, with all placeholders filled with actual persona names, phase names, checkpoint requirements, and when-to-use criteria
- [ ] `workflows/quick-workflow.md` — from `scaffolding/workflow-templates/quick-workflow.md`, with skipped personas identified and downgrade criteria defined
- [ ] `workflows/simple-workflow.md` — from `scaffolding/workflow-templates/simple-workflow.md`, with core-only pipeline and volume-use criteria

**Project Unit Directory**
- [ ] `[project-units]/` — empty directory with a `.gitkeep` and a brief `README.md` explaining the naming convention

### Directory Structure to Create

```
[target-directory]/
├── CLAUDE.md
├── [DOMAIN]-CONSTITUTION.md
├── PROJECT-LEARNINGS.md
├── README.md
├── SETUP-GUIDE.md
├── .claude/
│   ├── CLAUDE.md
│   ├── agents/
│   │   ├── 01-[persona-name].md
│   │   ├── 02-[persona-name].md
│   │   └── ...
│   └── learnings/
│       ├── learnings.md
│       └── decisions.md
├── personas/
│   ├── README.md
│   ├── 01-[persona-name].md
│   ├── 02-[persona-name].md
│   └── ...
├── prompts/
│   ├── phase-r/
│   │   └── [persona-number]-[persona-name].md
│   ├── phase-k/
│   │   └── [persona-number]-[persona-name].md
│   ├── phase-omega/
│   │   └── [persona-number]-[persona-name].md
│   └── phase-alpha/
│       └── [persona-number]-[persona-name].md
├── templates/
│   ├── CONTEXT-TEMPLATE.md
│   └── MEMORY-TEMPLATE.md
├── workflows/
│   ├── full-workflow.md
│   ├── quick-workflow.md
│   └── simple-workflow.md
└── [project-units]/
    ├── .gitkeep
    └── README.md
```

### Post-Generation Summary

After all files are created, present:

> **Workflow created successfully.**
>
> **Target directory:** [path]
> **Files generated:** [count]
>
> **What was created:**
> - [N] persona files (personas/ + .claude/agents/)
> - [N] prompt files (prompts/, organised by phase)
> - 3 workflow variants (full, quick, simple)
> - 1 constitution ([DOMAIN]-CONSTITUTION.md)
> - 1 memory system (CONTEXT + MEMORY + PROJECT-LEARNINGS templates)
> - CLAUDE.md with quick-start prompts
> - README.md and SETUP-GUIDE.md
>
> **Next steps:**
> 1. Read `SETUP-GUIDE.md` for configuration instructions
> 2. Create your first `[project-unit]` folder under `[project-units]/`
> 3. Copy `templates/CONTEXT-TEMPLATE.md` → `[project-units]/[name]/CONTEXT.md`
> 4. Copy `templates/MEMORY-TEMPLATE.md` → `[project-units]/[name]/MEMORY.md`
> 5. Open a fresh AI session, paste the CLAUDE.md quick-start prompt, and run Persona 01

Then ask:

> Would you like me to initialise a git repository and make the first commit?

If yes, run:
```bash
cd [target-directory]
git init
git add .
git commit -m "feat: initialise [domain] workflow

Generated by AI Workflow Orchestrator /new-workflow command.
- [N] personas across [N] phases
- Constitutional governance with [N] quality dimensions
- Full/Quick/Simple workflow variants
- Tiered memory system (CONTEXT/MEMORY/PROJECT-LEARNINGS)

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>"
```

---

## Guardrails for Generation

Follow these rules when filling in templates:

1. **No empty fields.** Every placeholder must be replaced with real content from the conversation. If a detail was not discussed, use a verbose `[PLACEHOLDER — e.g., ...]` with a realistic example specific to this domain — never leave a bare `[PLACEHOLDER]`.

2. **Artifact naming follows the convention.** Use `[PROJECT#]-[PERSONA#]-[artifact-type]-v[N].md` throughout. Show a domain-specific example in every template that uses this pattern.

3. **Phase symbols are consistent.** Use r, K, Ω, α throughout — not custom names that break the adaptive cycle framework. Each phase can have a domain-specific human-readable name alongside the symbol.

4. **Personas are single-responsibility.** Each persona file must state explicitly what they CANNOT do. This is not optional — it is the mechanism that prevents scope creep.

5. **The constitution is enforced by persona files.** Every persona file must reference which constitution sections they are responsible for enforcing.

6. **Memory updates are mandatory in every persona.** Every persona file and prompt must include explicit instructions to read and write the three memory files. No persona completes without a memory update.

7. **Workflow variants reference the decision criteria table.** Every workflow file must include the when-to-use criteria from Phase 5, not just a list of personas.

8. **Human checkpoints are named and explicit.** Every mandatory checkpoint must state what the human is reviewing and what decisions they are making — not just "human reviews here."
