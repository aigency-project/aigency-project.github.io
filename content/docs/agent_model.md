---
title: Aigency::Agent::Model
---

This resource defines the configuration for the AI model used by an agent.

Source: `aigency-lib/aigency/schemas/agent/model.py`

## Syntax
```yaml
name: <string>
provider: [ProviderConfig](/docs/provider_config/)
```

## Properties
- **name**
  - Description: Name of the AI model to use.
  - Type: string
  - Required: True

- **provider**
  - Description: Provider configuration details.
  - Type: [ProviderConfig](/docs/provider_config/)
  - Required: False

## Example
```yaml
name: gpt-4
provider:
  name: openai
  endpoint: https://api.openai.com
```
