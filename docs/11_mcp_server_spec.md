# MCP Server Spec (MVP)

## Tools
- agentguard.run_command(command, cwd, env?)
- agentguard.apply_patch(patch, files[])
- agentguard.git_action(action, args)
  - action: status | diff | commit | push | open_pr

## Per-call pipeline
1) Build ActionIntent
2) Apply mode constraints
3) Evaluate policy -> decision
4) If REQUIRE_APPROVAL: return approval request payload
5) If ALLOW/WARN (after continue): execute
6) Emit audit events
7) Return structured result (stdout/stderr/exit, patch applied summary, git output)
