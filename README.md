# 🤖 Agentic Design Patterns

<p align="center">
  <img src="https://img.shields.io/badge/Patterns-21-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Pages-424-green?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Author-Antonio%20Gulli-purple?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Frameworks-LangChain%20%7C%20CrewAI%20%7C%20Google%20ADK-orange?style=for-the-badge" />
</p>

> A consumable reference distilled from *Agentic Design Patterns* by Antonio Gulli (424 pages).  
> Use the README to orient yourself. Click into any pattern for the full cheat sheet.

---

## 📖 About the Book

*Agentic Design Patterns* is a hands-on handbook for engineers and architects building autonomous AI systems. It distills 21 reusable patterns — from prompt pipelines to multi-agent coordination to safety guardrails — and pairs each with runnable code examples in LangChain/LangGraph, CrewAI, and Google ADK.

The book's thesis: raw LLM calls are unreliable at scale. Patterns are how you make agents predictable, maintainable, and production-ready.

---

## 🤖 What Makes an AI System an Agent?

An agent is a goal-oriented software entity that perceives its environment, reasons about objectives, executes actions via tools or APIs, and adapts from feedback.

```
┌─────────────────────────────────────────────────────────────────────┐
│                      THE 5-STEP AGENT LOOP                          │
│                                                                     │
│   ┌──────────┐    ┌──────────────────┐    ┌─────────┐              │
│   │  PERCEIVE │───▶│ GOAL ASSESSMENT  │───▶│  PLAN   │              │
│   │          │    │                  │    │         │              │
│   │ Ingest   │    │ Interpret        │    │ Generate│              │
│   │ inputs & │    │ objectives &     │    │ ordered │              │
│   │ API state│    │ constraints      │    │ steps   │              │
│   └──────────┘    └──────────────────┘    └────┬────┘              │
│                                                │                   │
│   ┌──────────────────────┐    ┌───────────────▼──────────┐        │
│   │   OBSERVE & LEARN    │◀───│    ACT / EXECUTE         │        │
│   │                      │    │                          │        │
│   │ Update memory/state  │    │ Call tools, services,    │        │
│   │ Reflect & adapt      │    │ or perform actions       │        │
│   └──────────────────────┘    └──────────────────────────┘        │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🗺️ Pattern Relationships

```
                        ┌─────────────────────────────────────────────┐
                        │           FOUNDATION PATTERNS               │
                        │                                             │
                        │  Prompt Chaining → Routing → Planning       │
                        │         ↕              ↕                    │
                        │  Parallelization   Reflection               │
                        │         ↕              ↕                    │
                        │    Multi-Agent  ←  Tool Use                 │
                        └──────────────┬──────────────────────────────┘
                                       │
              ┌───────────────────────▼────────────────────────┐
              │                 STATE LAYER                     │
              │  Memory Management · MCP · Learning · Goals     │
              └───────────────────────┬────────────────────────┘
                                      │
              ┌───────────────────────▼────────────────────────┐
              │               RELIABILITY LAYER                 │
              │   Exception Handling · Human-in-Loop · RAG      │
              └───────────────────────┬────────────────────────┘
                                      │
              ┌───────────────────────▼────────────────────────┐
              │                ADVANCED LAYER                   │
              │  A2A · Resources · Reasoning · Guardrails       │
              │     Evaluation · Prioritization · Exploration   │
              └────────────────────────────────────────────────┘
```

---

## ⚡ Quick Reference

| # | Pattern | Part | One-Liner |
|---|---------|------|-----------|
| 1 | [Prompt Chaining](patterns/01-prompt-chaining.md) | Core | Chain LLM calls so each output feeds the next |
| 2 | [Routing](patterns/02-routing.md) | Core | Dispatch requests to the best specialist model or agent |
| 3 | [Parallelization](patterns/03-parallelization.md) | Core | Run independent subtasks concurrently and merge results |
| 4 | [Reflection](patterns/04-reflection.md) | Core | Let the agent critique and iteratively improve its outputs |
| 5 | [Tool Use](patterns/05-tool-use.md) | Core | Give the agent deterministic external capabilities |
| 6 | [Planning](patterns/06-planning.md) | Core | Generate an explicit, executable plan before acting |
| 7 | [Multi-Agent Collaboration](patterns/07-multi-agent.md) | Core | Compose specialized agents to solve complex tasks |
| 8 | [Memory Management](patterns/08-memory-management.md) | State | Manage short-term context and long-term persistence |
| 9 | [Learning & Adaptation](patterns/09-learning-adaptation.md) | State | Continuously improve from interaction data and feedback |
| 10 | [Model Context Protocol (MCP)](patterns/10-mcp.md) | State | Standardize how LLMs discover and call external resources |
| 11 | [Goal Setting & Monitoring](patterns/11-goal-setting.md) | State | Define, track, and revise agent objectives dynamically |
| 12 | [Exception Handling](patterns/12-exception-handling.md) | Reliability | Detect failures and restore stable operation |
| 13 | [Human-in-the-Loop](patterns/13-human-in-the-loop.md) | Reliability | Gate high-risk decisions on targeted human judgment |
| 14 | [Knowledge Retrieval (RAG)](patterns/14-rag.md) | Reliability | Ground generation in retrieved, up-to-date knowledge |
| 15 | [Inter-Agent Comms (A2A)](patterns/15-a2a-inter-agent.md) | Advanced | Standardize messaging between heterogeneous agents |
| 16 | [Resource Optimization](patterns/16-resource-optimization.md) | Advanced | Adapt to cost, latency, and compute constraints |
| 17 | [Reasoning Techniques](patterns/17-reasoning-techniques.md) | Advanced | CoT, ToT, self-consistency for multi-step reasoning |
| 18 | [Guardrails / Safety](patterns/18-guardrails-safety.md) | Advanced | Layered safety architecture for production agents |
| 19 | [Evaluation & Monitoring](patterns/19-evaluation-monitoring.md) | Advanced | Measure correctness, cost, and safety continuously |
| 20 | [Prioritization](patterns/20-prioritization.md) | Advanced | Decide what the agent works on first |
| 21 | [Exploration & Discovery](patterns/21-exploration-discovery.md) | Advanced | Actively seek new information while managing risk |

---

## 🎯 Patterns by Use Case

Not sure which pattern to reach for? Start here.

### 🏗️ "I'm building something new"
| Goal | Start With |
|------|-----------|
| Simple multi-step task | [Prompt Chaining](patterns/01-prompt-chaining.md) |
| Different requests need different handling | [Routing](patterns/02-routing.md) |
| Big task that needs a blueprint | [Planning](patterns/06-planning.md) |
| Need external data or API calls | [Tool Use](patterns/05-tool-use.md) |
| Want to analyze multiple documents fast | [Parallelization](patterns/03-parallelization.md) |

### 🔒 "I'm making it production-ready"
| Goal | Start With |
|------|-----------|
| Handle API failures gracefully | [Exception Handling](patterns/12-exception-handling.md) |
| Add safety filters | [Guardrails / Safety](patterns/18-guardrails-safety.md) |
| Know if it's working | [Evaluation & Monitoring](patterns/19-evaluation-monitoring.md) |
| Escalate edge cases to a human | [Human-in-the-Loop](patterns/13-human-in-the-loop.md) |
| Reduce hallucinations with real data | [RAG](patterns/14-rag.md) |

### 🧠 "I'm improving quality"
| Goal | Start With |
|------|-----------|
| Outputs aren't good enough | [Reflection](patterns/04-reflection.md) |
| Need better multi-step reasoning | [Reasoning Techniques](patterns/17-reasoning-techniques.md) |
| Agent should remember context | [Memory Management](patterns/08-memory-management.md) |
| System should improve over time | [Learning & Adaptation](patterns/09-learning-adaptation.md) |
| Multiple specialists would do better | [Multi-Agent Collaboration](patterns/07-multi-agent.md) |

### 💰 "I'm optimizing for cost/scale"
| Goal | Start With |
|------|-----------|
| Reduce latency or API spend | [Resource Optimization](patterns/16-resource-optimization.md) |
| Triage what gets compute first | [Prioritization](patterns/20-prioritization.md) |
| Share tools across multiple agents | [MCP](patterns/10-mcp.md) |
| Connect agents from different systems | [A2A](patterns/15-a2a-inter-agent.md) |
| Track long-running goals | [Goal Setting & Monitoring](patterns/11-goal-setting.md) |

### 🚀 "I'm going advanced"
| Goal | Start With |
|------|-----------|
| Agent needs to find unknowns | [Exploration & Discovery](patterns/21-exploration-discovery.md) |
| Connect to third-party agents | [A2A](patterns/15-a2a-inter-agent.md) |
| Balance cost vs. accuracy dynamically | [Resource Optimization](patterns/16-resource-optimization.md) |
| Agent must work across frameworks | [MCP](patterns/10-mcp.md) |

---

## 📦 Part One: Core Patterns (Ch. 1–7)

Foundational patterns every agentic system needs.

| | Pattern | Summary |
|-|---------|---------|
| 1 | [Prompt Chaining](patterns/01-prompt-chaining.md) | Pipeline where each LLM output is the next step's input |
| 2 | [Routing](patterns/02-routing.md) | Smart dispatch to the right specialist |
| 3 | [Parallelization](patterns/03-parallelization.md) | Concurrent execution with deterministic merge |
| 4 | [Reflection](patterns/04-reflection.md) | Producer/Critic loop for iterative self-improvement |
| 5 | [Tool Use](patterns/05-tool-use.md) | Ground agents in external APIs, search, databases |
| 6 | [Planning](patterns/06-planning.md) | Generate structured plans, then execute and replan |
| 7 | [Multi-Agent](patterns/07-multi-agent.md) | Orchestrate specialized agents with defined roles |

---

## 🧠 Part Two: State & Learning (Ch. 8–11)

Patterns for persistence, adaptation, and goal tracking.

| | Pattern | Summary |
|-|---------|---------|
| 8 | [Memory Management](patterns/08-memory-management.md) | Short-term context + long-term vector storage |
| 9 | [Learning & Adaptation](patterns/09-learning-adaptation.md) | Fine-tuning, RL, and feedback loops |
| 10 | [MCP](patterns/10-mcp.md) | Open protocol for tool/resource interoperability |
| 11 | [Goal Setting](patterns/11-goal-setting.md) | Track and revise objectives at runtime |

---

## 🛡️ Part Three: Reliability (Ch. 12–14)

Making agents resilient and trustworthy.

| | Pattern | Summary |
|-|---------|---------|
| 12 | [Exception Handling](patterns/12-exception-handling.md) | Retries, fallbacks, rollbacks, escalation |
| 13 | [Human-in-the-Loop](patterns/13-human-in-the-loop.md) | Gating, review UIs, correction feedback |
| 14 | [RAG](patterns/14-rag.md) | Retrieval stack, chunking, vector search, citations |

---

## 🚀 Part Four: Advanced Patterns (Ch. 15–21)

Scaling, safety, and optimization for production.

| | Pattern | Summary |
|-|---------|---------|
| 15 | [A2A](patterns/15-a2a-inter-agent.md) | Open protocol for heterogeneous agent ecosystems |
| 16 | [Resource Optimization](patterns/16-resource-optimization.md) | Cost/latency-adaptive routing and execution |
| 17 | [Reasoning Techniques](patterns/17-reasoning-techniques.md) | CoT, ToT, self-consistency, verifier agents |
| 18 | [Guardrails](patterns/18-guardrails-safety.md) | Defense-in-depth safety architecture |
| 19 | [Evaluation & Monitoring](patterns/19-evaluation-monitoring.md) | Model CI, telemetry, regression detection |
| 20 | [Prioritization](patterns/20-prioritization.md) | Schedulers, preemption, budget caps |
| 21 | [Exploration & Discovery](patterns/21-exploration-discovery.md) | Curiosity-driven agents with safe exploration |

---

## 📎 Appendices

- [Appendix A — Advanced Prompting Techniques](appendices/A-advanced-prompting.md)
- [Appendices B–G — Frameworks, GUI Agents, CLI, Reasoning Engines, Coding Agents](appendices/B-G-overview.md)

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

<p align="center">
  <i>Based on <strong>"Agentic Design Patterns"</strong> by Antonio Gulli (424 pages).<br>
  All author royalties donated to <a href="https://www.savethechildren.org">Save the Children</a>.</i>
</p>
