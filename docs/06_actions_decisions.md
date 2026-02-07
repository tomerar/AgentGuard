# Actions & Decisions

## Action Types (MVP)
- TERMINAL_COMMAND
- FILE_PATCH
- GIT_ACTION

## Decisions
- ALLOW: execute immediately
- WARN: require “Continue”
- REQUIRE_APPROVAL: needs explicit approval token
- BLOCK: deny and offer safer alternative

## Approval Tokens
- approve_once: for the next matching action
- approve_for_minutes: TTL window
- scope: workspace + action type + normalized command/path + operation
