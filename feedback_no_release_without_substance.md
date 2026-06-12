---
name: feedback_no_release_without_substance
description: "Don't proactively suggest releasing or pushing trailing commits unless they carry substantive content"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 770d834b-2fad-44a7-b4ed-bdf05f98dced
---

Do not prompt David to release — or to `git push github main` to sync
trailing commits — when those commits are just docs, handoff snapshots,
or other non-substantive housekeeping.

**Why:** A release/push should carry real change. Nagging to ship a
handoff snapshot or a planning-docs commit is noise; David decides when
the accumulated content is worth shipping, and a bare "main is ahead of
remote" prod adds nothing. Also see [[feedback_no_transient_state_in_commit_msg]].

**How to apply:** After committing, just report what was committed. Only
mention pushing/releasing if the work itself is substantive and the user
would plausibly want it shipped now. Don't append "say the word to push"
to every commit. Releases go through `just release` in lockstep anyway.
