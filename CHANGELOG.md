# Changelog

All notable changes to the AI Workflow Orchestrator will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Removed
- Examples directories removed — promised complete worked examples that weren't implemented, creating false expectations
- `scaffolding/agents/agent-template.yaml` — replaced with production-derived markdown templates
- `scaffolding/workflows/workflow-template.yaml` — replaced with three workflow variant templates
- `scaffolding/memory/` — old memory templates replaced with upgraded versions in `scaffolding/memory-templates/`

### Added
- `.claude/` project setup with CLAUDE.md, learnings system, and Claude Code agents for all personas
- `CHANGELOG.md` for tracking changes
- `scaffolding/claude-md-template.md` — production-derived CLAUDE.md for generated workflow repos (AI quick start, memory protocol, persona pipeline diagram, quality gates)
- `scaffolding/constitution-template.md` — production-derived with Kill List, 5-dimension scoring rubric, phase constraints, evolution rules
- `scaffolding/persona-template.md` — full persona structure with memory protocol, handoff, quality checklist, constitution enforcement
- `scaffolding/agent-template.md` — condensed Claude Code agent file format (role metadata, responsibilities, critical rules, handoff)
- `scaffolding/prompt-template.md` — copy-paste prompt structure (context, rules, inputs, instructions, output format, handoff)
- `scaffolding/project-learnings-template.md` — cross-project intelligence file (patterns, anti-patterns, constitution updates log)
- `scaffolding/memory-templates/context-template.md` — upgraded volatile memory template (~500 tokens, handoff-focused)
- `scaffolding/memory-templates/memory-template.md` — upgraded persistent history template (append-only, Human Edits Log with pattern detection)
- `scaffolding/workflow-templates/full-workflow.md` — all personas, highest quality, upgrade/downgrade paths
- `scaffolding/workflow-templates/quick-workflow.md` — Researcher skipped, faster cycle, comparison table
- `scaffolding/workflow-templates/simple-workflow.md` — minimal personas, fastest cycle, Full vs Quick vs Simple comparison

### Changed
- Constitution templates updated with verbose placeholder names (`[PLACEHOLDER_NAME — e.g., ...]` format)
- Verbose naming convention rule added to all software-development constitution templates
- README.md restructured to lead with quickstart and domain selection
- Domain READMEs updated to remove false claims about examples

---

## [1.0.0] - 2025-12-04

### Added
- Initial release of AI Workflow Orchestrator
- Software Development domain with 5 personas, 16 prompts, 3 constitution templates
- Content Writing domain with 5 personas, 12 prompts, 3 constitution templates
- Cross-domain guides (choosing domain, working solo, working with teams, customising personas)
- CONTRIBUTING.md with quality standards
