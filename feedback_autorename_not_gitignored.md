---
name: autorename-not-gitignored
description: .claude/autorename must not be gitignored in this repo — its presence is a hook defect signal
metadata: 
  node_type: memory
  type: feedback
  originSessionId: ba9ccd46-003c-423f-81a3-ea0c2163f195
---

Do not add `.claude/autorename` to `.gitignore` in this repo.

**Why:** The file is written by the handoff skill and deleted by a post-handoff hook. If it appears as an untracked file, that means the hook did not run — it is a signal of a defect, not a file to suppress.

**How to apply:** When preflight or git status shows `.claude/autorename` as untracked, investigate the hook rather than gitignoring the file. Delete it manually once the cause is understood.
