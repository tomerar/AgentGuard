# AgentGuard — MVP Plan & Product Spec (v1.0)

**Document type:** MVP PRD / Product Specification  
**Status:** Final (MVP)  
**Primary IDE:** Cursor  
**Compatibility:** VS Code (extension)  
**Core enforcement:** MCP Server (tools gateway)  
**Optional LLM supervisor:** explain/challenge/suggest only (never overrides deterministic policy)

---

## 1) Overview

AgentGuard is a governance layer for IDE agents that prevents unsafe actions unless they comply with a repo-defined policy or receive explicit approval.
The MVP enforces actions through AgentGuard MCP tools and offers an IDE-native UX via a VS Code extension.

---

## 2) Problem Statement

Coding agents can:
- execute destructive/expensive terminal commands,
- modify sensitive infra/auth/CI areas,
- drift from a plan and iterate without progress,
- produce changes that are hard to audit.

Existing protections are often best-effort or fragmented across tools. Teams need a consistent governance layer.

---

## 3) Goals & Success Metrics

### MVP Goals
1. Deterministic enforcement for agent actions via MCP tools gateway.
2. Safe-by-default workflow (Suggest-first).
3. Hard safety controls for terminal, sensitive files, git operations.
4. Supervisor discipline: plan gating for high risk + no-progress loop detection.
5. Auditability: local JSONL timeline for every run.

### Success Metrics
- ≥90% of agent actions are routed via AgentGuard MCP tools (measured via audit).
- 0 unapproved edits to blocked sensitive paths in controlled demos.
- 0 executions of blocked command patterns in controlled demos.
- ≤2 approvals per “standard bugfix” flow (dogfood benchmark).
- 100% of runs produce a usable JSONL audit timeline.

---

## 4) Non-Goals (MVP)

- OS-level sandboxing / security boundary.
- Governing manual user commands outside AgentGuard pathway.
- Centralized SaaS governance (local-first).
- Full org policy management (minimal policy-as-code only).

---

## 5) Personas & MVP Use Cases

### Personas
- Developer: wants speed without risk.
- Tech lead/security-minded dev: wants guardrails and auditability.
- Platform/DevOps contributor: needs protection for infra workflows.

### MVP Use Cases
1. Suggest-first code change: agent proposes patch; user reviews and applies.
2. Guarded terminal: safe commands allowed; risky commands approval; destructive blocked.
3. Sensitive path protection: CI/infra/auth paths blocked or approval-gated.
4. Git governance: block force push; block push to main/master; encourage PR flow.
5. No-progress loop intervention: repeated failures trigger supervisor intervention.

---

## 6) Key Decisions

### Enforcement via MCP tools
Agents execute actions through AgentGuard MCP tools (run_command/apply_patch/git_action). This gives deterministic control.

### Extension as UX plane
VS Code extension provides modes, approvals UI, policy inspector, and timeline.

### Hooks are Phase 2
Optional later for deeper lifecycle observation/control; MVP does not depend on hooks.

---

## 7) MVP Scope & Requirements (Summary)

- Modes: READ_ONLY, SUGGEST (default), GUARDED, FULL_TEMP (TTL)
- Policy-as-code: `.agentguard/policy.yml`
- MCP tools: run_command, apply_patch, git_action
- Terminal parsing: chain-aware evaluation (&&, ;, |, redirects)
- Supervisor v0: deterministic plan gating + no-progress detection
- Approvals: approve once / approve TTL / deny with reason
- Audit: JSONL timeline per run

---

## 8) Risks & Mitigations

- Setup friction: provide init script + minimal config; later use programmatic MCP registration.
- Bypass risk if agent doesn't use AgentGuard tools: provide standard agent instructions; later add hook-based off-path detection.
- Terminal parsing complexity: default to REQUIRE_APPROVAL when uncertain.
- Alert fatigue: risk tiers + TTL approvals + Suggest-first default.

---

## 9) Milestones

- M0: scaffolds (extension + MCP server) + policy loader + JSONL audit
- M1: file governance (patch flow + sensitive paths + approvals + timeline)
- M2: terminal governance (parser + approvals)
- M3: git governance (push restrictions + audit)
- M4: supervisor v0 (plan gate + no-progress)
- M5: optional LLM supervisor (explain/challenge/suggest)

---

## 10) Definition of Done (MVP)

- Modes behave correctly (READ_ONLY blocks, SUGGEST never auto-writes, FULL_TEMP expires)
- Terminal allow/require/block works with chain-aware parsing
- Sensitive paths enforced as per policy
- Git restrictions enforced (force push blocked; push to main blocked)
- Supervisor gates high-risk actions without plan and detects loops
- JSONL audit timeline exists for every run
