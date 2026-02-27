# Project: AI Workflow Orchestrator

## Project Context

**Type:** Domain-agnostic AI workflow framework
**Purpose:** Provide constitutional governance patterns, personas, prompts, and templates for structured AI collaboration across any domain
**Active Domains:** Software Development, Content Writing

## Key Concepts

- **Constitutions**: Non-negotiable project rules — templates per domain in `domains/[domain]/templates/`
- **Personas**: Role-based prompt files in `domains/[domain]/personas/`
- **Phases**: Planning → Implementation → Review → Documentation (adapted per domain)
- **Prompts**: Copy-paste prompts in `domains/[domain]/prompts/`

## Key Files

- `README.md` — Main overview and quickstart
- `QUICKSTART.md` — 5-minute getting started guide
- `domains/README.md` — Domain selection guide
- `CONTRIBUTING.md` — How to add domains, personas, prompts

## Project Learnings

@.claude/learnings/learnings.md
@.claude/learnings/decisions.md

## Working Agreements

1. Domain templates should be self-documenting with verbose placeholders
2. Keep personas focused on their specific role
3. Framework is tool-agnostic — no Claude Code-specific features in domain content
4. Use `/reflect` at end of sessions to capture learnings
5. Update `CHANGELOG.md` when making notable changes — use Keep a Changelog format, bump the version (semver), and date entries as `YYYY-MM-DD`
