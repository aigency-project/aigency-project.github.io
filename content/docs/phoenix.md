---
title: Aigency::Observability::Phoenix
---

This resource defines configuration for the Phoenix monitoring system.

Source: `aigency-lib/aigency/schemas/observability/phoenix.py`

## Syntax
```yaml
host: <string>
port: <int>
```

## Properties
- **host**
  - Description: Hostname or IP address for Phoenix monitoring service.
  - Type: string
  - Required: True

- **port**
  - Description: Port number for Phoenix monitoring service.
  - Type: integer
  - Required: True

## Example
```yaml
host: phoenix
port: 6006
```
