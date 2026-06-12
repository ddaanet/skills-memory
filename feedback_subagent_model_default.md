---
name: subagent-model-default
description: "Which model to default to when spawning subagents (Explore, claude-code-guide, etc.)"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 456a205a-13cf-4826-975e-674284fb7b1f
---

Default subagents to haiku. Override to sonnet/opus only when the task genuinely needs stronger reasoning (judgment, catching subtle errors), not reflexively.

**Why:** The built-in `Explore` and `claude-code-guide` agents both default to haiku (confirmed via `/agents`). Haiku is sufficient for focused local-file summarization and doc lookups — in this session a default-haiku claude-code-guide call correctly caught another agent's hallucinated settings field, so haiku is not too weak for verification either. The user explicitly pushed back when I defaulted to opus, then again when I over-corrected to sonnet.

**How to apply:** When calling the Agent tool, omit the `model` param (inherits the agent's haiku default) unless I can name a concrete reason this specific task needs more. Don't claim "sonnet was needed" without evidence — verify what actually happened first.
