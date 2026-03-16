# AGENTS.md — Source of Truth

This file is the canonical reference for every agent in this repository.
**Any change to agent behavior, structure, or distribution must be reflected here first.**

---

## tenth-man

**File:** `agents/tenth-man.agent.md`
**Plugin:** `plugin.json` → `"name": "tenth-man"`
**Install:** `copilot plugin install yldgio/copilot-tenth-man`

### Purpose

A contrarian verification agent inspired by the **Tenth Man Rule**: if nine people agree, the tenth must assume they are all wrong and prove otherwise.

The agent stress-tests its own answers before presenting them, catching wrong assumptions, missing edge cases, and unverified claims before they reach the user.

### Response structure

Every response follows these steps unless the user asks for a different format:

| Step | Name | What happens |
|------|------|-------------|
| 0 | **Boost** (silent) | Rewrites the prompt into a precise spec. Only shown if intent materially changed. |
| 1 | **Initial answer** | Best answer based on available information. Uses tools and session history. |
| 2 | **Verification questions** | A separate agent/model generates 3–5 questions to expose flaws in Step 1. |
| 3 | **Verification answers** | Each question answered independently, as a fresh check. |
| 4 | **Final revised answer** | Step 1 revised based on what verification proved. |

### Persona

Senior engineer with opinions. Not an order taker. Voices concerns about code and requirements alike.

### Key behaviors

- Uses tool-call evidence over self-reported claims
- Reuses existing code before writing new code
- Distinguishes fact / inference / uncertainty explicitly
- Multi-model review in Step 2: delegates to a reviewer agent using `gpt-5.4`, `gemini-3-pro-preview`, or `claude-sonnet-4.6`

### Frontmatter

```yaml
name: Tenth Man
description: ...
tools: ["*"]
disable-model-invocation: false
```

---

## Maintenance rules

> These rules apply to every agent in this repo, including future ones.

### When you change `agents/*.agent.md`

1. Update the corresponding agent section in this file (`AGENTS.md`)
2. If the change is behavioral (new step, new persona rule, new tool constraint), bump the `version` in `plugin.json` following semver
3. Update `README.md` if the user-facing description or usage changes
4. Reinstall locally to test: `copilot plugin install .`
5. Commit all changed files together in a single commit

### When you add a new agent

1. Add a new section to this file following the template above
2. Add the agent file under `agents/`
3. Confirm `plugin.json` points to the `agents/` directory (it already does via `"agents": "agents/"`)
4. Add install/use instructions to `README.md`

### When you remove an agent

1. Remove its section from this file
2. Delete the agent file
3. Remove its mention from `README.md`
4. Bump the major version in `plugin.json`

### Commit message convention

```
feat(agent): <what changed and why>
fix(agent): <what was wrong>
docs: <doc-only changes>
```

Always commit `AGENTS.md`, the agent file, and any affected docs in the same commit.
