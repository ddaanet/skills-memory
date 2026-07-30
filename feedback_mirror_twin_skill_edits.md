---
name: feedback_mirror_twin_skill_edits
description: "Editing one language twin of a skill pair means editing both — a brief naming only one file is underspecified, not a scope limit"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 9c3ef3da-204d-438f-8042-fc8144205db7
  modified: 2026-07-30T11:55:14.869Z
---

The bilingual pairs in this repo (`proof`/`relecture`, `preflight`/`preflight`,
`brief`/`brief`, `bookkeeping`/`saisie-comptable`, `handoff`/`passation`) move
together. Any edit to one twin lands in the other in the same commit series.
When a brief or a request names only one language's file, read that as
underspecification, not as a deliberate scope limit — mirror it and say so.

**Why:** twins that drift stop being the same skill, and the drift stays
invisible until someone greps for the stale sentence. David confirmed the rule
twice in one session (2026-07-30): he kept an unrequested FR extension of a
brief that named only the EN file, then asked for the one remaining gap to be
closed rather than merely reported.

**How to apply:** after editing one twin, grep the sibling for the same passage
and rewrite it natively in the target language — never translate, per
`ddaa:bilingual-skill-creator` Phase 2. Then verify with the Phase 3 check:
compare `grep '^#'` output of both `SKILL.md` files and of each reference file,
expecting equal count and order. Beware that `grep '^#'` also counts shell
comments inside fenced code blocks, which shows up as a phantom mismatch.
Parity extends to those comments too. Related: [[feedback_commit_language_english]].
