# Ch. 2 — Routing

> Dispatch incoming requests to the best specialist model, agent, or tool based on intent, metadata, or embeddings.

[← Back to README](../README.md)

---

## What It Is

Routing is a dispatcher pattern. When a request arrives, a lightweight router classifies it and forwards it to the most appropriate handler — whether that's a specialized agent, a cheaper/faster model, a domain-specific tool, or a fallback. This mirrors how a support team routes tickets: billing questions go to billing, technical issues go to engineering.

The router itself is typically a fast, cheap LLM classifier or an embedding-based nearest-neighbor lookup — not a heavyweight model.

---

## When to Use

- You have multiple specialized agents or models with different strengths
- Requests vary widely in domain, complexity, or cost tolerance
- You want to route cheap/simple queries to a fast cheap model and complex ones to a more capable model
- You need to scale horizontally by adding new specialists without changing the core system
- Improving accuracy through specialization is more valuable than one-model-does-all

---

## Key Implementation Insight

Build a **router + registry** architecture: the router classifies intent and the registry maps intents to agents/models with their capabilities, costs, and SLAs. Enforce input/output schemas on downstream handlers so the router doesn't need to know implementation details. Always define **confidence thresholds** — if the router isn't confident, route to a safe fallback or human escalation. Log every routing decision so you can improve the router over time.

---

## Quick Checklist

- [ ] Router has a fallback for low-confidence classifications?
- [ ] Agent/model capabilities documented in a central registry?
- [ ] Input/output schemas enforced on every downstream handler?
- [ ] Routing decisions logged for analysis and improvement?
- [ ] Cost and latency of each route monitored separately?
- [ ] New routes can be added without modifying the router logic?

---

## Related Patterns

- [Prompt Chaining](01-prompt-chaining.md) — chains steps after routing dispatches the request
- [Planning](06-planning.md) — a planner can use routing to assign subtasks to the right agents
- [Multi-Agent Collaboration](07-multi-agent.md) — routing is the entry point for multi-agent orchestration
