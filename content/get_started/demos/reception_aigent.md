---
title: Reception Aigent
type: docs
sidebar:
  open: true
weight: 1
next: /get_started/demos/gossip_agent
prev: /get_started/demos
---

This example demonstrates a simple, polite receptionist agent built with the Aigency framework. The Reception Aigent acts as a front-desk assistant: it greets users, asks brief clarifying questions, and conceptually routes them to the appropriate specialist in a detective agency. This agent runs without MCP services to remain lightweight and fast to deploy.

## Use Cases
The Reception Aigent is ideal for intake, triage, and routing.

{{< tabs items="Greeting & Triage, Clarifying Question, Provide Next Steps" >}}
  {{< tab >}}
    ### Greeting & Triage
    Welcome visitors and understand their needs in one or two sentences.
    **Example Prompt:**
    ```
    "Hello! I need help with a case involving stolen documents."
    ```
    **Agent's Likely Response:**
    "Welcome! I’m here to help. To route you properly, do you already have evidence (e.g., documents, fingerprints, video)? If yes, the Case Agent is best. 
    If the situation spans multiple teams, the Detective Manager can coordinate a broader investigation. Next steps: 1) Share key evidence, 2) Provide timeline, 3) Identify known witnesses."
  {{< /tab >}}
  {{< tab >}}
    ### Clarifying Question
    Ask just one concise question when the request is ambiguous.
    **Example Prompt:**
    ```
    "We suspect someone inside the company leaked information."
    ```
    **Agent's Likely Response:**
    "Understood. One quick question: do you need contacts or credibility checks from an informant network? If so, the Informant Agent is ideal. If you need evidence analysis and suspect profiling, the Case Agent will take the lead."
  {{< /tab >}}
  {{< tab >}}
    ### Provide Next Steps
    Offer a short checklist after routing.
    **Example Prompt:**
    ```
    "Who should handle a disappearance case with a few witnesses?"
    ```
    **Agent's Likely Response:**
    "Given there are witnesses and multiple leads, the Detective Manager can coordinate the case. Next steps: 1) Share a brief timeline, 2) List witnesses and locations, 3) Attach any media or documents you have."
  {{< /tab >}}
{{< /tabs >}}

----

## System Architecture

A single core agent with no MCP (Model Context Protocol) services.

### Reception Aigent
This agent serves as the front desk, ensuring users are welcomed and routed efficiently.

**Key Responsibilities:**
1. Greet users warmly and maintain a professional, friendly tone
2. Respond in the same language the user is writing in
3. Ask one concise clarifying question if needed
4. Explain which specialist best fits the case (Case Agent, Informant Agent, Detective Manager)
5. Provide brief and clear next steps

{{< callout type="important" icon="chat">}}
**Specialization**: Greeting, intake, triage, routing, and providing next steps.
{{< /callout >}}
{{< callout type="info" icon="puzzle" >}}
**MCP Tools**: None (intentionally no external MCP services).
{{< /callout >}}
{{< callout  icon="identification" >}}
**Skills**: `Greet and Route`, `Provide Next Steps`.
{{< /callout >}}

### Diagram of the System
<image src="/images/reception-agent_diagram.png" alt="Diagram of the Lone Aigent (Reception Agent) System">

---
## How to Run

### Prerequisites

{{% steps %}}

### Install Docker and Docker Compose

Follow the instructions for your operating system to install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/).

### Download the Repository

```bash
git clone https://github.com/aigency-project/demo-reception-agent
```

### Configure your environment variables in a .env file in the project root
Visit [Google AI Studio](https://aistudio.google.com/app/apikey) to generate your Gemini API key, since this agent uses the gemini-2.0-flash model.

```bash title=".env"
GEMINI_API_KEY=your_gemini_api_key
GOOGLE_GENAI_USE_VERTEXAI=FALSE
```
{{% /steps %}}

### Execution
Run the following command from the `reception_agent` directory:

```Bash
docker-compose up --build
```
### Access Ports
Once running, the services are available at these ports:

- **`Reception Agent`**: [http://localhost:8082](http://localhost:8082) (Main entry point)
- **`A2A Inspector`**: [http://localhost:6007](http://localhost:6007)

## Monitoring and Observability
- **A2A Inspector:** Agent inspection tools at http://localhost:6007.
- **Logs:** The agent generates logs for tracking and debugging.

## Extensibility
The system is designed to be easily expanded:

- **Add MCPs later**: Evidence database lookup, appointment scheduling, intake forms
- **New Skills**: Intake checklist builder, case summary generator
- **New Integrations**: Connect to the detective agency’s case management system

{{< callout type="info" title="Development Notes" >}}

The agent must always respond in the user's language. It prioritizes clarity and brevity and does not perform deep investigations. Designed to be simple and fast to deploy (no MCPs).
{{< /callout >}}

{{< callout type="warning" title="Content & Safety Considerations" >}}

Never request or reveal real personal information beyond what’s necessary for triage. Maintain a respectful, helpful, and professional tone. Keep guidance high-level and avoid sensitive details in public logs.
{{< /callout >}}