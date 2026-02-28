# Changelog

All notable changes to the AI Workflow Orchestrator will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.0.0] - 2026-02-28

### Added
- `/new-workflow` command — guided 6-phase workflow creation flow (domain discovery, process mapping, persona definition, constitution drafting, memory & workflow design, generation)
- `.claude/agents/workflow-architect.md` — Workflow Architect agent for guided creation
- `scaffolding/claude-md-template.md` — production-derived CLAUDE.md for generated workflow repos (AI quick start, memory protocol, persona pipeline diagram, quality gates)
- `scaffolding/constitution-template.md` — production-derived with Kill List, 5-dimension scoring rubric, phase constraints, evolution rules
- `scaffolding/persona-template.md` — full persona structure with memory protocol, handoff, quality checklist, constitution enforcement
- `scaffolding/agent-template.md` — condensed Claude Code agent file format (role metadata, responsibilities, critical rules, handoff)
- `scaffolding/prompt-template.md` — copy-paste prompt structure (context, rules, inputs, instructions, output format, handoff)
- `scaffolding/project-learnings-template.md` — cross-project intelligence file (patterns, anti-patterns, constitution updates log)
- `scaffolding/memory-templates/context-template.md` — upgraded volatile memory template (~500 tokens, handoff-focused)
- `scaffolding/memory-templates/memory-template.md` — upgraded persistent history template (append-only, Human Edits Log with pattern detection)
- `scaffolding/workflow-templates/full-workflow.md` — all personas, highest quality, upgrade/downgrade paths
- `scaffolding/workflow-templates/quick-workflow.md` — fewer personas, faster cycle, comparison table
- `scaffolding/workflow-templates/simple-workflow.md` — minimal personas, fastest cycle, Full vs Quick vs Simple comparison
- `docs/concepts/what-is-constitutional-ai.md` — beginner education on constitutional governance
- `docs/concepts/why-personas-not-prompts.md` — beginner education on single-responsibility AI roles
- `docs/concepts/the-adaptive-cycle.md` — beginner education on r→K→Ω→α workflow phases
- `docs/plans/2026-02-28-workflow-wizard-design.md` — design document for v2.0.0 transformation

### Changed
- **BREAKING:** `domains/` renamed to `examples/` — existing domains are now reference examples, not the product
- **BREAKING:** `templates/` renamed to `scaffolding/` — contains generation templates used by /new-workflow
- `.claude/CLAUDE.md` rewritten as Workflow Wizard operating instructions (two modes: creation and browsing)
- `README.md` rewritten for scaffolding tool with three user paths (create, learn, browse examples)
- `QUICKSTART.md` rewritten for scaffolding-first approach (Claude Code wizard + manual fallback)
- `examples/README.md` reframed as reference examples with study guidance
- Root `guides/` merged into `docs/guides/`

### Removed
- `QUICK-START.md` — duplicate, merged into QUICKSTART.md
- `WORKFLOW-ARCHITECT.md` — superseded by CLAUDE.md creation mode
- `README-ORIGINAL.md` — no longer needed
- Domain-specific agents (`sw-product-owner.md`, `sw-solutions-architect.md`, `sw-specialist-developer.md`, `sw-qa-engineer.md`, `sw-technical-writer.md`, `cw-content-strategist.md`, `cw-content-writer.md`, `cw-editor.md`, `cw-fact-checker.md`, `cw-seo-specialist.md`) — replaced by single `workflow-architect.md` agent
- `scaffolding/agents/agent-template.yaml` — replaced with production-derived markdown template
- `scaffolding/workflows/workflow-template.yaml` — replaced with three workflow variant templates
- `scaffolding/memory/` — old templates replaced with upgraded versions in `scaffolding/memory-templates/`

---

## [1.0.0] - 2025-12-04

### Added
- Initial release of AI Workflow Orchestrator
- Software Development domain with 5 personas, 16 prompts, 3 constitution templates
- Content Writing domain with 5 personas, 12 prompts, 3 constitution templates
- Cross-domain guides (choosing domain, working solo, working with teams, customising personas)
- CONTRIBUTING.md with quality standards
