# MVP Scope

## Must Have
- MCP enforcement tools: run_command, apply_patch, git_action
- Extension UI: mode toggle, approvals queue, timeline viewer
- Policy-as-code: .agentguard/policy.yml
- Terminal parser: chain-aware, risk-feature tagging
- Sensitive path restrictions
- Git safety restrictions
- Supervisor v0: plan gating + no-progress

## Should Have
- TTL approvals (approve for N minutes)
- Audit redaction (mask secrets)
- Default policy pack

## Could Have (Post-MVP)
- Cursor hooks integration (observer / off-path detection)
- Centralized policy distribution
- SIEM export
