# Policy Schema (MVP)

## Location
- .agentguard/policy.yml (committed)
- .agentguard/policy.local.yml (optional local override)

## Precedence
BLOCK > REQUIRE_APPROVAL > WARN > ALLOW

## Key Sections
- defaults (mode, FULL_TEMP TTL)
- sensitive_paths (block, require_approval)
- terminal (allow/require_approval/block)
- git (force push, push-to-main restrictions)
- supervisor (no-progress thresholds, optional LLM config)
