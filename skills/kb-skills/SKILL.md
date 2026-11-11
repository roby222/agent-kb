---
name: kb-skills
description: >
  Manage a repo's project skills so Claude Code and Codex share one copy:
  list, create, move or delete skills in .agents/skills/ and keep
  .claude/skills/ linked to it. Use for "add a skill", "list project skills",
  "move this skill into the repo", "kb skills".
---

# kb-skills

Read `../kb/SKILL.md` first.

## Convention

- One source of truth: `.agents/skills/<name>/SKILL.md` (Codex reads it there).
- `.claude/skills` is a relative symlink to `../.agents/skills` so Claude Code reads the same files. If `.claude/skills` already holds real files, move them into `.agents/skills/` before linking.
- A skill is a procedure (steps to do a task). A fact goes in `.ai/`, not in a skill; a skill links to the `.ai/` file it relies on.
- Each skill is listed in `.ai/AGENTS.md` under `## Skills` with one line: what it does and when to use it.

## Actions

- **list**: show each skill's name and description, flag skills missing from the index, broken links, and duplicates between `.claude/skills/` and `.agents/skills/`.
- **create**: ask what task it automates and when it should trigger. Write `SKILL.md` with `name` and a `description` that says what and when (that is what triggers it), then a short body of steps. Add it to the index.
- **move**: bring a skill from `~/.claude/skills`, `~/.codex/skills` or `.claude/skills` into `.agents/skills/`, then fix the symlink and the index.
- **delete**: remove the folder and its index line, after the user confirms.

shortcut: the symlink does not work on Windows without developer mode; if a teammate is on Windows, copy instead and let `kb-review` flag drift.
