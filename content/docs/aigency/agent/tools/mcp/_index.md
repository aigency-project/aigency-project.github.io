---
title: Aigency::Agent::Tools::McpTool
linkTitle: McpTool
type: docs
weight: 1
prev: docs/aigency/agent/tools/
---

### McpTool
MCP (Model Context Protocol) based tools.

#### Syntax
```yaml
type: mcp
name: <string>
description: <string>
mcp_config:  [McpTypeStreamable] | [McpTypeStdio]
```

#### Properties
- **type**
  - Description: The type of tool.
  - Type: string
  - Required: True
  - Value: 
    - `mcp`
- **name**
  - Description: Name identifier for the tool.
  - Type: string
  - Required: True
- **description**
  - Description: What the tool does.
  - Type: string
  - Required: True
- **mcp_config**
  - Description: Configuration (streamable HTTP or stdio) for the MCP tool.
  - Type: [McpTypeStreamable](/docs/aigency/agent/tools/mcp/mcpstreamble/) | [McpTypeStdio](/docs/aigency/agent/tools/mcp/mcpstdio/)
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
