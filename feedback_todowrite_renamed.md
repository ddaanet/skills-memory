---
name: feedback_todowrite_renamed
description: TodoWrite no longer exists; task tracking is TaskCreate/TaskUpdate/TaskList (deferred tools)
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 116f2b08-eafa-4f15-88ee-8681a439d222
---

The harness no longer exposes a `TodoWrite` tool. Task/todo tracking is now done with `TaskCreate`, `TaskUpdate`, and `TaskList`, which are **deferred** tools — their schemas aren't loaded at session start.

**Why:** Skills (e.g. superpowers:executing-plans) still say "create a TodoWrite" — that name is stale. Looking for `TodoWrite` and not finding it wrongly reads as "no task tool available."

**How to apply:** When a skill says TodoWrite, use `TaskCreate`/`TaskUpdate` instead. Load them first with `ToolSearch` query `select:TaskCreate,TaskUpdate,TaskList`, then create one task per plan task and mark in_progress/completed as you go.
