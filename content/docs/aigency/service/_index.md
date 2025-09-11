---
title: Aigency::Service
linkTitle: Service
type: docs
prev: /docs/aigency
next: docs/aigency/service/interface/
weight: 2
---

This resource defines the network and communication configuration of an Aigency agent service.

## Syntax
```yaml
url: <string>
interface: [Interface]
capabilities: [Capabilities]
```

## Properties
- **url**
  - Description: Base URL where the agent service is accessible.
  - Type: string
  - Required: True

- **interface**
  - Description: Communication interface configuration.
  - Type: [Interface](/docs/aigency/service/interface/)
  - Required: True

- **capabilities**
  - Description: Technical capabilities of the service.
  - Type: [Capabilities](/docs/aigency/service/capabilities/)
  - Required: True

## Example
```yaml
url: http://hello-world-agent:8080
interface:
  default_input_modes:
    - text
    - text/plain
  default_output_modes:
    - text
    - text/plain
capabilities:
  streaming: true
```
