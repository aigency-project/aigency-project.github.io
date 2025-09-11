---
title: Aigency:::Agent
linkTitle: Agent
type: docs
weight: 3
---

This resource defines the agent's core logic, model, instruction, skills, tools, and connections to remote agents.

## Syntax
```yaml
model: [AgentModel]
instruction: <string>
skills:
  - [Skill]
  - ...

# Optional
tools:
  - [Tool]
  - ...
remote_agents:
  - [RemoteAgent]
  - ...
```

## Properties
- **model**
  - Description: Configuration for the AI model to use.
  - Type: [AgentModel](/docs/aigency/agent/agent_model/)
  - Required: True

- **instruction**
  - Description: System instruction that defines the agent's behavior.
  - Type: string
  - Required: True

- **skills**
  - Description: List of skills the agent possesses.
  - Type: list of [Skill](/docs/skill/)
  - Required: True

- **tools**
  - Description: List of tools available to the agent.
  - Type: list of [Tool](/docs/tools/)
  - Required: False

- **remote_agents**
  - Description: List of remote agents this agent can communicate with.
  - Type: list of [RemoteAgent](/docs/remote_agent/)
  - Required: False

## Example
```yaml
model:
  name: gemini-2.0-flash
instruction: |
  """
  You are a simple "Hello World" type agent designed to demonstrate the basic structure of agents in this project.

  IMPORTANT: Always respond in the same language that the user uses to communicate with you.
  """
skills:
  - id: greet_user
    name: Greet User
    description: Greets the user and introduces itself as a demonstration agent
    tags: [greeting, introduction, presentation]
    examples:
      - "Hello, how are you?"
      - "What is an agent?"
  - id: math_operations
    name: Mathematical Operations
    description: Performs basic mathematical operations like addition or subtraction using tools
    tags: [mathematics, addition, subtraction, tools, demonstration]
    examples:
      - "Add 5 and 3"

# Optional
tools:
  - type: function
    name: substraction_tool
    description: Performs subtraction of two numbers and returns the result
    module_path: demo_tools
    function_name: substraction_tool
  - type: mcp
    name: calculator
    description: Performs addition of two numbers and returns the result
    mcp_config:
      url: hello-world-mcp-server
      port: 8080
      path: /mcp/
remote_agents:
  - name: data_processor
    host: agent-data-processor
    port: 8080
```
