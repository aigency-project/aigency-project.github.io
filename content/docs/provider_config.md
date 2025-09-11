---
title: Aigency::Agent::ProviderConfig
---

This resource defines the configuration for an AI model provider.

Source: `aigency-lib/aigency/schemas/agent/model.py`

## Syntax
```yaml
name: <string>
endpoint: <string | null>
```

## Properties
- **name**
  - Description: Name of the AI provider.
  - Type: string
  - Required: True

- **endpoint**
  - Description: Custom endpoint URL for the provider.
  - Type: string
  - Required: False

## Example
```yaml
name: openai
endpoint: https://api.openai.com
```
