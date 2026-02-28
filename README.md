# AI Workflow Orchestrator

Turn any domain process into a structured AI workflow with constitutional governance, specialized personas, and quality scoring.

```
┌─────────────────────────────────────────┐
│         CONSTITUTION                    │
│    (Governance, Kill List, scoring)     │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│     SPECIALIZED PERSONAS               │
│  (One job each — explicit I/O)         │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│       ADAPTIVE PHASES                   │
│  r (gather) → K (produce) →            │
│  Ω (evaluate) → α (learn)              │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│      SCORED ARTIFACTS                   │
│  (0-100 scores, named verdicts)         │
└─────────────────────────────────────────┘
```

---

## Create Your Workflow

### Prerequisites

- **With Claude Code:** [Install Claude Code](https://claude.ai/claude-code), then clone this repo and open it
- **Without Claude Code:** Browse `examples/` and manually adapt the `scaffolding/` templates (see [Without Claude Code](#without-claude-code))

### With Claude Code

```bash
git clone https://github.com/Optiminz/ai-workflow-orchestrator.git
cd ai-workflow-orchestrator
# Open in Claude Code, then run:
/new-workflow
```

Follow the guided 6-phase flow. The wizard asks about your domain, team structure, quality standards, and output format — then generates a complete workflow scaffold.

### What You Get

```
your-workflow/
├── CLAUDE.md              # AI operating instructions
├── CONSTITUTION.md        # Quality standards & governance
├── personas/              # Single-responsibility AI roles
├── prompts/               # Copy-paste prompts (works with any AI)
├── .claude/agents/        # Claude Code agent files
├── workflows/             # Full, Quick, Simple variants
└── templates/             # Memory & artifact schemas
```

---

## How It Works

Five concepts underpin every generated workflow. Each links to deeper reading.

**[Constitution](docs/concepts/what-is-constitutional-ai.md)**
A single governance document containing the Kill List (automatic fail conditions), scoring dimensions, and evolution rules. Every persona checks work against it before passing output forward.

**[Personas](docs/concepts/why-personas-not-prompts.md)**
Single-responsibility AI roles. Each has one job, explicit inputs and outputs, and a defined set of constraints. They check each other's work rather than working in isolation.

**[Phases](docs/concepts/the-adaptive-cycle.md)**
An adaptive cycle adapted from ecological systems theory: r (gather information) → K (produce output) → Ω (evaluate against constitution) → α (extract learnings). Applied differently per domain.

**Memory**
Three tiers: CONTEXT (volatile, current session only), MEMORY (persistent across sessions), PROJECT-LEARNINGS (cross-project patterns). Generated workflows include templates for all three.

**Quality Scoring**
Numeric scores (0–100) mapped to named verdicts: APPROVE / REVISE / RESTRUCTURE / RELEASE. Removes ambiguity from review cycles — every artifact gets a score, not just feedback.

---

## Examples

### Software Development
5 personas, 5 phases, 3 constitution templates (internal tool, client app, AI agent).
→ [examples/software-development/](examples/software-development/)

### Content Writing
5 personas, 4 phases, 3 constitution templates (blog, marketing, technical docs).
→ [examples/content-writing/](examples/content-writing/)

### Production Example
The [ai-dev-orchestrator](https://github.com/Optiminz/ai-dev-orchestrator) is a full software development workflow built with this framework — all personas, phases, and constitution in active use.

---

## Without Claude Code

Generated workflows include a `prompts/` directory with copy-paste prompts that work with any AI tool (ChatGPT, Gemini, Claude.ai, etc.).

If you want to build a workflow manually without the `/new-workflow` wizard:
1. Browse `examples/` to find the closest match to your domain
2. Copy the relevant `scaffolding/` templates
3. Fill in the placeholders following the inline guidance

---

## Learn More

- [What is Constitutional AI?](docs/concepts/what-is-constitutional-ai.md)
- [Why Personas, Not Prompts?](docs/concepts/why-personas-not-prompts.md)
- [The Adaptive Cycle](docs/concepts/the-adaptive-cycle.md)
- [Quick Start Guide](QUICKSTART.md)
- [Contributing](CONTRIBUTING.md)

---

## Contributing

Contributions welcome — new domains, personas, and constitution templates. See [CONTRIBUTING.md](CONTRIBUTING.md) for standards and submission process.

## License

MIT — see [LICENSE](LICENSE) for details.
