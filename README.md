# Agentic Design Patterns

> **21 Patterns · 424 Pages · Antonio Gulli**  
> A consumable reference distilled from the full book — summaries, cheat sheets, and implementation guides.

---

## 📖 About the Book

*Agentic Design Patterns* is a practical, developer-focused handbook for building autonomous AI systems that perceive, plan, act, and adapt. It distills 21 reusable design patterns and pairs each with runnable code examples on popular canvases (LangChain/LangGraph, CrewAI, Google ADK). The emphasis is hands-on: pattern intent, real-world use cases, implementation notes, and runnable snippets so you can apply each pattern directly to your products.

The book targets engineers, architects, and technical product builders who need to move beyond single-prompt LLM usage into robust agentic systems. By the end you'll be able to (1) select appropriate patterns for a problem, (2) implement them on an agent framework, and (3) build more reliable, auditable, and maintainable agents.

---

## 🤖 What Makes an AI System an Agent?

An agent is a goal-oriented software entity that perceives its environment, reasons about objectives, and executes actions (often via tools/APIs) with some autonomy, memory, and the ability to communicate and adapt.

The five-step agent loop:

1. **Perceive** — ingest inputs and sensor/API state
2. **Goal Assessment** — interpret objectives and constraints
3. **Plan** — generate a concrete sequence of steps or subtasks
4. **Act / Execute** — call tools, services, or perform actions
5. **Observe & Learn** — capture results, update memory/state, reflect and adapt

---

## ⚡ Quick Reference

| # | Pattern | Part | One-Liner |
|---|---------|------|-----------|
| 1 | [Prompt Chaining](patterns/01-prompt-chaining.md) | Core | Chain LLM calls in a pipeline where each output feeds the next |
| 2 | [Routing](patterns/02-routing.md) | Core | Dispatch requests to the best specialist model, agent, or tool |
| 3 | [Parallelization](patterns/03-parallelization.md) | Core | Run independent subtasks concurrently and merge results |
| 4 | [Reflection](patterns/04-reflection.md) | Core | Let the agent critique and iteratively refine its own outputs |
| 5 | [Tool Use](patterns/05-tool-use.md) | Core | Give the agent deterministic external capabilities |
| 6 | [Planning](patterns/06-planning.md) | Core | Generate an explicit, executable plan before acting |
| 7 | [Multi-Agent Collaboration](patterns/07-multi-agent.md) | Core | Compose specialized agents to solve complex tasks together |
| 8 | [Memory Management](patterns/08-memory-management.md) | State & Learning | Manage short-term and long-term memory across sessions |
| 9 | [Learning and Adaptation](patterns/09-learning-adaptation.md) | State & Learning | Continuously improve from interaction data and feedback |
| 10 | [Model Context Protocol (MCP)](patterns/10-mcp.md) | State & Learning | Standardize how LLMs discover and call external resources |
| 11 | [Goal Setting and Monitoring](patterns/11-goal-setting.md) | State & Learning | Define, track, and revise agent objectives dynamically |
| 12 | [Exception Handling and Recovery](patterns/12-exception-handling.md) | Reliability | Detect failures and restore stable operation gracefully |
| 13 | [Human-in-the-Loop](patterns/13-human-in-the-loop.md) | Reliability | Gate high-risk decisions on targeted human judgment |
| 14 | [Knowledge Retrieval (RAG)](patterns/14-rag.md) | Reliability | Ground generation in retrieved, up-to-date external knowledge |
| 15 | [Inter-Agent Communication (A2A)](patterns/15-a2a-inter-agent.md) | Advanced | Standardize messaging and discovery between heterogeneous agents |
| 16 | [Resource-Aware Optimization](patterns/16-resource-optimization.md) | Advanced | Adapt to cost, latency, and compute constraints dynamically |
| 17 | [Reasoning Techniques](patterns/17-reasoning-techniques.md) | Advanced | Apply CoT, ToT, self-consistency to improve multi-step reasoning |
| 18 | [Guardrails / Safety Patterns](patterns/18-guardrails-safety.md) | Advanced | Constrain agent behavior with layered safety architecture |
| 19 | [Evaluation and Monitoring](patterns/19-evaluation-monitoring.md) | Advanced | Continuously measure correctness, cost, safety in production |
| 20 | [Prioritization](patterns/20-prioritization.md) | Advanced | Decide what the agent works on first under resource constraints |
| 21 | [Exploration and Discovery](patterns/21-exploration-discovery.md) | Advanced | Let agents actively seek new information while managing risk |

---

## 📦 Part One: Core Agentic Patterns (Ch. 1–7)

Foundational patterns every agentic system needs.

- [Ch. 1 — Prompt Chaining](patterns/01-prompt-chaining.md) — sequential pipelines where each LLM step feeds the next
- [Ch. 2 — Routing](patterns/02-routing.md) — intelligent dispatch to the right specialist
- [Ch. 3 — Parallelization](patterns/03-parallelization.md) — concurrent execution with deterministic merge
- [Ch. 4 — Reflection](patterns/04-reflection.md) — producer/critic loop for self-improvement
- [Ch. 5 — Tool Use](patterns/05-tool-use.md) — external APIs, search, databases, calculators
- [Ch. 6 — Planning](patterns/06-planning.md) — generate then execute structured plans
- [Ch. 7 — Multi-Agent Collaboration](patterns/07-multi-agent.md) — orchestrate specialized agents

---

## 🧠 Part Two: State & Learning (Ch. 8–11)

Patterns for persistence, adaptation, and goal-oriented behavior.

- [Ch. 8 — Memory Management](patterns/08-memory-management.md) — short-term context + long-term vector storage
- [Ch. 9 — Learning and Adaptation](patterns/09-learning-adaptation.md) — fine-tuning, RL, feedback loops
- [Ch. 10 — Model Context Protocol (MCP)](patterns/10-mcp.md) — open protocol for tool/resource interoperability
- [Ch. 11 — Goal Setting and Monitoring](patterns/11-goal-setting.md) — track and revise objectives at runtime

---

## 🛡️ Part Three: Reliability Patterns (Ch. 12–14)

Making agents resilient and trustworthy.

- [Ch. 12 — Exception Handling and Recovery](patterns/12-exception-handling.md) — retries, fallbacks, rollbacks, escalation
- [Ch. 13 — Human-in-the-Loop](patterns/13-human-in-the-loop.md) — gating, review UIs, correction feedback
- [Ch. 14 — Knowledge Retrieval (RAG)](patterns/14-rag.md) — retrieval stack, chunking, vector search, citations

---

## 🚀 Part Four: Advanced Patterns (Ch. 15–21)

Scaling, safety, and optimization for production agents.

- [Ch. 15 — Inter-Agent Communication (A2A)](patterns/15-a2a-inter-agent.md) — open protocol for multi-agent ecosystems
- [Ch. 16 — Resource-Aware Optimization](patterns/16-resource-optimization.md) — cost/latency-adaptive routing and execution
- [Ch. 17 — Reasoning Techniques](patterns/17-reasoning-techniques.md) — CoT, ToT, self-consistency, verifier agents
- [Ch. 18 — Guardrails / Safety](patterns/18-guardrails-safety.md) — defense-in-depth safety architecture
- [Ch. 19 — Evaluation and Monitoring](patterns/19-evaluation-monitoring.md) — model CI, telemetry, regression detection
- [Ch. 20 — Prioritization](patterns/20-prioritization.md) — schedulers, preemption, budget caps
- [Ch. 21 — Exploration and Discovery](patterns/21-exploration-discovery.md) — curiosity-driven agents with safe exploration

---

## 📎 Appendices

- [Appendix A — Advanced Prompting Techniques](appendices/A-advanced-prompting.md) — few-shot, CoT, ReAct, output schemas
- [Appendices B–G — Frameworks, Tools, CLI, Reasoning Engines, Coding Agents](appendices/B-G-overview.md)

---

## 🔑 Key Takeaways

1. **Patterns > prompts** — raw LLM calls break at scale; reusable patterns give you reliability, debuggability, and maintainability
2. **Separate concerns** — always decouple Planning from Execution, Producer from Critic, Routing from Implementation
3. **Treat memory explicitly** — context window management, long-term storage, and retrieval are engineering problems, not LLM magic
4. **Tools are the bridge to reality** — ground your agents in deterministic tool calls, not model imagination
5. **Safety is layered** — input sanitization + policy models + output filters + human review; no single guardrail is enough
6. **Evaluate like production software** — offline test suites, live telemetry, regression detection, and human spot-checks
7. **Composition is the goal** — the real skill is knowing which patterns to combine (e.g., RAG + Reflection + Guardrails for a production Q&A agent)

---

*Based on "Agentic Design Patterns" by Antonio Gulli (424 pages). All author royalties donated to [Save the Children](https://www.savethechildren.org).*
