---
name: feedback_git_status_sandbox_retry
description: "When the git-status sandbox hook says retry unsandboxed, re-run the exact same command with dangerouslyDisableSandbox — don't improvise around it"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b3b63d42-16e9-4e19-bc1a-7ca0a432b5ff
---

`git status` trips the command sandbox: the hook blocks the whole compound
command and says "Re-run the exact same Bash command with
dangerouslyDisableSandbox set to true." Do exactly that — re-run the identical
command unsandboxed. Do **not** improvise (e.g. drop the `git status` and run a
trimmed command, then check state separately).

**Why:** When I improvised instead of following the retry directive, it worked
but relied on an unverified assumption that the block aborted the whole command
(so nothing committed). The verbatim retry needs no such assumption — it runs
add+commit+status in one accurate step. David flagged the deviation directly.

**How to apply:** Two rules. (1) Any command containing `git status` should run
with `dangerouslyDisableSandbox: true` from the outset — `git status` misreports
under the sandbox (phantom mounted-artifact entries). The problem is the sandbox,
NOT the compound `&&` chaining; chaining `git status` after add/commit is fine as
long as the whole command runs unsandboxed. (2) When a hook gives an explicit
recovery instruction, follow it literally rather than substituting your own plan.
