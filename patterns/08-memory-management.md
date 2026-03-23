# Ch. 8 — Memory Management

> Manage short-term context and long-term persistent memory so agents maintain coherence across turns and sessions.

[← Back to README](../README.md)

---

## What It Is

Memory Management defines how an agent stores and retrieves information across two horizons: **short-term** (the active context window for the current session) and **long-term** (persistent storage, typically a vector database, that survives across sessions). A well-designed memory system lets agents personalize behavior, recall past interactions, and combine fresh retrieved knowledge with immediate reasoning.

The primitives: **Session** (ephemeral, in-memory context), **session.state** (structured key-value within a session), and **MemoryService** (persistent, semantically queryable long-term storage).

---

## When to Use

- Conversational agents that need to remember context across a multi-turn dialogue
- Personalization — the agent should adapt to the user's history and preferences
- Long-running tasks that span multiple sessions or interactions
- Any agent that benefits from retrieving relevant past context (similar to RAG but for interaction history)
- Systems where rebuilding context from scratch every session is too expensive or impractical

---

## Key Implementation Insight

**Keep the context window focused** — don't just append everything; summarize or prune older context as the session grows. For long-term memory, store embeddings in a vector DB and retrieve only **relevant** memories at each turn (don't flood the context with everything ever remembered). Choose your storage backend based on scale: InMemory for tests and prototypes, Database or managed vector stores (VertexAI, Pinecone, etc.) for production. Inject retrieved long-term context into short-term context only when it's relevant to the current turn.

---

## Quick Checklist

- [ ] Context window managed to prevent overflow (summarization or pruning strategy)?
- [ ] Long-term storage is semantically queryable (vector DB)?
- [ ] Only relevant memories retrieved and injected per turn?
- [ ] Memory freshness and staleness handled (old memories don't mislead)?
- [ ] Privacy and data retention policies defined for stored memories?
- [ ] Storage backend chosen appropriately for scale (InMemory vs. Database vs. Cloud)?

---

## Related Patterns

- [Knowledge Retrieval (RAG)](14-rag.md) — RAG applies the same retrieval principle to document corpora
- [Learning and Adaptation](09-learning-adaptation.md) — learning updates long-term memory based on feedback
- [Goal Setting and Monitoring](11-goal-setting.md) — goals often need to persist in memory across sessions
