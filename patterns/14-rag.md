# Ch. 14 — Knowledge Retrieval (RAG)

> Ground LLM generation in retrieved, up-to-date external knowledge rather than relying on stale parametric memory.

[← Back to README](../README.md)

---

## What It Is

Retrieval-Augmented Generation (RAG) combines a retrieval pipeline with an LLM generator. When a query comes in, the system retrieves the most relevant documents or chunks from an external knowledge source (vector database, document store, search index), injects that context into the LLM's prompt, and generates a grounded answer. The model doesn't need to "know" the answer — it reads and reasons from retrieved evidence.

RAG is now a foundational pattern for any agent that needs to work with documents, domain-specific knowledge, or information that changes over time.

---

## When to Use

- The model's built-in knowledge is stale or insufficient for the domain
- Long documents that don't fit in a single context window
- Domain-specific corpora (internal docs, legal documents, technical manuals)
- Factual grounding and source citations are required
- Real-time or frequently updated information (news, prices, policies)

---

## Key Implementation Insight

The quality of RAG is determined by retrieval quality, not just generation quality. Focus on: **chunking strategy** (how you split documents affects what gets retrieved), **embedding quality** (the retrieval model matters), **metadata filters** (let users and agents narrow the search scope), and **re-ranking** (a second pass to reorder top-k results by relevance). After retrieval, prompt the LLM to include **source citations** and add a verification layer to catch hallucinated citations. Evaluate retrieval and generation **end-to-end** — a retrieval metric alone doesn't tell you if the answer was good.

---

## Quick Checklist

- [ ] Chunking strategy optimized for retrieval quality (not just ingestion speed)?
- [ ] Metadata attached to chunks for filtering (date, source, category)?
- [ ] Re-ranking applied to top-k retrieved results?
- [ ] Source citations included in generated output?
- [ ] End-to-end evaluation pipeline (not just retrieval in isolation)?
- [ ] Incremental updates strategy for keeping the index fresh?

---

## Related Patterns

- [Memory Management](08-memory-management.md) — memory applies the same retrieval principle to interaction history
- [Tool Use](05-tool-use.md) — retrieval is often implemented as a tool call
- [Evaluation and Monitoring](19-evaluation-monitoring.md) — RAG pipelines need end-to-end eval (precision, recall, groundedness)
