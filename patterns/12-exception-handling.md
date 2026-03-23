# Ch. 12 — Exception Handling and Recovery

> Make agents resilient by treating failures as first-class state — with retries, fallbacks, rollbacks, and escalation paths.

[← Back to README](../README.md)

---

## What It Is

Exception Handling and Recovery is the pattern for making agents production-grade. Rather than crashing or silently producing wrong outputs when something goes wrong, this pattern gives agents a structured approach: classify the error, retry with backoff if transient, fall back to an alternative if persistent, roll back to a checkpoint if needed, or escalate to a human if none of the above resolves it.

In a real deployment, things go wrong constantly — API timeouts, malformed tool outputs, rate limits, partial state. This pattern is how you build agents that keep running.

---

## When to Use

- Any agent deployed in a production or semi-production environment
- Agents calling external APIs, databases, or tools (all of which fail intermittently)
- Long-running workflows where a single failure shouldn't abort everything
- Safety-critical or compliance-sensitive systems where silent failures are unacceptable
- Systems that need audit trails of what went wrong and how it was handled

---

## Key Implementation Insight

**Design recovery logic separately from business logic** — don't inline error handling in every tool call. Build a centralized error handler that classifies errors (transient vs. fatal, known vs. unknown), applies the right strategy per class, and logs every failure event. Make operations **idempotent** wherever possible so retries are safe. Use **state checkpoints** so a failed 20-step workflow can resume from step 15, not restart from scratch. Test failure modes explicitly — don't discover your error handling at 3am.

---

## Quick Checklist

- [ ] Error types classified (transient vs. fatal, known vs. unknown)?
- [ ] Retry logic bounded — max attempts + exponential backoff?
- [ ] Operations idempotent where retries are expected?
- [ ] State checkpoints implemented for long-running workflows?
- [ ] Clear escalation path defined (fallback system or human)?
- [ ] Failure events logged with context for post-mortem analysis?

---

## Related Patterns

- [Human-in-the-Loop](13-human-in-the-loop.md) — the final escalation path when automated recovery fails
- [Planning](06-planning.md) — plans should include replanning steps on failure
- [Guardrails / Safety](18-guardrails-safety.md) — guardrails detect failure conditions before they propagate
