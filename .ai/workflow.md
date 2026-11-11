# Workflow

## Layout

- `skills/<name>/SKILL.md`: the plugin's skills, shared by both tools. Skills reference each other with relative paths (`../kb/SKILL.md`).
- Claude Code: `.claude-plugin/plugin.json` (plugin) and `.claude-plugin/marketplace.json` (so the repo installs as a marketplace). Skills are picked up from `skills/` by default.
- Codex: `.codex-plugin/plugin.json` (`"skills": "./skills/"`) and `.agents/plugins/marketplace.json` (points at the GitHub URL).

## Versioning

- `version` lives in both `plugin.json` files; bump them together. Tags are `vX.Y.Z`.

## Testing locally

- Claude Code: `claude --plugin-dir ~/src/agent-kb`, then run `/kb:kb-review` in a repo that has `.ai/` (e.g. `~/src/rush`).
- Codex: `codex plugin marketplace add roby222/agent-kb` then `codex plugin add kb@agent-kb` (verified with codex-cli 0.164); it installs from GitHub `main`, so push before testing. On this Mac the binary is `~/.codex/plugins/.plugin-appserver/codex-cli/bin/codex` (not in PATH).

## Git

- Work lands on `main`, pushed to `github.com/roby222/agent-kb`.
