---
title: Aigency::Observability::Monitoring
---

This resource defines monitoring tool configuration groupings.

Source: `aigency-lib/aigency/schemas/observability/observability.py`

## Syntax
```yaml
phoenix: [Phoenix](/docs/phoenix/)
```

## Properties
- **phoenix**
  - Description: Phoenix monitoring configuration.
  - Type: [Phoenix](/docs/phoenix/)
  - Required: True

## Example
```yaml
phoenix:
  host: phoenix
  port: 6006
```
