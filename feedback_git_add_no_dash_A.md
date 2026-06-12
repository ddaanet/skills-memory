---
name: sandbox dotfiles in this repo
description: Char-device dotfiles (.bash_profile, .zshrc, etc.) are sandbox artifacts — gitignored, not a real repo concern
type: feedback
originSessionId: 79dd51a2-5ebf-4ba8-b4b7-e636de62905d
---
In sandboxed Claude Code sessions, `/Users/david/code/skills` shows host dotfiles (`.bash_profile`, `.bashrc`, `.zshrc`, `.gitconfig`, `.idea`, `.mcp.json`, `.profile`, `.ripgreprc`, `.vscode`, `.zprofile`) mounted into the working tree as character devices. They appear in `git status` and used to break `git add -A` with "can only add regular files".

**Why:** they're a sandbox mount artifact; outside the sandbox they don't exist. The user's rule is: gitignore everything sandbox-mounted except `.claude/` and `.gitmodules` (git submodule manifest). This was done on 2026-04-24 in commit 8756bdd.

**How to apply:** in a future sandboxed session, if new host-mounted char-device files appear (user adds a new dotfile), extend the "Sandbox artifacts" block in `.gitignore` to cover it. Do NOT gitignore `.claude/` or `.gitmodules`. With the current gitignore, `git add -A` is safe to use again, but staging by explicit path is still a reasonable default.
