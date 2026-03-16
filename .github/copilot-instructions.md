# Copilot Instructions — copilot-tenth-man

This repository is a **GitHub Copilot CLI plugin**. It contains no build system, no tests, and no compiled code. All logic is expressed in Markdown.

## Plugin structure

```
plugin.json              ← manifest (name, version, agent directory)
agents/
  tenth-man.agent.md     ← the agent definition (YAML frontmatter + prompt)
```

The plugin is installed locally with:
```bash
copilot plugin install .
```

After any change to `agents/tenth-man.agent.md`, reinstall to pick up the cache:
```bash
copilot plugin install .
```

## Agent file format

`agents/tenth-man.agent.md` is a Markdown file with YAML frontmatter:

```markdown
---
name: Tenth Man
description: ...
tools: ["*"]
disable-model-invocation: false
---

Prompt body here...
```

Key frontmatter fields:
- `tools`: `["*"]` means all tools available. Restrict with explicit names if needed.
- `disable-model-invocation: false` — the agent can be auto-selected by the model.
- `name` — display name shown in `/agent` picker.

## Conventions

- **The prompt is the product.** Changes to `agents/tenth-man.agent.md` are the main work of this repo.
- The four-step response structure (Initial → Verification questions → Verification answers → Revised answer) is the core behavior. Do not remove or flatten it.
- Step 0 (prompt boosting) is silent unless intent materially changes — keep it that way.
- The agent uses a multi-model review pattern in Step 2: it delegates to a separate agent/model to generate verification questions. Preserve this — it's intentional.
- `plugin.json` version should be bumped (semver) when the agent behavior changes meaningfully.

## Distribution

Published at: https://github.com/yldgio/copilot-tenth-man

Install command for end users:
```bash
copilot plugin install yldgio/copilot-tenth-man
```
