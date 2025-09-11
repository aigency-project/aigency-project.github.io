---
title: Aigency::Metadata
---

This resource defines descriptive metadata for an Aigency agent, used for discovery, categorization, and documentation.

Source: `aigency-lib/aigency/schemas/metadata/metadata.py`

## Syntax
```yaml
name: <string>
version: <string>
description: <string>
```

## Properties
- **name**
  - Description: Name of the agent.
  - Type: string
  - Required: True

- **version**
  - Description: Version identifier of the agent.
  - Type: string
  - Required: True

- **description**
  - Description: Human-readable description of the agent's purpose.
  - Type: string
  - Required: True

## Example
```yaml
name: hello_world_agent
version: 1.0.0
description: A simple demonstration agent for the project.
```
