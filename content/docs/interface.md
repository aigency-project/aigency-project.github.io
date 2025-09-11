---
title: Aigency::Service::Interface
---

This resource defines the communication interface of an Aigency service, including supported input and output modes.

Source: `aigency-lib/aigency/schemas/service/interface.py`

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

- **default_output_modes**
  - Description: Supported output communication modes.
  - Type: list of string
  - Required: True

## Example
```yaml
default_input_modes:
  - text
  - text/plain
default_output_modes:
  - text
  - text/plain
```
