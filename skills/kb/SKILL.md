---
name: kb
description: >
  The agent knowledge base pattern: a repo's durable facts for agents live in
  .ai/, one subject per file, indexed by .ai/AGENTS.md. Use whenever you learn
  something durable about a project (a command, an invariant, a decision, a
  gotcha) and need to record it, whenever you edit AGENTS.md, CLAUDE.md or
  anything in .ai/, and when the user asks how the knowledge base works.
---

# The .ai/ knowledge base

## Layout

```
AGENTS.md          # 3-6 lines: what the project is, then "Agent knowledge lives in .ai/: start there before any change."
CLAUDE.md          # optional, only "@AGENTS.md", for tools that do not read AGENTS.md
README.md          # for humans; agents do not depend on it
.ai/
  AGENTS.md        # the index: one line per file saying what it holds and WHEN to read it, then house rules
  product.md       # who uses it, what it promises, principles
  architecture.md  # data flow, layers, invariants, external API facts
  workflow.md      # build, test, run, git, releases, tickets
  design.md        # visual system (only if there is a UI)
  ...              # one file per subject; name files by subject, not by date
.agents/skills/    # project skills, shared by Codex and Claude (see kb-skills)
```

The subject files above are typical, not required: create only the ones the project needs.

## Rules

1. **One fact, one file.** Before adding a fact, grep `.ai/` for it. If it exists, edit it there; elsewhere, link to it (`see architecture.md, Storage`).
2. **Record in the same change.** When you learn something durable, add it to the matching file in the same commit as the code it explains.
3. **Durable only.** No task logs, no "today I did", no copies of what code, git history or `--help` already say. Write what an agent cannot cheaply rediscover: why, invariants, gotchas, the command that actually works.
4. **The index says when.** Every file in `.ai/` has one line in `.ai/AGENTS.md` that tells the agent which tasks require reading it. A file not in the index does not exist for the agent.
5. **Short and imperative.** Bullets, concrete paths and commands, no filler. A file past ~150 lines is a sign it holds two subjects: split it.
6. **Point, do not paste.** Reference code as `path/to/file` instead of copying it; copies go stale.
7. **Private stays out.** No secrets, keys, personal addresses or customer data. Say where they live (`local.properties`, never committed) instead.

## Commands

- `kb-init`: create the pattern in a repo, migrating what already exists.
- `kb-skills`: create, list or move project skills.
- `kb-review`: read-only health report of the knowledge base.
- `kb-clean`: apply fixes so the knowledge base stays tidy.
