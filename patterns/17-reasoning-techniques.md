# Ch. 17 — Reasoning Techniques

> Use structured reasoning methods to improve multi-step logic, correctness, and traceability.

[← Back to README](../README.md)

---

## What It Is

Reasoning Techniques are a family of prompting and architectural methods that improve how agents think through complex problems. The chapter covers patterns like chain-of-thought, tree-of-thoughts, decomposition, self-consistency, reflexion, verifier agents, and external tool-backed checking. These techniques make intermediate reasoning more explicit and final answers more reliable.

---

## When to Use

- Problems require multi-step logic or planning
- Mathematical or symbolic correctness matters
- Tasks are ambiguous and benefit from multiple candidate reasoning paths
- You need traceability for how the answer was produced
- Hallucination risk is high and outputs need verification

---

## Key Implementation Insight

Make intermediate steps **explicit and auditable**. Decompose large problems into smaller subqueries or roles, add verification layers, and use multiple reasoning passes or voting when ambiguity is high. The win is not from one magic prompt; it's from combining decomposition, validation, and consistency checks into a repeatable reasoning workflow.

---

## Quick Checklist

- [ ] Intermediate reasoning steps visible or logged?
- [ ] Problem decomposed into smaller verifiable parts?
- [ ] Verification layer added for high-stakes outputs?
- [ ] Self-consistency or voting used where ambiguity is high?
- [ ] Tool-backed checks used where deterministic verification is possible?
- [ ] Reasoning process evaluated for faithfulness, not just final accuracy?

---

## Related Patterns

- [Reflection](04-reflection.md) — reflection critiques and improves the reasoning trace
- [Planning](06-planning.md) — planning is structured reasoning applied to actions
- [Evaluation and Monitoring](19-evaluation-monitoring.md) — reasoning quality should be measured, not assumed
