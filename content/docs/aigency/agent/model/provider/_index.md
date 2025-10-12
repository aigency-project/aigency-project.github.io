---
title: Aigency::Agent::ProviderConfig
linkTitle: ProviderConfig
type: docs
prev: docs/aigency/agent/model/
---

This resource defines the configuration for an AI model provider.

## Syntax
```yaml
name: <string>
api_base: <string | null>
```

## Properties
- **name**
  - Description: Name of the AI provider.
  - Type: string
  - Required: True

- **api_base**
  - Description: Custom endpoint URL for the provider.
  - Type: string
  - Required: False

## Example
```yaml
name: openai
api_base: https://api.openai.com
```
