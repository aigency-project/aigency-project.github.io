---
title: Aigency::Observability
linkTitle: Observability
type: docs
prev: /docs/aigency
next: /docs/aigency/observability/monitoring/
weight: 4
---

This resource groups all observability configurations for the agent.

## Syntax
```yaml
monitoring: [Monitoring]
```

## Properties
- **monitoring**
  - Description: Monitoring tools configuration.
  - Type: [Monitoring](/docs/aigency/observability/monitoring/)
  - Required: True

## Example
```yaml
monitoring:
  phoenix:
    host: phoenix
    port: 6006
```
