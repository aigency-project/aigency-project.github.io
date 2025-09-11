---
title: Aigency::Agent::Tools::FunctionTool
linkTitle: FunctionTool
type: docs
weight: 1
prev: docs/aigency/agent/tools/
---

## FunctionTool
Function-based tools loaded from Python modules.

### Syntax
```yaml
type: function
name: <string>
description: <string>
module_path: <string>
function_name: <string>
```

### Properties
- **type**
  - Description: The type of tool.
  - Type: string
  - Required: True
  - Value: 
    - `function`
- **name**
  - Description: Name identifier for the tool.
  - Type: string
  - Required: True
- **description**
  - Description: What the tool does.
  - Type: string
  - Required: True
- **module_path**
  - Description: Python module path containing the function.
  - Type: string
  - Required: True
- **function_name**
  - Description: Function name to load from the module.
  - Type: string
  - Required: True

### Example
```yaml
type: function
name: calculator
description: Adds two integers
module_path: math_tools
function_name: add
```