---
name: feedback_askuser_action_labels
description: "AskUserQuestion option labels in French first-person (\"Je fais X\") can be misread by the permission classifier as the user doing it"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b3b63d42-16e9-4e19-bc1a-7ca0a432b5ff
---

When offering an action the *assistant* will perform via AskUserQuestion,
a French first-person label like "Je déplace maintenant" was misread by the
Claude Code auto-mode permission classifier as the *user* committing to do
it — it then denied the follow-up tool call ("user indicated they would
handle the move themselves").

**Why:** The classifier reads option labels as intent signals and "Je" is
ambiguous about who acts.

**How to apply:** Phrase action labels so the actor is unambiguous — e.g.
"Claude déplace maintenant" / "Effectuer le déplacement" rather than "Je
déplace maintenant". If a legitimate, user-authorized action still gets
denied by the classifier, don't silently retry — explain the misread and
let the user re-authorize (they can switch to acceptEdits).
