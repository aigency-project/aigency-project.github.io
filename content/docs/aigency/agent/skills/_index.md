---
title: Aigency::Agent::Skill
linkTitle: Skill
type: docs
weight: 2
prev: docs/aigency/agent/
---

This resource defines a specific skill or capability of an agent.

## Syntax
```yaml
id: <string>
name: <string>
description: <string>
tags:
  - <string>
examples:
  - <string>
```

## Properties
- **id**
  - Description: Unique identifier for the skill.
  - Type: string
  - Required: True

- **name**
  - Description: Human-readable name of the skill.
  - Type: string
  - Required: True

- **description**
  - Description: Detailed description of what the skill does.
  - Type: string
  - Required: True

- **tags**
  - Description: Tags for categorizing the skill.
  - Type: list of string
  - Required: True

- **examples**
  - Description: Usage examples for the skill.
  - Type: list of string
  - Required: True

## Example
```yaml
id: greet_user
name: Greet User
description: Greets the user and introduces itself as a demonstration agent
tags: [greeting, introduction, presentation]
examples:
  - "Hello, how are you?"
  - "Introduce yourself"
```
