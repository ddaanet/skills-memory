---
name: feedback_conventional_commit_type
description: Pick the correct Conventional Commit type for the change; the version/release type is only for actual releases
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 116f2b08-eafa-4f15-88ee-8681a439d222
---

Choose the **Conventional Commit type** that matches what the change *is*. The gitmoji emoji is just the rendered form — the commit-msg hook maps the type to an emoji (`feat:`→✨, `docs:`→📝, `fix:`→🐛, the version/release type→🔖). So this is a Conventional Commits rule, not a gitmoji rule: get the type right and the emoji follows.

David flagged a handoff-snapshot commit tagged as a release (🔖). A snapshot/notes file is `docs:` (📝). The release type (🔖) is reserved for an actual version bump (e.g. the `0.3.0` release commit) — nothing else.

**How to apply:** classify the change first — feature, fix, docs/notes, chore/tooling, or release — then write that type (or its emoji). When unsure, describe the file's role (a notes file is docs), not the surrounding event (a snapshot taken *after* a release is still docs, not a release).

Related: [[feedback_commit_language_english.md]] (these messages stay English), [[feedback_no_transient_state_in_commit_msg.md]].
