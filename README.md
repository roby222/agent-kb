# agent-kb

A plugin for Claude Code and Codex that keeps a repo's agent knowledge in one place: `.ai/`, one subject per file, indexed by `.ai/AGENTS.md`, read by the agent before any change.

| Skill | What it does |
|---|---|
| `kb` | The pattern and its rules; triggers when the agent records a durable fact |
| `kb-init` | Sets up `.ai/` in a repo, migrating existing `CLAUDE.md`, `.cursorrules`, ... |
| `kb-skills` | Project skills in `.agents/skills/`, shared with Claude via a symlink |
| `kb-review` | Read-only report: stale, duplicate, unindexed, secrets |
| `kb-clean` | Applies the fixes and rebuilds the index |

## Install

Claude Code:

```
/plugin marketplace add roby222/agent-kb
/plugin install kb@agent-kb
```

Then `/kb:kb-init`, `/kb:kb-review`, `/kb:kb-clean`, `/kb:kb-skills`.

Codex: add the marketplace from `https://github.com/roby222/agent-kb.git` and install `kb`; call the skills as `$kb-init`, `$kb-review`, ...

## Status

0.1.0, scaffolding. Skills are first drafts.
