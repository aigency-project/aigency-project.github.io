---
title: Aigency::Agent::RemoteAgent
linkTitle: RemoteAgent
weight: 4
prev: docs/aigency/agent
type: docs
---

This resource defines configuration for connecting to remote agents in the A2A protocol.

## Syntax
```yaml
name: <string>
host: <string>
port: <int>  # 1-65535
```

## Properties
- **name**
  - Description: Name identifier for the remote agent.
  - Type: string
  - Required: True

- **host**
  - Description: Hostname or IP address of the remote agent.
  - Type: string
  - Required: True

- **port**
  - Description: Port number for the remote agent connection.
  - Type: integer (1-65535)
  - Required: True

## Example
```yaml
name: data_processor
host: agent-data-processor
port: 8080
```
