---
name: ddaanet marketplace location
description: Where the Claude Code marketplace manifest for ddaanet plugins lives
type: reference
originSessionId: 79dd51a2-5ebf-4ba8-b4b7-e636de62905d
---
The ddaanet Claude Code marketplace is at `/Users/david/code/claude-plugins/` locally, pushed to `ddaanet/claude-plugins` on GitHub. Manifest: `.claude-plugin/marketplace.json`.

It lists ddaanet plugins (`ddaa`, `ddaa-fr`, `edify`, `handoff`, `gitmoji`, `gitlore`, ...).

For a plugin living in a subdir of a multi-plugin repo, the source type must be `git-subdir` with `url` + `path` — NOT `source: "github"` with `path`. The `github` type silently ignores `path`, clones the whole repo, and Claude Code then loads skills from the repo-root `skills/` instead of the intended subdir. Correct shape:
```json
"source": { "source": "git-subdir", "url": "ddaanet/skills", "path": "plugins/ddaa" }
```

`/plugin update <name>@<mkt>` does NOT re-fetch when only the source type changes on the same version — the stale cache persists. Force a fresh pull with `/plugin uninstall` then `/plugin install`, then `/reload-plugins`.

When the user says "update the marketplace" from inside the skills repo, that's this sibling repo — not something in the current working directory.

Releasing a plugin is a TWO-repo operation. The manifest pins each plugin's `version` and a human-written `description` + `keywords` list (these do NOT auto-derive from the plugin.json in `ddaanet/skills`). After bumping a plugin version in `plugins/<p>/.claude-plugin/plugin.json` and pushing `ddaanet/skills`, you must also bump the matching `version` here and refresh its description/keywords, then push `ddaanet/claude-plugins`. Skipping this leaves users on stale metadata. Because the version changes, a normal `/plugin update <p>@ddaanet` re-fetches (the uninstall/reinstall dance is only for same-version source-type changes).

**As of 2026-06-10, `just release [patch|minor|major]` in the skills repo automates this two-repo dance** (bump both manifests in lockstep → tag → push → GitHub release → bump both marketplace `version` entries → push `claude-plugins`). It does NOT touch descriptions/keywords — refresh those by hand when skills change. Never hand-edit `.version` (a `version-guard` PreToolUse hook refuses it; the recipe is the only path). Documented in skills repo CLAUDE.md.
