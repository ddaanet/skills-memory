---
name: feedback_no_transient_state_in_commit_msg
description: "Don't put transient repo state (e.g. \"unpushed\", \"ahead of remote\") in commit messages"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 116f2b08-eafa-4f15-88ee-8681a439d222
---

Never describe transient repo state in a commit message — e.g. "docs commit unpushed", "main ahead of remote", "WIP, will fix later". David called this out as silly: the statement is false the moment the state changes (a push, a later commit), but it's frozen in history forever.

**Why:** A commit message documents *what the change is*, not the working-tree/sync situation at authoring time. Sync state belongs in the conversation or a handoff snapshot, not the permanent record.

**How to apply:** Describe the change itself ("🔖 handoff snapshot après release v0.3.0"), not where it sits relative to the remote. Put "still unpushed / main ahead by N" in chat or [[feedback_todowrite_renamed]]-style ephemeral notes instead.
