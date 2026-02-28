# What Is Constitutional AI Governance?

Constitutional AI governance has nothing to do with AI safety research. It's a practical pattern for controlling AI output quality — a single file that every persona in your workflow reads before doing anything.

Here's the short version: instead of repeating your quality rules in every prompt, you write them once in a `CONSTITUTION.md` file, and every persona in your workflow references that file as the source of truth.

---

## The Problem It Solves

Without a constitution, your rules live in your prompts. You might tell the Writer persona "don't use jargon" and the Editor persona "avoid buzzwords" — but those are separate instructions that can drift apart over time, contradict each other, and get lost when you update one but forget to update the other.

A constitution centralises everything. One file. One source of truth. Every persona checks it before producing output.

---

## What a Constitution Contains

A constitution is a markdown file with four main sections:

**1. Project overview** — what you're building, who it's for, what success looks like.

**2. Core principles** — non-negotiable rules. In software development, this might be "never use a framework not listed in the tech stack." In content writing, it might be "every statistical claim must have a citation."

**3. The Kill List** — explicitly prohibited vocabulary and patterns.

**4. Quality dimensions** — the scored criteria used to evaluate output.

Here's what a Kill List looks like in practice, from the blog constitution template:

```
Banned: "game-changing"
Why: Empty hype with no specificity
Use instead: A concrete description of the actual change
```

```
Banned: "leverage" (when used as a verb meaning "use")
Why: Corporate jargon that obscures meaning
Use instead: use, apply, deploy
```

```
Banned: "seamless"
Why: Oversold promise that means nothing
Use instead: smooth, integrated, frictionless
```

The Kill List forces specificity. "Game-changing" is banned not because it sounds bad, but because it communicates nothing. A writer who can't use it has to write something like "reduces deployment time from 2 hours to 8 minutes" — which is actually informative.

---

## Quality Dimensions and Verdicts

The scoring section of a constitution defines five dimensions, each worth 0–20 points, for a total of 100. Your QA or Editor persona scores work against these dimensions, then issues a verdict based on the total.

**Example from a content writing constitution:**

| Dimension | Description | Max Points |
|-----------|-------------|------------|
| Voice Consistency | Matches brand tone, avoids Kill List words | 20 |
| Factual Accuracy | All claims cited, no hallucinations | 20 |
| SEO Optimization | Keywords placed correctly, meta tags complete | 20 |
| Reader Engagement | Strong hook, clear structure, useful CTA | 20 |
| Strategic Alignment | Serves the stated content goal | 20 |

**Total → Verdict:**

| Score | Verdict | Meaning |
|-------|---------|---------|
| 85–100 | APPROVE | Ready to publish |
| 70–84 | REVISE | Minor fixes needed |
| 50–69 | RESTRUCTURE | Significant rework required |
| 0–49 | RELEASE | Triggers the Evolutionist |

The RELEASE verdict is the unusual one. It doesn't mean "publish" — it means the work failed badly enough that the constitution itself needs updating. More on that below.

---

## Why One File Beats Repeated Instructions

When you paste quality rules into individual prompts, three things happen over time:

1. **Drift** — you update the Writer prompt but forget the Editor prompt. Now they have conflicting rules.
2. **Bloat** — every prompt grows longer as you add more rules, until the rules section is longer than the actual task instructions.
3. **Inconsistency** — different personas interpret the same intent differently because they're reading different words.

With a constitution, each persona gets one instruction: "read `CONSTITUTION.md` before you do anything." The rules are identical for everyone because they literally read the same file.

In practice, this means you can add a new banned word to the Kill List once, and every persona in your workflow immediately enforces it on the next project.

---

## The Constitution Evolves

Here's the part that makes this approach genuinely different from just writing a style guide: **the constitution updates itself through failure**.

When a QA or Editor persona scores work below the RELEASE threshold, it triggers the **Evolutionist** persona. The Evolutionist doesn't fix the current piece of work — that's already failed. Instead, it analyses the root cause and updates the constitution to prevent the same failure from recurring in future projects.

**Example from a content writing workflow:**

A blog post scores 42/100. The Evolutionist traces the failure to a consistent pattern: the Writer cited statistics without checking their age, and three of the four statistics were more than four years old.

The Evolutionist adds a rule to the constitution: "No statistics older than two years unless providing explicit historical context."

The next article automatically enforces this rule because the Writer persona reads the updated constitution before drafting.

The system gets smarter through failure rather than just documenting the same mistakes in a lessons-learned file that nobody reads.

---

## What This Looks Like in Practice

**Software development example:**

Your `CONSTITUTION.md` might specify:
- Tech stack: React, TypeScript, Node.js (no deviations without approval)
- Security: All API endpoints must validate input before processing
- Code style: Maximum function length 50 lines; single responsibility per function
- Kill List: No `any` types in TypeScript; no `console.log` in production code
- Quality dimensions: Functionality, Security, Code Quality, Test Coverage, Documentation

Every Developer persona reads this before implementing. Every QA persona reads it before reviewing. When the QA scores a PR at 38/100 because there are six `any` types and no tests, the Evolutionist traces the pattern to an unclear developer prompt and tightens the implementation instructions.

**Content writing example:**

Your `CONSTITUTION.md` might specify:
- Brand voice: Professional but conversational; use contractions; write to a colleague
- Kill List: "delve," "unlock," "leverage," "game-changing," "bustling," "seamless"
- Research: All claims require inline citation; statistics must include year and source
- Quality dimensions: Voice Consistency, Factual Accuracy, SEO Optimization, Reader Engagement, Strategic Alignment

The Writer reads this and knows exactly what to avoid. The Editor reads the same file and knows exactly what to check. No ambiguity, no drift.

---

## Key Takeaways

- A constitution is a single `CONSTITUTION.md` file — not a prompt, not a style guide, not a checklist
- It contains principles, a Kill List of banned patterns, and scored quality dimensions
- Every persona references it before producing output, giving you consistent enforcement across the entire workflow
- Quality scoring produces one of four verdicts: APPROVE, REVISE, RESTRUCTURE, or RELEASE
- RELEASE triggers the Evolutionist, who updates the constitution itself — the system learns from failure

---

**Next steps:**
- [Why Personas, Not Prompts?](./why-personas-not-prompts.md) — how roles enforce quality
- [The Adaptive Cycle](./the-adaptive-cycle.md) — how failure triggers system learning
- [Blog Constitution Template](../../examples/content-writing/templates/blog-constitution.md) — a complete example to copy
- [Internal Tool Constitution](../../examples/software-development/templates/internal-tool-constitution.md) — software version
