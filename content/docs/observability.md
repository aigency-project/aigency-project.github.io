---
title: Aigency::Observability
---

This resource groups all observability configurations for the agent.

Source: `aigency-lib/aigency/schemas/observability/observability.py`

## Syntax
```yaml
monitoring: [Monitoring](/docs/monitoring/)
```

## Properties
- **monitoring**
  - Description: Monitoring tools configuration.
  - Type: [Monitoring](/docs/monitoring/)
  - Required: True

## Example
```yaml
monitoring:
  phoenix:
    host: phoenix
    port: 6006
```
