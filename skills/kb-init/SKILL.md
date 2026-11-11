---
name: kb-init
description: >
  Set up the .ai/ agent knowledge base in the current repo: root AGENTS.md
  pointer, .ai/AGENTS.md index and one file per subject, migrating existing
  CLAUDE.md, AGENTS.md, .cursorrules and similar agent docs. Use for
  "knowledge init", "kb init", "set up the knowledge base", "create .ai/".
---

# kb-init

Read `../kb/SKILL.md` first: it defines the layout and rules you are creating.

## Steps

1. **Inventory.** List what already exists: `AGENTS.md`, `CLAUDE.md`, `.ai/`, `.cursorrules`, `.cursor/rules/`, `.github/copilot-instructions.md`, `.windsurfrules`, `docs/`, the README's contributor parts, `.claude/skills/`, `.agents/skills/`. If `.ai/AGENTS.md` already exists, stop and suggest `kb-review` instead.
2. **Scan the repo.** Build files, entry points, test command, CI config, directory layout. Note facts an agent would need and could not cheaply rediscover.
3. **Propose a plan** to the user before writing: which subject files, what goes in each (one line per file), which existing content moves where, what gets dropped as duplicate or stale. Ask only what the code cannot answer (who the users are, product principles, house rules).
4. **Write** `.ai/AGENTS.md` (index + house rules), the subject files, and a short root `AGENTS.md` that points to `.ai/`. Move content, do not copy it: each fact ends up in exactly one place.
5. **Old files.** Replace migrated agent files with a one-line pointer to `AGENTS.md`, or delete them if the user agrees. If `CLAUDE.md` exists, reduce it to `@AGENTS.md`.
6. **Skills.** If project skills exist, hand off to `kb-skills` to put them in `.agents/skills/`.
7. **Report** the files created, what moved where, and the open questions you left as `TODO(kb):` in the files.

Do not commit unless the user asks.
