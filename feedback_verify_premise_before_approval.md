---
name: feedback-verify-premise-before-approval
description: "Check a claim isn't already settled by construction before proposing work to test it; put the premise in the approval question, not just the scope"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 0d3c121b-6e30-4edb-9c7d-fbc59ae76e8c
  modified: 2026-07-30T20:00:15.085Z
---

Before proposing empirical work, ask whether the claim is deductively
closed. If the result can only come out one way, there is nothing to run.
And when asking for approval, expose the premise — offering only
size/scope options makes the approval hollow, because every option
presupposes the work is worth doing.

**Why:** 2026-07-30 I burned six subagent sessions "testing" whether
removing the bottom-to-top edit-ordering hint from `proof`/`relecture`
broke batch-apply. `Edit` takes `old_string`/`new_string` — line numbers
are not an input, so ordering cannot affect it. The commit message I had
already read stated exactly that; I called it "an argument, not evidence"
and went hunting for evidence. David's verdict: a waste, and the lesson
is not approving something without making sure it makes sense.

**How to apply:** when a task is "prove X still works after removing Y",
first check whether Y ever had a mechanism. Read the tool contract, not
just the prose. A tell that I am rationalising: reasoning about how to
make a null result *visible* (model choice, harder fixtures) instead of
asking whether it could be non-null. In AskUserQuestion, make one option
"this does not need testing, here is why" whenever that is live. See
[[feedback-no-release-without-substance]] — same family: don't generate
motion that looks like rigour.
