# Example Workflows

> **These are reference examples — not the tool itself.** To create your own workflow, use `/new-workflow` in Claude Code or follow the [Quick Start](../QUICKSTART.md).

Study these examples to understand the patterns before creating your own.

---

## Software Development Example

**Build production-ready software using AI with constitutional governance and specialized personas.**

### What's Included
- **5 Personas:** Product Owner → Solutions Architect → Specialist Developer → QA Engineer → Technical Writer
- **5 Phases with 16 Prompts:** Setup, Planning, Implementation, Review, Documentation
- **3 Constitution Templates:** Internal tool, Client app, AI agent

### Workflow Shape
```
Phase 0: Complexity Estimator
Phase 1: Product Owner (PRD) → Architect (Tech Spec, Schema, API)
Phase 2: Specialist Developer (Implementation)
Phase 3: QA Engineer (Testing, Security, Code Review)
Phase 4: Technical Writer (Documentation)
```

**[Explore the Software Development Example →](./software-development/)**

---

## Content Writing Example

**Create high-quality content using AI with brand voice consistency and structured quality gates.**

### What's Included
- **5 Personas:** Content Strategist → Content Architect → Content Writer → Fact Checker → Editor
- **4 Phases with 12 Prompts:** Planning, Creation, Refinement, Publishing
- **3 Constitution Templates:** Blog, Marketing, Technical docs

### Workflow Shape
```
Phase 1: Content Strategist (Brief, Keywords, Outline)
Phase 2: Content Architect (Structure) + Content Writer (First Draft)
Phase 3: Fact Checker → Editor
Phase 4: Meta Tags → Distribution Checklist
```

**[Explore the Content Writing Example →](./content-writing/)**

---

## Production Example (External)

**[ai-dev-orchestrator](https://github.com/Optiminz/ai-dev-orchestrator)** — A production coding workflow built with this framework. Shows how constitutions, personas, and phases work together in a real project context.

---

## What to Look For in These Examples

Study these patterns as you read through the examples:

**Persona structure (single responsibility)**
Each persona owns exactly one phase or concern. The Product Owner never writes code; the QA Engineer never writes docs. This boundary prevents context bleed and keeps AI outputs focused.

**Constitutions as quality definitions**
The Kill List in each constitution template defines what failure looks like — not what success looks like. This inversion is intentional: it's easier to define and detect failure than to enumerate all forms of success.

**Phases as quality gates**
Work only moves forward when the current phase output meets its acceptance criteria. The next persona's prompt assumes the previous output is complete and valid.

**Prompts mapped to personas (copy-paste ready)**
Each prompt is scoped to a single persona in a single phase. You copy the prompt, paste it into a new Claude session, and the persona context is fully established within that prompt — no prior conversation history required.

---

## Using Personas Across Examples

You can mix personas from different examples when your project spans domains.

**Example: Technical Blog Post**
- Use **Content Strategist** (content example) for the brief
- Use **Specialist Developer** (software example) for code examples
- Use **Fact Checker** (content example) for accuracy review
- Use **Technical Writer** (software example) for clarity and structure

Personas are modular. Adapt the framework to your actual workflow rather than forcing your workflow into a predefined shape.

---

## Building a Custom Workflow

The examples above are starting points, not requirements. See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidance on:
- Creating new personas with single-responsibility scope
- Structuring constitution templates for your domain
- Designing prompts that are copy-paste ready with no implicit context

---

## Questions?

- **Quick Start:** [5-Minute Guide](../QUICKSTART.md)
- **Working Solo:** [Solo Practitioner Guide](../docs/guides/working-solo.md)
- **Working with Teams:** [Team Collaboration Guide](../docs/guides/working-with-teams.md)
- **Customizing Personas:** [Persona Customization Guide](../docs/guides/customizing-personas.md)
