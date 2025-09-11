---
title: Aigency::Observability::Monitoring
linkTitle: Monitoring
type: docs
prev: /docs/aigency/observability
---

This resource defines monitoring tool configuration groupings.

## Syntax
```yaml
phoenix: [Phoenix]
```

## Properties
- **phoenix**
  - Description: Phoenix monitoring configuration.
  - Type: [Phoenix](/docs/aigency/observability/monitoring/phoenix/)
  - Required: True

## Example
```yaml
phoenix:
  host: phoenix
  port: 6006
```
