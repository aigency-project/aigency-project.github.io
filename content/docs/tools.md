---
title: Aigency::Agent::Tools
---

This resource defines tool configuration models for agent capabilities, including function-based tools and MCP-based tools.

Source: `aigency-lib/aigency/schemas/agent/tools.py`

## ToolType
- Values: `mcp`, `function`

## BaseTool
Common fields for all tools.

### Syntax
```yaml
type: <mcp | function>
name: <string>
description: <string>
```

### Properties
- **type**
  - Description: The type of tool.
  - Type: enum `mcp` | `function`
  - Required: True
- **name**
  - Description: Name identifier for the tool.
  - Type: string
  - Required: True
- **description**
  - Description: What the tool does.
  - Type: string
  - Required: True

## FunctionTool
Extends BaseTool.

### Syntax
```yaml
type: function
name: <string>
description: <string>
module_path: <string>
function_name: <string>
```

### Properties
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

## MCP Tool Variants

### McpTypeStreamable
Configuration for HTTP-streaming MCP tools.

#### Syntax
```yaml
url: <string>
port: <int>
path: <string>  # default: "/"
```

#### Properties
- **url**: Base URL for the MCP server. (required)
- **port**: Port number. (required)
- **path**: URL path. Default "/". (optional)

### McpTypeStdio
Configuration for stdio-based MCP tools.

#### Syntax
```yaml
command: <string>
args:
  - <string>
  - <string>
# optional
env:
  KEY: VALUE
```

#### Properties
- **command**: Command to execute for the MCP server. (required)
- **args**: Command line arguments. (required)
- **env**: Environment variables. (optional)

### McpTool
Extends BaseTool.

#### Syntax
```yaml
type: mcp
name: <string>
description: <string>
# choose one of the following configs
mcp_config:  # McpTypeStreamable
  url: <string>
  port: <int>
  path: "/"
# OR
mcp_config:  # McpTypeStdio
  command: <string>
  args: [<string>, <string>]
  env: { KEY: VALUE }
```

#### Properties
- **mcp_config**
  - Description: Configuration (streamable HTTP or stdio) for the MCP tool.
  - Type: McpTypeStreamable | McpTypeStdio
  - Required: True

#### Example
```yaml
type: mcp
name: file_manager
description: Manage files via MCP
mcp_config:
  command: file-server
  args: ["--port", "8080"]
```
