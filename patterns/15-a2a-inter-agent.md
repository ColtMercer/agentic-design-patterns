# Ch. 15 — Inter-Agent Communication (A2A)

> Standardize messaging, discovery, and task coordination between heterogeneous AI agents.

[← Back to README](../README.md)

---

## What It Is

Inter-Agent Communication (A2A) is an open protocol and design pattern for letting agents talk to each other across frameworks, vendors, and runtimes. Instead of hard-coding one agent to call another with bespoke glue, A2A defines shared contracts for discovery, metadata, task exchange, and results. That makes agents composable, replaceable, and easier to orchestrate as a network.

A2A is to agent-to-agent coordination what MCP is to agent-to-tool interaction.

---

## When to Use

- You want multiple specialized agents to collaborate on one workflow
- Agents come from different vendors or frameworks
- You need a federated ecosystem rather than one monolithic supervisor
- Third-party agents need to plug into your system cleanly
- You want swappable agents without rewriting orchestration logic

---

## Key Implementation Insight

Treat the protocol itself as the contract. Standardize **Agent Cards** (capabilities and metadata), message schemas, authentication, provenance, and versioning. Orchestration should depend on those contracts, not on vendor-specific behavior. Add tracing and graceful degradation so one unavailable downstream agent doesn't collapse the whole system.

---

## Quick Checklist

- [ ] Agent capability metadata published clearly?
- [ ] Message schemas versioned and documented?
- [ ] Authentication and provenance enforced end-to-end?
- [ ] Tracing/logging in place for inter-agent calls?
- [ ] Timeouts and fallback behavior defined for unavailable agents?
- [ ] Agents swappable without changing orchestration code?

---

## Related Patterns

- [Multi-Agent Collaboration](07-multi-agent.md) — A2A provides the coordination layer for multi-agent systems
- [Model Context Protocol (MCP)](10-mcp.md) — MCP standardizes agent-to-tool calls, while A2A standardizes agent-to-agent calls
- [Routing](02-routing.md) — routing decides which downstream agent should receive a task
