# Sample Decision Log

This example shows a sanitized decision record for a single governed action attempt.

## Purpose

The decision log exists so an observer can inspect:

- what was requested
- what authority was active
- why the system allowed, denied, or escalated
- what happened after the decision

## Sanitized Example

```yaml
decision_id: "dec_public_2026_06_11_07"
timestamp: "2026-06-11T14:22:17Z"
manifest_id: "mf_public_2026_06_11_01"
session_id: "session.public-demo.014"

requested_action:
  domain: "workspace_change"
  tool_class: "file_write"
  requested_target: "drafts/status-summary.md"
  operator_intent: "update a public-facing progress note"

governing_context:
  standing_domain: "workspace_change"
  standing_state: "limited"
  authority_scope_match: true
  sensitivity_class: "low"
  novelty_class: "known_pattern"

decision:
  outcome: "allow"
  reason_code: "in_scope_low_risk_known_pattern"
  fail_closed_triggered: false
  escalation_required: false

execution_link:
  executor_validation: "passed"
  callback_status: "completed"
  post_execution_review: "no anomaly detected"

audit_notes:
  evidence_summary:
    - "target path matched issued writable scope"
    - "requested action type matched manifest authority"
    - "no restricted pattern was implicated"
```

## Interpreting The Record

A useful decision record is not just an allow or deny bit. It preserves enough governing context that the outcome can be reviewed later and compared against future policy changes.

## Alternate Outcomes

The same shape can also represent:

- `deny`: for explicit out-of-scope actions
- `escalate`: for ambiguous or sensitive actions
- `allow_with_additional_review`: for bounded cases that need downstream inspection
