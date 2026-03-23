# Ch. 10 — Model Context Protocol (MCP)

> Standardize how LLMs discover and call external resources, tools, and functions — vendor-agnostic and composable.

[← Back to README](../README.md)

---

## What It Is

The Model Context Protocol (MCP) is an open client-server protocol that standardizes how LLMs interact with external resources: tools, data sources, APIs, and interactive templates. Instead of building custom integrations for every model × tool combination, MCP defines a common contract so any MCP-compatible agent can discover and call any MCP-compatible server. Think of it as HTTP for agent-tool communication.

MCP servers expose: **Resources** (readable data), **Tools** (callable actions), and **Prompts** (interactive templates).

---

## When to Use

- You need vendor-agnostic tool integration that works across multiple LLM providers
- You're exposing legacy systems or microservices to agentic workflows and want a clean abstraction
- Building a platform where multiple agents from different frameworks need to share tools
- You want a federated ecosystem of reusable capability servers that any agent can consume
- Standardizing tool discovery and capability metadata across a team or organization

---

## Key Implementation Insight

**MCP is only as useful as the underlying API design.** A poorly designed API wrapped in MCP is still a poorly designed API. Build agent-friendly endpoints: deterministic filters and sorting, **structured textual outputs** (Markdown, JSON — not binary blobs the LLM can't reason about), and rich capability metadata so agents can make intelligent tool selection decisions. Treat MCP servers as **service contracts** — define error semantics, paging behavior, rate limits, and latency guarantees explicitly. Observability is critical: instrument every MCP call.

---

## Quick Checklist

- [ ] Endpoint outputs are structured and textual (not binary blobs)?
- [ ] Rich capability metadata exposed for discovery and selection?
- [ ] Error semantics clearly defined in the contract?
- [ ] Rate limits and latency guarantees provided to callers?
- [ ] Protocol versioning handled with backward compatibility?
- [ ] Every MCP call instrumented for observability (tracing, logging)?

---

## Related Patterns

- [Tool Use](05-tool-use.md) — MCP is the standardized protocol layer for tool exposure
- [Inter-Agent Communication (A2A)](15-a2a-inter-agent.md) — A2A handles agent-to-agent; MCP handles agent-to-tool
- [Planning](06-planning.md) — plans reference MCP tools as callable actions
