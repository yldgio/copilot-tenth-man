# Copilot Instructions — copilot-tenth-man

This repository is a **GitHub Copilot CLI plugin**. All logic is expressed in Markdown — no build system, no compiled code.

## Source of truth

**[AGENTS.md](../AGENTS.md)** is the canonical reference for every agent in this repo: behavior, structure, persona, and maintenance rules.

Read it before making any change. Update it as part of every change.

## Quick reference

| Task | Command |
|------|---------|
| Install locally | `copilot plugin install .` |
| Pick up changes | `copilot plugin install .` (reinstall to bust cache) |
| Install from GitHub | `copilot plugin install yldgio/copilot-tenth-man` |

## Key rule

Whenever you change an agent file, `plugin.json`, or `README.md` — update `AGENTS.md` in the same commit. See the **Maintenance rules** section in `AGENTS.md` for the full checklist.
