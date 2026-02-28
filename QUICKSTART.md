# Quick Start — Create Your First AI Workflow

---

## 1. Prerequisites

- **With Claude Code (recommended):** Install Claude Code at https://claude.ai/claude-code. That's it.
- **Without Claude Code:** You'll use the manual approach — browse examples and adapt templates by hand.

---

## 2. With Claude Code (5 minutes)

### Step 1: Clone and open

```bash
git clone https://github.com/Optiminz/ai-workflow-orchestrator.git
cd ai-workflow-orchestrator
claude  # opens Claude Code
```

### Step 2: Run the workflow wizard

```
/new-workflow
```

### Step 3: Follow the guided flow

Claude walks you through 6 phases:

1. **Domain Discovery** — What's this workflow for?
2. **Process Mapping** — How does your process work today?
3. **Persona Definition** — Who does what? (roles → personas → agents)
4. **Constitution Drafting** — What are your quality standards?
5. **Memory & Workflow Design** — How should work be tracked?
6. **Generation** — Claude creates all the files

### Step 4: Use your new workflow

```bash
cd ~/Projects/ai-[your-domain]-workflow
# Your workflow is ready — start with Persona 1
```

---

## 3. Without Claude Code (30 minutes)

### Step 1: Clone the repo and explore

```bash
git clone https://github.com/Optiminz/ai-workflow-orchestrator.git
cd ai-workflow-orchestrator
```

### Step 2: Study the examples

- Read `examples/software-development/` or `examples/content-writing/` to see the pattern
- Read `docs/concepts/` to understand the principles

### Step 3: Create your workflow manually

- Create a new directory for your workflow
- Copy templates from `scaffolding/` to your new directory
- Fill in the `[PLACEHOLDER — e.g., ...]` values with your domain specifics
- Key files to customize: constitution, personas, CLAUDE.md

### Step 4: Start using it

- Each persona has a matching copy-paste prompt in `prompts/`
- Paste the prompt into any AI tool (Claude, ChatGPT, etc.)
- Follow the phase order: r → K → Ω → α

---

## 4. What's Next

- Read your generated workflow's README and SETUP-GUIDE
- Run your first cycle end-to-end
- After 2–3 cycles, review and refine your constitution
- The system improves over time through the Evolutionist pattern

---

## 5. Common Questions

**"Do I need Claude Code?"**
No, but it's faster. Without it, use copy-paste prompts.

**"Can I modify the generated workflow?"**
Yes, it's yours. The scaffolding is a starting point.

**"What if my domain doesn't fit the r/K/Ω/α model?"**
Most do. If not, the wizard adapts the phases to your process.
