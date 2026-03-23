# Ch. 3 — Parallelization

> Decompose work into independent subtasks, execute them concurrently, and aggregate the results.

[← Back to README](../README.md)

---

## What It Is

Parallelization is a map-reduce pattern applied to LLM workflows. You split a large task into independent chunks, fan out to multiple concurrent LLM calls or agents (map), then merge and reconcile the outputs into a final result (reduce). A classic example: summarizing 50 documents by summarizing each in parallel, then synthesizing the summaries.

The key constraint is that parallel tasks must be **truly independent** — no shared mutable state between them.

---

## When to Use

- Processing large datasets, multiple documents, or many data sources simultaneously
- Any workload where subtasks don't depend on each other's outputs
- Latency matters and sequential execution is too slow
- You want to generate multiple candidate outputs and pick the best (self-consistency voting)
- Multi-perspective analysis where different agents analyze the same input independently

---

## Key Implementation Insight

Shard inputs sensibly (by document, by question, by chunk), enforce **structured outputs** from parallel workers (JSON makes aggregation deterministic), and build a robust aggregator that handles conflicts, duplicates, and partial failures. Don't assume all workers finish — handle timeouts and partial results gracefully. Manage **rate limits** carefully: fan-out of 50 concurrent calls will hit API limits fast. Cache results to avoid redundant calls on retry.

---

## Quick Checklist

- [ ] Tasks are truly independent (no shared mutable state)?
- [ ] API rate limits accounted for in fan-out size?
- [ ] Structured outputs enforced so aggregation is deterministic?
- [ ] Partial failures handled — system doesn't crash if one worker fails?
- [ ] Aggregation logic tested with conflicting or duplicate inputs?
- [ ] Results cached to avoid redundant work on retry?

---

## Related Patterns

- [Multi-Agent Collaboration](07-multi-agent.md) — parallelization is the core mechanism behind ParallelAgent
- [Prompt Chaining](01-prompt-chaining.md) — parallelization often feeds into a chained synthesis step
- [Routing](02-routing.md) — route different subtasks to different specialists before parallelizing
