# Acceptance Criteria (MVP)

## Modes
- READ_ONLY blocks terminal + patch + git write
- SUGGEST never writes without explicit apply
- FULL_TEMP expires automatically

## Terminal
- rm -rf is BLOCK
- terraform apply is REQUIRE_APPROVAL (per policy)
- npm test / pytest is ALLOW (per policy)
- chain-aware parsing required (&&, ;, |)

## Files
- sensitive paths blocked or approval-gated exactly per policy

## Git
- force push blocked
- push to main/master blocked

## Supervisor
- high-risk without plan -> blocked with plan request
- repeated failures triggers intervention

## Audit
- JSONL log exists per run with full timeline
