# Terminal Parsing (MVP)

## Requirements
- Normalize command string (trim, collapse spaces, basic quote handling)
- Detect operators: &&, ||, ;, |, redirects
- Evaluate the entire chain, not only the first token
- Tag risk features:
  - pipe_to_shell (| bash / | sh)
  - destructive_delete (rm -rf, recursive deletes)
  - infra_high_blast (terraform apply/destroy, kubectl delete, etc.)

## Safe fallback
If parser is uncertain -> REQUIRE_APPROVAL
