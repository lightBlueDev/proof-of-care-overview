# Standing Model

Proof-of-Care separates standing from raw capability.

## Why Standing Matters

Static permissions alone do not capture how trust changes over time. An agent may operate reliably in one domain, weakly in another, and unpredictably in a third. A meaningful governance boundary needs room for that distinction.

## Standing As Operational Trust

Standing represents the system's current basis for treating an agent as more or less trustworthy within a given domain or behavior class.

This enables:

- domain-specific trust progression
- narrowing after degraded outcomes
- explicit escalation behavior when certainty is low
- more realistic trust modeling than a single universal score

## Public Boundary

This repository does not disclose the private scoring logic, internal thresholds, or full state machinery behind standing updates. The public goal is to explain the model clearly without exposing the private tuning surface.
