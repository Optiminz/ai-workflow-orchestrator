# Software Development Domain

Build production-ready software using AI with constitutional governance and specialized personas.

---

## What's Included

- **5 Personas:** Product Owner, Solutions Architect, Developer, QA Engineer, Technical Writer
- **16 Prompts:** Organized across 5 phases (setup, planning, implementation, review, documentation)
- **3 Constitution Templates:** Internal tool, Client app, AI agent
- **3 Tool Setup Guides:** Claude Code, Cursor, Replit

---

## Quick Start

### 1. Choose a Constitution Template

Pick a template from [`templates/`](./templates/) that matches your project type:

| Template | Best For | Key Focus |
|----------|----------|-----------|
| **[internal-tool-constitution.md](./templates/internal-tool-constitution.md)** | Internal tools (5-50 users) | Fast iteration, minimal security, function over form |
| **[client-app-constitution.md](./templates/client-app-constitution.md)** | Customer-facing apps | Production-grade security, polish, scalability |
| **[ai-agent-constitution.md](./templates/ai-agent-constitution.md)** | Bots, APIs, automation | Reliability, integration, monitoring |

Copy the template to your project and customize it.

### 2. Start with Phase 1: Planning

Use the **[Product Owner PRD prompt](./prompts/phase-1-planning/1.1-product-owner-prd.md)** to create your Product Requirements Document.

**Give the prompt to your AI:**
- Claude Code, Cursor, or Replit (as a project prompt)
- Copy-paste into ChatGPT or Claude (for manual workflow)

**Output:** `artifacts/01-prd.md`

### 3. Follow the Workflow

See the [Workflow Overview](./workflow/workflow-overview.md) for the full process.

---

## Personas Overview

| # | Persona | Responsibility | When to Use |
|---|---------|----------------|-------------|
| 1 | **[Product Owner](./personas/01-product-owner.md)** | Defines WHAT to build and WHY | Start of every project / feature |
| 2 | **[Solutions Architect](./personas/02-solutions-architect.md)** | Defines HOW to build it | After PRD approved |
| 3 | **[Specialist Developer](./personas/03-specialist-developer.md)** | Implements the solution | After tech spec approved |
| 4 | **[QA Engineer](./personas/04-qa-engineer.md)** | Validates quality (tests, security, code review) | After implementation done |
| 5 | **[Technical Writer](./personas/05-technical-writer.md)** | Documents the solution | After QA passes |

**[View All Persona Details →](./personas/)**

---

## Workflow Phases

### Phase 0: Setup
**Complexity Estimator** - Analyze project complexity and recommend workflow level (simple, standard, complex)

**Prompts:**
- [complexity-estimator.md](./prompts/phase-0-setup/complexity-estimator.md)

---

### Phase 1: Planning
Define WHAT to build (Product Owner) and HOW to build it (Solutions Architect)

**Prompts:**
1. [1.1-product-owner-prd.md](./prompts/phase-1-planning/1.1-product-owner-prd.md) - Product Requirements Document
2. [1.2-architect-tech-spec.md](./prompts/phase-1-planning/1.2-architect-tech-spec.md) - Technical Specification
3. [1.3-architect-database-schema.md](./prompts/phase-1-planning/1.3-architect-database-schema.md) - Database Schema (if applicable)
4. [1.4-architect-api-design.md](./prompts/phase-1-planning/1.4-architect-api-design.md) - API Design (if applicable)

**Outputs:** PRD, Tech Spec, Schema, API Design

---

### Phase 2: Implementation
Build the solution (Developer)

**Prompts:**
1. [2.1-generate-task-list.md](./prompts/phase-2-implementation/2.1-generate-task-list.md) - Break down tech spec into tasks
2. [2.2-iterative-implementation.md](./prompts/phase-2-implementation/2.2-iterative-implementation.md) - Implement one task at a time
3. [2.3-code-commenter.md](./prompts/phase-2-implementation/2.3-code-commenter.md) - Add comments to existing code

**Outputs:** Source code, implementation artifacts

---

### Phase 3: Review & Refactoring
Validate quality and refine (QA Engineer + Solutions Architect)

**Prompts:**
1. [3.1-qa-comprehensive-review.md](./prompts/phase-3-review/3.1-qa-comprehensive-review.md) - Full code review
2. [3.2-qa-bugs-edge-cases.md](./prompts/phase-3-review/3.2-qa-bugs-edge-cases.md) - Find bugs and edge cases
3. [3.3-qa-security-audit.md](./prompts/phase-3-review/3.3-qa-security-audit.md) - Security audit
4. [3.4-qa-style-standards.md](./prompts/phase-3-review/3.4-qa-style-standards.md) - Style and coding standards
5. [3.5-qa-testability.md](./prompts/phase-3-review/3.5-qa-testability.md) - Testing and testability review
6. [3.6-architect-refactor-consultation.md](./prompts/phase-3-review/3.6-architect-refactor-consultation.md) - Refactoring advice

**Outputs:** QA reports, security audit, refactored code

---

### Phase 4: Documentation
Document the solution (Technical Writer)

**Prompts:**
1. [4.1-readme-generator.md](./prompts/phase-4-documentation/4.1-readme-generator.md) - Generate README.md
2. [4.2-user-guide-generator.md](./prompts/phase-4-documentation/4.2-user-guide-generator.md) - Generate user guides

**Outputs:** README, user guides, API docs

---

## Workflow Type: Iterative

Software development uses an **iterative workflow**:

```
┌─────────────────────────────────────────┐
│  Plan (Phases 0-1)                      │
│  ↓                                       │
│  Implement (Phase 2)                    │
│  ↓                                       │
│  Review & Test (Phase 3)                │
│  ↓                                       │
│  Issues Found? → Back to Implement      │
│  ↓                                       │
│  All Pass? → Document (Phase 4)         │
└─────────────────────────────────────────┘
```

Unlike content writing (linear), software iterates between implementation and review multiple times.

**[View Full Workflow Details →](./workflow/workflow-overview.md)**

---

## Tool Setup Guides

Use your favorite AI coding tool with this framework:

- **[Claude Code Setup](./guides/claude-code-setup.md)** - Claude Code IDE integration
- **[Cursor Setup](./guides/cursor-setup.md)** - Cursor IDE integration
- **[Replit Setup](./guides/replit-setup.md)** - Replit AI integration

Each guide includes installation, project integration, workflow examples, best practices, and troubleshooting.

---

## Quick Start Workflows

For faster iteration on simple projects:

- **[Simple Workflow](./quick-start/simple-workflow.md)** - Simplified 2-3 hour feature workflow (minimal setup)
- **[Process Task List](./quick-start/process-task-list.md)** - How to manage task lists during implementation

---

## Common Workflows by Project Type

### Building a New Feature
1. **Product Owner:** Define what the feature does and why ([1.1-prd](./prompts/phase-1-planning/1.1-product-owner-prd.md))
2. **Architect:** Design how to implement it ([1.2-tech-spec](./prompts/phase-1-planning/1.2-architect-tech-spec.md))
3. **Developer:** Build it ([2.2-implementation](./prompts/phase-2-implementation/2.2-iterative-implementation.md))
4. **QA Engineer:** Test and review ([3.1-comprehensive-review](./prompts/phase-3-review/3.1-qa-comprehensive-review.md))
5. **Technical Writer:** Document it ([4.1-readme](./prompts/phase-4-documentation/4.1-readme-generator.md))

### Reviewing Existing Code
1. **QA Engineer:** Comprehensive review ([3.1](./prompts/phase-3-review/3.1-qa-comprehensive-review.md))
2. **QA Engineer:** Security audit ([3.3](./prompts/phase-3-review/3.3-qa-security-audit.md))
3. **Architect:** Refactoring consultation ([3.6](./prompts/phase-3-review/3.6-architect-refactor-consultation.md))

### Improving Documentation
1. **Technical Writer:** Generate README ([4.1](./prompts/phase-4-documentation/4.1-readme-generator.md))
2. **Technical Writer:** Create user guides ([4.2](./prompts/phase-4-documentation/4.2-user-guide-generator.md))
3. **Developer:** Add code comments ([2.3](./prompts/phase-2-implementation/2.3-code-commenter.md))

---

## Tips for Success

### 1. Start with a Constitution
Don't skip this step. Your `CONSTITUTION.md` file:
- Prevents scope creep (defines what's out of scope)
- Maintains consistency (coding standards, tech stack)
- Enables personas to make aligned decisions

### 2. Use Versioned Artifacts
Track iteration history:
```
artifacts/01-prd-v1.md
artifacts/01-prd-v2.md  (after architect review)
artifacts/02-tech-spec-v1.md
artifacts/02-tech-spec-v2.md  (after security concerns)
```

### 3. Iterate Within Phases
If QA finds critical issues, go back to implementation. Don't advance to documentation until quality gates pass.

### 4. Customize for Your Stack
The templates use generic examples. Adapt:
- Add your specific frameworks (React, Django, etc.)
- Include your team's coding standards
- Define your security requirements

### 5. Mix AI and Human Personas
Some personas can be real people:
- Product Owner: Your actual product manager
- Developer: AI-assisted
- QA Engineer: Mix of automated tests + AI review
- Technical Writer: AI-assisted

---

## Questions?

- **[Quick Start](../../QUICKSTART.md)** - 5-minute guide to get started
- **[Working Solo](../../docs/guides/working-solo.md)** - Using personas as a solo developer
- **[Working with Teams](../../docs/guides/working-with-teams.md)** - Team collaboration strategies
- **[Customizing Personas](../../docs/guides/customizing-personas.md)** - Adapt personas for your needs

---

**Ready to start?** → Pick a [constitution template](./templates/), then use your first [prompt](./prompts/)!
