---
title: Aigency::Service::Interface
linkTitle: Interface
type: docs
prev: /docs/aigency/service/
weight: 1
---

This resource defines the communication interface of an Aigency service, including supported input and output modes.

## Syntax
```yaml
default_input_modes:
  - <string>
  - <string>

default_output_modes:
  - <string>
  - <string>
```

## Properties
- **default_input_modes**
  - Description: Supported input communication modes.
  - Type: list of string
  - Required: True
  - Values: 
    - `text`
    - `text/plain`

- **default_output_modes**
  - Description: Supported output communication modes.
  - Type: list of string
  - Required: True
  - Values: 
    - `text`
    - `text/plain`

## Example
```yaml
default_input_modes:
  - text
  - text/plain
default_output_modes:
  - text
  - text/plain
```
