---
name: feedback_claude_dir_tracked
description: "In the skills repo, .claude/ is tracked tooling — commit settings.json and handoff-task.md, only handoff-session is ignored"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b3b63d42-16e9-4e19-bc1a-7ca0a432b5ff
---

In `/Users/david/code/skills`, `.claude/` is **tracked tooling**, not session
cruft — the `.gitignore` says so explicitly. When committing, stage these:

- `.claude/settings.json` — `enabledPlugins` declaration, versioned project config.
- `.claude/handoff-task.md` — the pre-clear passation snapshot ("gitlore"), versioned; the handoff hook reads it next session.
- `.claude/settings.local.json` — already tracked.

Only `.claude/handoff-session` is gitignored: it holds the current session's
`.jsonl` transcript path, which is session-specific.

**Why:** I twice wrongly excluded `.claude/` files from a commit as "session
artifacts"; David corrected both (settings.json, then handoff-task.md).

**How to apply:** Don't treat `.claude/` as throwaway in this repo. Default to
staging its tooling files; the only transient one is `handoff-session`. See
[[feedback_askuser_action_labels]] for the other workflow correction this session.
