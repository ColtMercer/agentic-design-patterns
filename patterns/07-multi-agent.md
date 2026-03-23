# Ch. 7 — Multi-Agent Collaboration

> Compose specialized agents — researchers, critics, coordinators, executors — that coordinate to solve tasks no single agent handles well alone.

[← Back to README](../README.md)

---

## What It Is

Multi-Agent Collaboration orchestrates a system of specialized agents, each with a focused role, that work together toward a shared goal. Common patterns: a **SequentialAgent** where agents hand off in order, a **ParallelAgent** where agents work concurrently and results are merged, or a **Supervisor** agent that coordinates and routes work between specialists.

Think of it as building a team with distinct roles rather than expecting one generalist to do everything.

---

## When to Use

- Tasks benefit from specialization (researcher + writer + fact-checker > one all-purpose agent)
- Parallel data collection or analysis can happen simultaneously to reduce latency
- Quality improves with independent review by a separate agent
- The task is too large for a single context window
- You want modularity — swap out one specialist without rebuilding the whole system

---

## Key Implementation Insight

Define **clear agent roles** with single responsibilities, and standardize how they communicate (shared state schema, message passing, or blackboard pattern). At merge/synthesis time, the coordinator should **validate inputs** rather than blindly trust what other agents produced. Handle **failure isolation** — one agent failing should not cascade to the whole system. Security matters: agents that can call tools or other agents need scoped permissions, not unrestricted access.

---

## Quick Checklist

- [ ] Each agent has a single, well-defined responsibility?
- [ ] Shared state schema documented and typed?
- [ ] Coordinator validates inputs before synthesizing?
- [ ] One agent's failure doesn't cascade to others?
- [ ] Security boundaries enforced — agents have scoped tool/resource access?
- [ ] Attribution tracked — which agent produced which output?

---

## Related Patterns

- [Routing](02-routing.md) — routing is often the entry point for a multi-agent system
- [Parallelization](03-parallelization.md) — ParallelAgent is parallelization applied to agents
- [Inter-Agent Communication (A2A)](15-a2a-inter-agent.md) — the open protocol for cross-framework multi-agent comms
