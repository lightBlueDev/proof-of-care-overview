# Architecture

Proof-of-Care is organized around a governed execution loop that binds session authority, policy evaluation, action enforcement, and post-execution standing updates into one control surface.

## Execution Loop

```text
session
  -> signed manifest
  -> gateway decision
  -> shim enforcement
  -> executor validation
  -> tool execution
  -> execution callback
  -> standing update
  -> manifest reissue
```

## Component Responsibilities

### Session initialization

The session establishes the actor, operating context, and boundary assumptions required for authority issuance.

### Signed manifest

The manifest defines the capabilities available to the agent for that session. It is intended to be authoritative, bounded, and resistant to accidental scope expansion during runtime.

### Gateway decision

The gateway evaluates requested actions against authority, standing, policy, and context. This is the primary decision point for allow, deny, or escalation behavior.

### Shim enforcement

The enforcement layer ensures that policy outcomes are reflected in the actual execution path rather than left as advisory metadata.

### Executor validation

The executor validates that the requested action is still within the authorized boundary immediately before execution.

### Execution callback

Outcome data returns to the control loop so the system can link action, result, and downstream state changes.

### Standing update and manifest reissue

Standing changes over time. The model assumes trust can strengthen, weaken, or remain stable based on governed evidence, and that future authority should reflect that state.

## Architectural Intent

The important idea is not just that the system decides. It is that the system decides, enforces, records, and updates through a linked runtime loop. That is what makes the boundary governable rather than symbolic.
