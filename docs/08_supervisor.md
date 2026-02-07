# Supervisor (MVP)

## Deterministic Supervisor (Required)
- Plan gating for HIGH risk actions:
  - must provide 3–7 bullet plan before action proceeds
- No-progress loop detection:
  - repeated failures >= threshold
  - too many similar actions without success signal
- Challenge prompts for HIGH risk:
  - blast radius
  - dry-run first
  - rollback plan
  - evidence (tests run)

## Optional LLM Supervisor (Allowed)
- Only for explain/challenge/suggest safer alternatives
- Must NEVER override deterministic policy (BLOCK stays BLOCK)
