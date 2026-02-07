# Architecture — High Level Design

## Components

### A) VS Code Extension (UX Plane)
- Mode Manager (READ_ONLY / SUGGEST / GUARDED / FULL_TEMP)
- Policy Loader + Inspector
- Approvals Panel (Action Queue)
- Timeline Panel (Audit viewer)
- Local log management

### B) MCP Server (Enforcement Plane)
- Action Gateway (single entry point)
- Policy Engine (deterministic)
- Terminal Parser (chain-aware)
- Approval Manager (tokens + TTL)
- Supervisor v0 (deterministic) + optional LLM supervisor
- Audit Logger (JSONL)

## Why enforcement via MCP
Deterministic control requires the agent to route actions through a controlled gateway.
MCP tools provide that gateway surface.

## Data Flow (MVP)
Agent -> MCP Tool -> Policy+Mode -> (Approval?) -> Execute -> Audit -> UI timeline
