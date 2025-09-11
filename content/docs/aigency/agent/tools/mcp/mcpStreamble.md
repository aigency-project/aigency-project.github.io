---
title: Aigency::Agent::Tools::McpTool::McpTypeStreamable
linkTitle: Streamable
prev: /docs/aigency/agent/tools/mcp/
type: docs
weight: 2
---

### McpTypeStreamable
Configuration for HTTP-streaming MCP tools.

#### Syntax
```yaml
url: <string>
port: <int>
path: <string>  # default: "/"
```

#### Properties

- **url**
  - Description: Base URL for the MCP server.
  - Type: string
  - Required: True
- **port**
  - Description: Port number.
  - Type: int
  - Required: True
- **path**
  - Description: URL path.
  - Type: string
  - Required: False
  - Default: /