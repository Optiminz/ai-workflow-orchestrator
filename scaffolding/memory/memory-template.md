---
project: "[PROJECT-NAME]"
type: "memory"
created: "[YYYY-MM-DDTHH:MM:SSZ]"
last_updated: "[YYYY-MM-DDTHH:MM:SSZ]"
---

# Project Memory Log

**Purpose:** Persistent, append-only log of all project events, decisions, and artifacts.

## [YYYY-MM-DD HH:MM] - Agent Name (Step X, Phase)
- Key decision made
- Artifact created: `[PROJECT#]-[AGENT#]-[artifact-name]-v[N].md`
- Human feedback: "..."
- Notes: ...

## [YYYY-MM-DD HH:MM] - Phase Transition: [phase] → [phase]
- Action taken: ...
- What changed: ...
- Context summary: ...

## [YYYY-MM-DD HH:MM] - Human Checkpoint
- Agent: [agent-name]
- Decision: [APPROVED|REJECTED|ITERATE]
- Feedback: "..."

---

## Guidelines for Memory Log

### What to Log
- Every agent execution
- All artifact creation (with version numbers)
- Key decisions and their rationale
- Human feedback and approvals
- Phase transitions
- Iteration history

### Format
```
## [Timestamp] - Event Type
- Detail 1
- Detail 2
- **Created:** artifact-filename.md (if applicable)
- **Human feedback:** "..." (if applicable)
```

### Rules
- **Append-only** - Never delete or modify past entries
- **Chronological** - Always add to the end
- **Timestamped** - Use ISO 8601 format (YYYY-MM-DD HH:MM)
- **Artifact tracking** - Always note created files with version

---

*Append-only log. Never delete entries.*
*Last updated: [YYYY-MM-DD HH:MM]*
