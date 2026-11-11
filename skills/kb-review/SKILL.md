---
name: kb-review
description: >
  Read-only health check of the .ai/ knowledge base: stale facts, duplicates,
  contradictions, files missing from the index, bloat, secrets, skills out of
  sync. Produces a ranked report and changes nothing. Use for "knowledge base
  review", "kb review", "is our .ai/ up to date", before a release or after a
  big refactor.
---

# kb-review

Read `../kb/SKILL.md` first: every check below is a rule from there.

## Checks

1. **Stale**: every path, command, class, flag or env var named in `.ai/` still exists (grep the tree, check `package.json`/build files for commands). Facts contradicted by the code.
2. **Duplicates**: the same fact in two files, or copied from README or code.
3. **Contradictions**: two files that disagree.
4. **Index**: files in `.ai/` not in `.ai/AGENTS.md`, index lines pointing at missing files, index lines that do not say when to read the file.
5. **Bloat**: files past ~150 lines or covering two subjects; task logs, dated diaries, filler.
6. **Gaps**: recent commits (`git log --since=60.days --stat`) that changed behavior with no matching `.ai/` update; areas of the code no file covers.
7. **Secrets and private data**: keys, tokens, real addresses, customer names.
8. **Skills**: run the `list` check from `../kb-skills/SKILL.md`.
9. **Root**: root `AGENTS.md` is short and points to `.ai/`; other agent files (`CLAUDE.md`, `.cursorrules`, ...) do not carry their own facts.

## Report

Start with one line: files reviewed and overall state. Then findings grouped **Must fix** (wrong or secret), **Should fix** (duplicate, stale, unindexed), **Nice to have**. Each: `file:line`, the problem in one sentence, the proposed fix. End with "Run `kb-clean` to apply." Change no files.
