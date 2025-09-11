---
title: Aigency::Service
---

This resource defines the network and communication configuration of an Aigency agent service.

Source: `aigency-lib/aigency/schemas/service/service.py`

## Syntax
```yaml
url: <string>
interface: [Interface](/docs/interface/)
capabilities: [Capabilities](/docs/capabilities/)
```

## Properties
- **url**
  - Description: Base URL where the agent service is accessible.
  - Type: string
  - Required: True

- **interface**
  - Description: Communication interface configuration.
  - Type: [Interface](/docs/interface/)
  - Required: True

- **capabilities**
  - Description: Technical capabilities of the service.
  - Type: [Capabilities](/docs/capabilities/)
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
