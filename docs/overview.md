# Overview

Proof-of-Care is a governed trust boundary for autonomous agents.

Its function is straightforward in statement and demanding in implementation: determine whether an agent may take a requested action under present conditions, then enforce that decision in a way that is auditable, bounded, and resilient to ambiguity.

## Public Framing

This repository should be read as a documentation-first overview of a private implementation effort. It exists to make the system's architecture, thesis, and differentiation inspectable without exposing the full operational surface.

Proof-of-Care is not presented here as:

- a generic agent platform
- a UI-first product
- a loose trust-scoring layer
- a prompt-only safety wrapper

It is presented as a governance substrate at the action boundary.

## Problem Statement

Agent systems become materially more dangerous when their execution authority is implied rather than governed.

Common failure modes include:

- permissions that are too broad to reason about
- runtime context that silently expands effective authority
- safety logic embedded in prompts instead of enforced at the boundary
- audit trails that explain outcomes after the fact but do not constrain them
- policy changes that cannot be tested safely before deployment

Proof-of-Care exists to answer those problems with a control architecture that treats authority, enforcement, and audit as linked concerns.

## Design Commitments

The project is shaped by several commitments:

- authority should be explicit rather than inferred
- trust should be domain-specific rather than global
- ambiguity should resolve toward restriction
- execution should be tied to audit
- governance should be testable against prior behavior

Those commitments matter because the credibility of an agent boundary comes from what it can reliably prevent, not from what it claims to intend.
