# Sample Policy Replay

This example shows how prior decision history can be replayed against a proposed policy change before activation.

## Purpose

Replay exists to answer:

What would have changed if the new policy had been active already?

That matters because governance changes should be evaluated on historical behavior, not intuition alone.

## Sanitized Example

### Historical Input Set

```yaml
replay_window:
  from: "2026-05-01T00:00:00Z"
  to: "2026-05-31T23:59:59Z"

historical_decisions:
  total: 124
  by_outcome:
    allow: 88
    deny: 21
    escalate: 15

focus_domain:
  - "workspace_change"
```

### Proposed Policy Delta

```yaml
proposal_id: "policy_delta_public_03"
change_summary:
  - "route first-time writes to newly introduced path classes through escalation"
  - "keep previously established low-risk write patterns unchanged"
```

### Replay Result

| Result class | Count | Interpretation |
| --- | ---: | --- |
| unchanged allow | 76 | existing known-safe cases still pass |
| unchanged deny | 21 | clearly out-of-scope cases remain denied |
| unchanged escalate | 15 | already-sensitive cases remain escalated |
| allow -> escalate | 12 | newly classified path-novel actions become review-bound |
| allow -> deny | 0 | no previously valid action becomes outright blocked in this sample |

## What A Reviewer Learns

From this replay, a reviewer can infer that the proposal is:

- targeted rather than global
- increasing caution on novel write patterns
- unlikely to disrupt established low-risk behavior

## Public Boundary

This example intentionally omits private replay tooling, internal scoring logic, and exact policy language. The goal is to show the evaluation method, not the entire implementation.
