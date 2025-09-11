---
title: Aigency::Agent::Config
next: first-page
---

This resource defines the root configuration for an Aigency agent. It structures and validates all aspects of the agent's setup, including metadata, service settings, agent logic, and observability configurations.

## Syntax
To declare this resource in a Hextra template, use the following syntax:
```yaml
metadata: [Metadata](http://www.google.es)

service:

agent:

observability:

```
## Properties
The properties section of the Hextra::Agent::Config resource accepts the following attributes:

### metadata
- **Description:** Descriptive information about the agent.
- **Type:** [Metadata]().
- **Required values:** True

### service
- **Description:** Network and communication configuration for the agent. 
- **Type:** [Service]().
- **Required:** True

### agent
- **Description:** The core agent logic, model, and capabilities.
- **Type:** [Agent]().
- **Required:** True

### observability
- **Description:** Settings for monitoring and observability of the agent.
- **Type:** [Observability]().
- **Required:** False

## Example
```yaml
metadata:
  name: hello_world_agent
  description: A simple "Hello World" type agent to demonstrate the basic structure of agents in the project.
  version: 1.0.0

service:
  url: http://hello-world-agent:8080
  capabilities:
    streaming: true
  interface:
    default_input_modes:
      - text
      - text/plain
    default_output_modes:
      - text
      - text/plain

agent:
  model:
    name: gemini-2.0-flash

  instruction: |
      """
      You are a simple "Hello World" type agent designed to demonstrate the basic structure of agents in this project.
      
      **IMPORTANT: Always respond in the same language that the user uses to communicate with you.** If they write in Spanish, respond in Spanish. If they write in English, respond in English. If they write in any other language, respond in that language.
      
      Your main function is to greet the user and provide basic information about how agents work in this ecosystem.
      
      When a user sends you a message, you should:
      
      1. **Greet cordially** the user in their language.
      2. **Introduce yourself** as a demonstration agent.
      3. **Briefly explain** your purpose (demonstrate the basic structure of an agent).
      4. **Provide information** about the project structure and how to create new agents.
      5. **Demonstrate tool usage** when the user requests it.
      6. **Perform basic calculations using the available tools**.
      
      You have access to the following tools that you can use when appropriate:
      
      - **substraction_tool**: Performs subtraction of two numbers and returns the result.
      - **add_tool**: Adds two integers.
      
      Maintain a friendly and didactic tone, as your purpose is to help users understand how agents and tools work in this system. Remember to always match the user's language in your responses.
      """

  skills:
    - id: greet_user
      name: Greet User
      description: Greets the user and introduces itself as a demonstration agent
      tags:
        - greeting
        - introduction
        - presentation
      examples:
        - "Hello, how are you?"
        - "What is an agent?"
        - "Introduce yourself"

    - id: explain_project
      name: Explain Project Structure
      description: Explains the basic structure of the project and how agents work
      tags:
        - structure
        - project
        - explanation
        - tutorial
      examples:
        - "How does this project work?"
        - "Explain the agent structure to me"
        - "How can I create my own agent?"
        
    - id: math_operations
      name: Mathematical Operations
      description: Performs basic mathematical operations like addition or subtraction using tools
      tags:
        - mathematics
        - addition
        - subtraction
        - tools
        - demonstration
      examples:
        - "Add 5 and 3"
        - "What is 10 plus 20?"
        - "Show how the addition tool works"
        - "Subtract 5 and 3"
        - "What is 10 minus 20?"
        - "Show how the subtraction tool works"

  tools:
    - type: function
      name: substraction_tool
      description: Performs substraction of two numbers and returns the result
      module_path: demo_tools
      function_name: substraction_tool
    - type: mcp
      name: calculator
      description: Performs addition of two numbers and returns the result
      mcp_config:
          url: hello-world-mcp-server
          port: 8080
          path: /mcp/

observability:
  monitoring:
    phoenix:
      host: phoenix
      port: 6006
```
