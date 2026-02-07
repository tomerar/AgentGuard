# AgentGuard (MVP)

AgentGuard is a governance layer for AI agent actions inside the IDE (Cursor-first, VS Code compatible).  
It provides deterministic enforcement via an MCP server and a VS Code extension for UX, modes, approvals, and audit.

## What it solves
- Prevents unsafe agent actions (terminal, file edits, git actions) unless they pass repo-defined policy or receive explicit approval.
- Safe-by-default workflow with Suggest-first and time-limited elevated modes.
- Supervisor discipline: plan gating for high-risk actions and no-progress loop detection.
- Audit timeline (JSONL) for full traceability.

## Architecture
- **VS Code Extension**: UI + policy editor/inspector + approvals queue + timeline viewer.
- **MCP Server**: enforcement + execution gateway via MCP tools:
  - `agentguard.run_command`
  - `agentguard.apply_patch`
  - `agentguard.git_action`

## Quick start (MVP)
1. Add `.agentguard/policy.example.yml` and copy to `.agentguard/policy.yml`
2. Start MCP server locally (implementation TBD)
3. Install extension (implementation TBD)
4. Configure Cursor to expose AgentGuard MCP tools to the agent

See `docs/01_mvp_plan_prd.md` for the complete MVP plan and spec.
