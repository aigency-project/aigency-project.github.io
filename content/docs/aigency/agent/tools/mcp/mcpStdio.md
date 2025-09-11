---
title: Aigency::Agent::Tools::McpTool::McpTypeStdio
linkTitle: Stdio
type: docs
weight: 1
prev: /docs/aigency/agent/tools/mcp/
---

### McpTypeStdio
Configuration for stdio-based MCP tools.

#### Syntax
```yaml
command: <string>
args:
  - <string>
  - <string>
env:
  KEY: VALUE
```

#### Properties

- **command**
  - Description: Command to execute for the MCP server.
  - Type: string
  - Required: True
- **args**
  - Description: Command line arguments.
  - Type: list of string
  - Required: True
- **env**
  - Description: Environment variables.
  - Type: string
  - Required: False