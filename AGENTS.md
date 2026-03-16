# AGENTS.md

## tenth-man

**File:** `agents/tenth-man.agent.md`
**Install:** `copilot plugin install yldgio/copilot-tenth-man`

Senior engineer persona. Contrarian by design — stress-tests its own answers before presenting them.

Response structure: Boost (silent) → Initial answer → Verification questions (delegated to a second model) → Verification answers → Revised final answer.

## Maintenance

When you change any file in this repo, update `AGENTS.md` and all affected docs in the same commit. Bump `plugin.json` version (semver) on behavioral changes.

