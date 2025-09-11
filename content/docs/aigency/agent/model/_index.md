---
title: Aigency::Config::Agent::AgentModel
linkTitle: AgentModel
type: docs
weight: 1
prev: docs/aigency/agent/
next: docs/aigency/agent/model/provider/
---

This resource defines the configuration for the AI model used by an agent.

## Syntax
```yaml
name: <string>
provider: [ProviderConfig]
```

## Properties
- **name**
  - Description: Name of the AI model to use.
  - Type: string
  - Required: True

- **provider**
  - Description: Provider configuration details.
  - Type: [ProviderConfig](/docs/aigency/agent/model/provider/)
  - Required: False

## Example
```yaml
name: gpt-4
provider:
  name: openai
  endpoint: https://api.openai.com
```
