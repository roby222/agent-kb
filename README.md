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

Codex:

```
codex plugin marketplace add roby222/agent-kb
codex plugin add kb@agent-kb
```

Start a new Codex session, then call `$kb-init`, `$kb-review`, `$kb-clean`, `$kb-skills`.

Update later with `/plugin marketplace update agent-kb` (Claude) or by re-running `codex plugin add kb@agent-kb` (Codex).

## The pattern

```
AGENTS.md          # what the project is + "start in .ai/"
.ai/AGENTS.md      # index: each file, and when to read it; house rules
.ai/<subject>.md   # product, architecture, workflow, design, ...
.agents/skills/    # project skills (.claude/skills links here)
```

One fact lives in one file; the agent records what it learns in the same change as the code. Full rules: [skills/kb/SKILL.md](skills/kb/SKILL.md).

## Status

0.1.0, early: the skills are first drafts. Issues and PRs welcome.
