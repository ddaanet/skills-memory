---
name: handoff — two distinct things
description: The ddaanet/handoff github repo is a separate Stop-hook tool, not to be confused with the handoff skill inside this repo
type: project
originSessionId: 79dd51a2-5ebf-4ba8-b4b7-e636de62905d
---
"Handoff" refers to two different things in ddaanet-land:

1. **`ddaanet/handoff`** — a separate GitHub repo and Claude Code plugin (shipped via the ddaanet marketplace). A Stop-hook tool that composes a task snapshot with auto-extracted last-N user prompts and files touched from the session JSONL. Largely subsumed by Claude Code's automemory.

2. **`skills/handoff/`** inside `ddaanet/skills`** (plus its French mirror `skills/passation/`)** — a session-wrap-up skill shipped as a claude.ai `.skill` only (not in any Claude Code plugin). Retained because automemory doesn't apply to plain claude.ai, and because the user uses it with Notion integration.

**Why:** the name collision is deliberate-ish (same concept, different surfaces) but confuses anyone reading either project in isolation.

**How to apply:** when the user says "handoff", disambiguate by context — Claude Code plugin work → the separate repo; claude.ai / Notion / session-summary → the skill in this repo.
