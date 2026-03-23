# Appendix A — Advanced Prompting Techniques

[← Back to README](../README.md)

---

## Summary

Appendix A distills the prompting techniques that make agentic systems more reliable in practice:

- **Clear system instructions and personas** to establish role and constraints
- **Few-shot exemplars** to demonstrate the desired structure, tone, and behavior
- **Chain-of-thought / scratchpad prompts** for multi-step reasoning
- **ReAct-style prompting** to interleave reasoning and tool use
- **Explicit output schemas** so agents produce machine-readable results
- **Self-review and iterative refinement** to reduce hallucinations and improve correctness

The big theme: prompting is not just about sounding clever. It's about creating predictable interfaces between the model and the rest of your system. The more structured your prompts and outputs, the easier the agent is to debug, compose, and trust.

---

## Why It Matters for Agents

Agents break when prompts are vague, outputs are messy, and tool descriptions are underspecified. This appendix reinforces a core message of the whole book: prompt design is interface design. If you want composable, production-grade agents, you need prompts that are explicit, constrained, and testable.
