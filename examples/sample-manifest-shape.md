# Sample Manifest Shape

This example shows the public-facing shape of a signed capability manifest at a level that is useful for evaluation without exposing private schema details, signing implementation, or validation logic.

## Purpose

The manifest is the bounded authority surface for a single agent session. It answers a simple question:

What may this agent do right now?

## Sanitized Example

```yaml
manifest_version: "public-sample/v1"
manifest_id: "mf_public_2026_06_11_01"
issued_at: "2026-06-11T14:00:00Z"
expires_at: "2026-06-11T16:00:00Z"

subject:
  agent_id: "agent.public-demo"
  session_id: "session.public-demo.014"
  operator_mode: "supervised"

authority:
  domains:
    repository_read:
      access: "allow"
      scope:
        repositories: ["sanitized-target"]
        paths: ["docs/", "README.md", "src/public-surface/"]

    workspace_change:
      access: "allow_with_limits"
      scope:
        writable_paths: ["drafts/", "notes/public/"]
        prohibited_patterns: ["secrets/*", ".env*", "deploy/*"]

    network_egress:
      access: "deny"

    credential_surfaces:
      access: "deny"

standing_snapshot:
  repository_read: "established"
  workspace_change: "limited"
  network_egress: "restricted"

policy_requirements:
  on_ambiguity: "fail_closed"
  on_scope_mismatch: "deny"
  on_novel_sensitive_action: "escalate"

verification:
  manifest_signature: "signed"
  issuer: "governance-boundary"
```

## How To Read It

- `subject` identifies the acting session, not a permanent universal agent identity.
- `authority.domains` keeps trust domain-specific instead of collapsing everything into one global permission bit.
- `standing_snapshot` shows that authority and standing are related but not identical.
- `policy_requirements` makes restriction behavior explicit instead of implied.

## What This Example Deliberately Omits

This public example does not expose:

- private signing formats
- internal validation steps
- full policy language
- operational thresholds
- complete domain taxonomy

The point is to make the authority model legible without publishing the full implementation surface.
