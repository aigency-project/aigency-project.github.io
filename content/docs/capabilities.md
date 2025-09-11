---
title: Aigency::Service::Capabilities
---

This resource defines the technical capabilities exposed by an Aigency service.

Source: `aigency-lib/aigency/schemas/service/capabilities.py`

## Syntax
```yaml
streaming: <bool>
```

## Properties
- **streaming**
  - Description: Whether the agent supports streaming responses.
  - Type: boolean
  - Required: True

## Example
```yaml
streaming: true
```
