---
title: Tutorial, Creating Your First Agent with Aigency
type: docs
weight: 1
---


This tutorial will guide you step-by-step through creating and launching your first Aigency agent. An agent is fundamentally composed of two files that work together:

- `agent_config.yaml`: The configuration file that defines the personality, the AI model, and the capabilities (tools).

- `main.py`: The Python script that loads this configuration and starts the agent.

## 0. Prerequisites

- **Python**: Version 3.12 or higher.
- **Model credentials**: A valid API key for the model provider you choose. Aigency supports any model as long as the appropriate API key is configured. 

**Model provider example (Gemini)**: If you plan to use Google's Gemini (e.g., `gemini-2.0-flash`), visit [Google AI Studio](https://aistudio.google.com/app/apikey) to generate your Gemini API key. Create a `.env` file in the project root and add:

```bash title=".env"
# Do not commit this file to version control
GEMINI_API_KEY=your_gemini_api_key
GOOGLE_GENAI_USE_VERTEXAI=FALSE
```
- **Aigency library**: Install the Aigency Python package in your environment.

```bash
# Using pip
pip install aigency

# Or with uv
uv add aigency
```



## 1. The Definition: Building agent_config.yaml

The YAML file `agent_config.yaml` acts as the agent's "recipe", structuring all its logic and dependencies. It is composed of four main blocks, as defined in the [documentation](/docs/aigency/).

For our first demonstration agent, we will create a "Hello World Agent" example.

### 1.1 Metadata Block: The Agent's Identity

This block is mandatory and provides basic descriptive information.
For a complete reference of this block, see the documentation: [Metadata](/docs/aigency/metadata/).

<table>
  <thead>
    <tr>
      <th>Property</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>name</td>
      <td>Unique name for the agent. Underscore not allowed.</td>
    </tr>
    <tr>
      <td>description</td>
      <td>A brief explanation of its purpose.</td>
    </tr>
    <tr>
      <td>version</td>
      <td>Current version.</td>
    </tr>
  </tbody>
</table>

```yaml
metadata:
  name: hello_world_agent
  description: A simple agent to demonstrate the basic structure.
  version: 1.0.0
```
### 1.2 Service Block: Connectivity

This mandatory block defines how the agent connects to the world (URLs and data types it handles).
For a detailed reference of the service configuration, consult the documentation: [Service](/docs/aigency/service/), [Capabilities](/docs/aigency/service/capabilities/), and [Interface](/docs/aigency/service/interface/).

  </thead>
  <tbody>
    <tr>
      <td>url</td>
      <td>Internal or service URL.</td>
    </tr>
    <tr>
      <td>capabilities.streaming</td>
      <td>If the agent can stream responses in real-time (true).</td>
    </tr>
    <tr>
      <td>interface.default_input_modes</td>
      <td>Types of input it accepts (e.g., text).</td>
    </tr>
    <tr>
      <td>interface.default_output_modes</td>
      <td>Types of output it accepts (e.g., text).</td>
    </tr>
  </tbody>
  
</table>

```yaml
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
```

### 1.3 Agent Block: The Brain and Logic (The Key Component)

This mandatory block contains the core AI logic.

#### 1.3.1 Model Configuration and instruction (The System Prompt)

The instruction property is the system prompt, which defines the agent's personality, role, and behavior rules. It is key to directing its behavior.
For a detailed description of the agent schema and model options, see [Agent](/docs/aigency/agent/) and [Agent Model](/docs/aigency/agent/model/).

<table>
  <thead>
    <tr>
      <th>Property</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>model.name</td>
      <td>Identifier of the LLM model to use.</td>
    </tr>
    <tr>
      <td>instruction</td>
      <td>System prompt that defines role and behavior.</td>
    </tr>
  </tbody>
</table>

```yaml
agent:
  model:
    name: gemini-2.0-flash # Specifies the LLM model to use

  instruction: |
      """
      You are a simple "Hello World" agent designed to demonstrate the basic structure of agents in this project.
      
      **IMPORTANT: Always respond in the same language the user uses.**
      
      Your main function is to greet, introduce yourself, explain your purpose, and demonstrate the use of tools.
      
      [... additional behavior rules ...]
      """
```

#### 1.3.2 Defining skills (The Intentions)

Skills are the high-level user intentions that the agent must be able to recognize and handle. By defining examples, you help the model map user phrases to the correct skill.
For guidance on authoring skills, see [Agent Skills](/docs/aigency/agent/skills/).

<table>
  <thead>
    <tr>
      <th>Property</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>id</td>
      <td>Unique identifier for the skill.</td>
    </tr>
    <tr>
      <td>name</td>
      <td>Human-readable name of the skill.</td>
    </tr>
    <tr>
      <td>description</td>
      <td>Short explanation of the capability.</td>
    </tr>
    <tr>
      <td>tags</td>
      <td>Optional labels to help categorize the skill.</td>
    </tr>
    <tr>
      <td>examples</td>
      <td>Sample user phrases that should trigger this skill.</td>
    </tr>
  </tbody>
</table>

```yaml
  skills:
    - id: greet_user
      name: Greet User
      description: Greets the user and introduces itself.
      tags:
        - greeting
        - introduction
      examples:
        - "Hello, how are you?"
        - "Introduce yourself"
```

#### 1.3.3 Integrating tools (The Action Functions)

This capability allows an agent to call external functions or microservices during execution (for example, local Python functions or services connected via Model Context Protocol). To keep the “Hello World” tutorial focused and minimal, tools are not used here and this section is optional. When you are ready to extend your agent, define a `tools` block in your YAML and ensure the referenced modules or services are reachable. See the Demos and the main documentation for tool-enabled examples.
To learn how to enable and configure tools, see [Agent Tools](/docs/aigency/agent/tools/).

#### 1.3.4 Remote Agents (Optional)

Remote agents allow your agent to call other A2A agents over the network. This is optional and useful when composing capabilities across services. Declare remote agents under the `agent.remote_agents` list in your YAML.
To configure communication with other agents, see [RemoteAgent](/docs/aigency/agent/remotes/).

<table>
  <thead>
    <tr>
      <th>Property</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>name</td>
      <td>Name identifier for the remote agent.</td>
    </tr>
    <tr>
      <td>host</td>
      <td>Hostname or IP address of the remote agent.</td>
    </tr>
    <tr>
      <td>port</td>
      <td>Port number for the remote agent connection.</td>
    </tr>
  </tbody>
</table>

```yaml
remote_agents:
  - name: data_processor
    host: agent-data-processor
    port: 8080
```

Note: Ensure the `host` and `port` are reachable from where your agent runs (local/dev, container, or cluster). See full details in `Aigency::Agent::RemoteAgent` docs at `/docs/aigency/agent/remotes/`.

#### 1.4 Observability Block: Monitoring and Tracing (Optional)

This block is optional, but essential for monitoring and debugging agent behavior in production. Phoenix is currently the only supported observability tool.
For monitoring and tracing options, see [Observability](/docs/aigency/observability/) and [Monitoring](/docs/aigency/observability/monitoring/).

<table>
  <thead>
    <tr>
      <th>Property</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>monitoring.phoenix.host</td>
      <td>Hostname for the Phoenix server</td>
    </tr>
    <tr>
      <td>monitoring.phoenix.port</td>
      <td>Port for the Phoenix server</td>
    </tr>
  </tbody>
</table>

```yaml
observability:
  monitoring:
    phoenix:
      host: phoenix
      port: 6006
```

## 2. The Starting Point: The main.py Script

Once the agent is fully defined in agent_config.yaml, we need a Python script to load it and bring it online. This is the purpose of main.py.

### 2.1 The Launcher Code

Follow these steps to create `main.py`, then copy the code below:

1. In your project root, create (or open) the folder where your agent will live.
2. Ensure `agent_config.yaml` and `main.py` reside in the same directory.
3. Create a new file named `main.py`.
4. Paste the code below and save the file.

Tip: The script resolves the path to `agent_config.yaml` relative to the file location. If you keep the YAML elsewhere, update `config_path` accordingly.

Build `main.py` incrementally with these short steps:

1) Add imports and a logger

```python
import os
from aigency.aigency import open_aigency
from aigency.utils.logger import get_logger

logger = get_logger()
```

2) Define `main()` and resolve the configuration path

```python
def main():
    # Compute an absolute path so the script works no matter where it's run from
    config_path = os.path.join(os.path.dirname(os.path.abspath(__file__)), "agent_config.yaml")
```

3) Initialize the agent with `open_aigency()`

```python
    # Read the YAML, initialize the model and tools, and bring the agent online
    open_aigency(config_path=config_path)
```

4) Add the entry-point guard and graceful shutdown

```python
if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        logger.info("Application interrupted by user. Exiting...")
```

Reference (optional): Full `main.py`

```python
"""Main entry point for the reception agent."""

import os
from aigency.aigency import open_aigency
from aigency.utils.logger import get_logger

logger = get_logger()

def main():
    # 1. Constructs the path to the YAML configuration file.
    #    This ensures that Aigency finds the configuration regardless
    #    of where the script is executed.
    config_path = os.path.join(os.path.dirname(os.path.abspath(__file__)), "agent_config.yaml")
    
    # 2. Calls the key function of the Aigency library.
    #    This line reads the YAML, initializes the LLM, loads the tools
    #    and brings the agent online.
    open_aigency(config_path=config_path)

if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        logger.info("Application interrupted by user. Exiting...")
```

### 2.2 Key Explanation

In this entry point, `open_aigency(config_path=...)` acts as the orchestrator. It reads and validates the YAML, builds the agent according to the `metadata`, `service`, and `agent` blocks, initializes the selected model, registers the declared tools (local functions and MCP microservices), and brings the service online with the configured interface. When the optional `observability` block is present (e.g., Phoenix), it enables monitoring hooks so you can trace requests and tool calls.

This single call is provided for simplicity: instead of writing custom bootstrap code for configuration parsing, dependency wiring, and server startup, you keep `main.py` minimal and declarative. It also makes upgrades safer—improvements in the Aigency runtime are adopted without changes to your application code.

## 3. Running the Agent

With both files (agent_config.yaml and main.py) saved in your project directory, you can start your agent:
- Make sure your Python environment is active.
- Run the script from your terminal:

```bash
python main.py
```

The agent will start and be ready to receive requests at the URL you defined in the service block. Congratulations, you've created your first Aigency agent! 🎉

## 4. Consuming your agent

Use the A2A Inspector to interact with your agent via a simple web UI, without Docker.

- **What it is**: A web UI to connect to an A2A agent, view its Agent Card, and chat.
- **Repo**: https://github.com/a2aproject/a2a-inspector
- **Prerequisites** (Inspector): Python 3.10+, [uv](https://github.com/astral-sh/uv), Node.js and npm.

1) Clone and install dependencies

```bash
git clone https://github.com/a2aproject/a2a-inspector.git
cd a2a-inspector

# Backend deps
uv sync

# Frontend deps
cd frontend
npm install
cd ..
```

2) Run the Inspector (choose one)

- Convenience script (single terminal):

```bash
chmod +x scripts/run.sh
bash scripts/run.sh
```

- Manually (two terminals):

Terminal 1
```bash
cd frontend
npm run build -- --watch
```

Terminal 2
```bash
cd backend
uv run app.py
```

Open http://127.0.0.1:5001 in your browser.

3) Connect the Inspector to your agent

In the Inspector, enter your agent base URL (the `service.url` you configured). For a local agent, use:

```text
http://127.0.0.1:8080
```

4) Send a message

Try the example skills defined in your YAML:

```text
Hello, how are you?
```

<br>

<div style="display: flex; gap: 20px;">

<div style="border: 1px solid #ddd; padding: 20px; border-radius: 8px; flex: 1;">
<h3>🚀 Explore the Demos</h3>
<p>The best way to learn is by seeing code in action. Dive into our working examples to understand key use cases and get a solid starting point.</p>
<a href="/get_started/demos/"><strong>See Demos →</strong></a>
</div>

<div style="border: 1px solid #ddd; padding: 20px; border-radius: 8px; flex: 1;">
<h3>📚 Dive into the Documentation</h3>
<p>For an in-depth understanding of concepts, architecture, and configuration options, our main documentation is your best resource. You'll find all the theoretical information there.</p>
<a href="/docs/aigency"><strong>Go to Docs →</strong></a>
</div>

</div>

<br>
