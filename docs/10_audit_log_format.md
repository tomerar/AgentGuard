# Audit Log Format (JSONL)

## Storage
.agentguard/logs/<run_id>.jsonl

## Events (append-only)
- intent.created
- policy.decided
- approval.requested
- approval.granted
- approval.denied
- action.executed
- action.failed
- supervisor.feedback

## Redaction
- mask secrets (basic regex)
- cap sizes; store patch hashes for very large payloads
