# AI Workflow Orchestrator

## What This Is

A scaffolding tool for creating AI-powered workflow repos. It turns any domain process into a structured, persona-driven workflow with constitutional governance, tiered memory, and quality scoring.

**This is not a template library.** It's a workflow creation tool. The `examples/` directory contains reference implementations you can study, but the real value is the `/new-workflow` command that builds you a complete workflow repo.

## Quick Start for Claude

When a user opens this project, determine their intent:

| Intent | Action |
|--------|--------|
| "Create a workflow" / `/new-workflow` | Run the /new-workflow command (`.claude/commands/new-workflow.md`) |
| Questions about the framework | Guide them through `docs/concepts/` |
| Exploring examples | Point to `examples/software-development/` and `examples/content-writing/` |
| "How does this work?" | Explain the pattern: Constitution → Personas → Phases → Artifacts |

## Key Concepts

- **Constitution**: A governance document that defines quality standards, prohibited patterns (Kill List), scoring dimensions, and evolution rules. Every persona enforces it.
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
