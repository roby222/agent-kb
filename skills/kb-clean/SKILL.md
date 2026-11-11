---
name: kb-clean
description: >
  Tidy the .ai/ knowledge base: fix stale facts, merge duplicates, split
  overgrown files, rebuild the index, remove secrets and noise. Use for
  "knowledge base clean", "kb clean", "clean up .ai/", or after kb-review.
---

# kb-clean

Read `../kb/SKILL.md` first.

## Steps

1. **Findings.** Use the latest `kb-review` report from this conversation; if there is none, run its checks (`../kb-review/SKILL.md`) first.
2. **Plan.** Show the user the list of edits grouped by file. Deletions of facts and anything you are unsure is stale need an explicit yes.
3. **Apply**, in this order:
   - remove secrets and private data (tell the user to rotate any real key you found);
   - fix stale facts against the code; if you cannot tell what is true now, leave `TODO(kb): <question>`;
   - merge duplicates into the file the index says owns the subject, replacing the other copy with a link;
   - split files covering two subjects, cut task logs and filler;
   - rebuild `.ai/AGENTS.md`: one line per file with when to read it, skills section in sync.
4. **Verify**: every path and command you kept still exists; every `.ai/` file is in the index.
5. **Report** what changed per file and the `TODO(kb):` left open. Do not commit unless the user asks.
