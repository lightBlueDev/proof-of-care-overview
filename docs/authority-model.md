# Authority Model

Proof-of-Care treats authority as an explicit, signed, and bounded surface.

## First-Class Authority

Authority is not inferred from prompt content, conversation drift, or tool availability alone. It is defined at session start and represented in a capability manifest that describes what the agent may do.

## Design Goals

The authority model is designed to ensure:

- capabilities are granted intentionally
- scope does not expand implicitly at runtime
- downstream executors can validate what was authorized
- delegation does not create net-new authority

## Public Interpretation

In public terms, the authority model is best understood as a structured answer to a simple question:

What may this agent do right now, and why?

The model is stronger when that answer is deterministic, inspectable, and difficult to widen by accident.

## Boundary Principle

Nothing the agent reads during execution should be able to enlarge the authority that was issued before execution began. That separation is central to the integrity of the boundary.
