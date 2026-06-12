---
name: feedback_commit_language_english
description: Commit messages in English by default; French only in French-only projects
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 116f2b08-eafa-4f15-88ee-8681a439d222
---

Write commit messages in **English** by default. Use French only in French-only projects (e.g. `candidature`).

**Why:** The `skills` repo is bilingual (ships EN `ddaa` + FR `ddaa-fr` skills), but that does NOT make French the commit language — David specified English commits here. "Bilingual content" ≠ "French commits." Don't infer commit language from the presence of French skills.

**How to apply:** Default commit subjects/bodies to English. Reserve French for repos whose whole purpose is French (project content + audience French throughout). Keep gitmoji + "why not what" density either way. If unsure, English. Don't switch languages mid-session — see [[feedback_no_transient_state_in_commit_msg.md]] for the broader "commit messages stay consistent and substantive" principle.
