---
title: The Gossip Aigent
type: docs
weight: 2
next: /get_started/demos/detective_aigency
prev: /get_started/demos
---

This example demonstrates a friendly and entertaining conversational agent built with the Aigency framework. The Gossip Agent is designed to share interesting stories, rumors, and engage in entertaining, multilingual conversations.

## Use Cases
The Gossip Agent is perfect for lighthearted and engaging interactions.

{{< tabs items="Casual Conversation, Story Request, Using Tools" >}}
  {{< tab >}}
    ### Casual Conversation
    You can chat with the agent about your day or any topic.
    **Example Prompt:**
    ```
    ‘Hello! How's everything today? It's been a crazy day at work.’
    ```
    **Agent's Likely Response:**
    ‘Hello! How exciting that you've written to me! Tell me everything, don't leave out a single detail. Sometimes the craziest days bring the best stories. Did anything interesting happen?’
  {{< /tab >}}
  {{< tab >}}
    ### Story & Gossip Request
    Directly ask the agent for an interesting story or some fictional gossip.
    **Example Prompt:**
    ```
    "Tell me some gossip you've heard recently."
    ```
    **Agent's Likely Response:**
    "Oh, you won't believe what I 'heard'! They say the famously minimalist artist, Silas Croft, has a secret room in his house filled with nothing but rubber ducks. Thousands of them! Can you imagine?"
  {{< /tab >}}
  {{< tab >}}
    ### Using Tools for Inspiration
    If the conversation lulls, you can ask the agent to generate a new topic.
    **Example Prompt:**
    ```
    "I'm not sure what to talk about. Can you generate a topic for us?"
    ```
    **Agent's Likely Response:**
    *(The agent uses its `generate_gossip_topic` tool)*
    "Of course! Let me see... Ooh, how about this: 'A celebrity chef was secretly replaced by a hyper-intelligent raccoon, and no one has noticed because the food is even better.' What do you think happened to the original chef?"
  {{< /tab >}}
{{< /tabs >}}

----

## System Architecture

The system consists of a single core agent supported by a specialized MCP (Model Context Protocol) service that provides tools for generating creative content.

### The Gossip Agent
This agent is the heart of the experience, designed to be a charismatic and endlessly curious conversationalist. Its primary role is to entertain and engage the user.

**Key Responsibilities:**
1.  Greet users enthusiastically and maintain a lively conversation.
2.  Respond in the same language the user is writing in.
3.  Share entertaining fictional stories and "rumors".
4.  Use its tools to generate random topics, facts, and conversation starters.
5.  Ensure all interactions remain harmless, playful, and respectful.

{{< callout type="important" icon="chat">}}
**Specialization**: Entertaining conversations, storytelling, and multilingual support.
{{< /callout >}}
{{< callout type="info" icon="puzzle" >}}
**MCP Tools**: `generate_gossip_topic`, `random_fact_generator`, `create_conversation_starter`.
{{< /callout >}}
{{< callout  icon="identification" >}}
**Skills**: `Greet and Engage`, `Share Stories`, `Generate Topics`.
{{< /callout >}}

### Diagram of the System
<image src="/images/gossip-agent_diagram.png" alt="Diagram of the Gossip Agent System">

---
## How to Run

### Prerequisites

{{% steps %}}

### Install Docker and Docker Compose

Follow the instructions for your operating system to install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/).

### Download the Repository

```bash
git clone https://github.com/aigency-project/gossip-agent
```

### Configure your environment variables in a .env file in the project root:
Visit Google AI Studio to generate your Gemini API key, since this agent uses the gemini-2.0-flash model.

```Bash
GEMINI_API_KEY=your_gemini_api_key
```
{{% /steps %}}

### Execution
Run the following command from the gossip_agent directory:

```Bash
docker-compose up --build
```
### Access Ports
Once running, the services are available at these ports:

- **`Gossip Agent`**`: [http://localhost:8080](http://localhost:8080) (Main entry point)
- **`Gossip MCP Server`**`: [http://localhost:8081](http://localhost:8081) (Tool server, for internal use)
- **`Phoenix Observability`**`: [http://localhost:6006](http://localhost:6006)
- **`A2A Inspector`:** [http://localhost:6007](http://localhost:6007)

## Monitoring and Observability
- **Phoenix:** An observability dashboard is available at http://localhost:6006.
- **A2A Inspector:** Agent inspection tools can be found at http://localhost:6007.
- **Logs:** Each agent generates detailed logs for tracking and debugging.

## Extensibility
The system is designed to be easily expanded:

- **New Skills**: Add a Tell a Joke skill or a Share Celebrity News (fictional) skill.
- **New MCPs**: Integrate a service that generates fictional character backstories or a "rumor mill" that can chain related stories together.
- **New Personality Traits**: Modify the agent's main instruction to give it a different personality, such as a wise old storyteller or a futuristic news bot.

{{< callout type="info" title="Development Notes" >}}

The agent must always respond in the user's language. This is a core instruction.
The agent's personality is defined by its instruction prompt: friendly, chatty, and a bit dramatic.
The distinction between skills (agent's abilities) and tools (external services) is key to its modularity.
{{< /callout >}}

{{< callout type="warning" title="Content & Safety Considerations" >}}

All gossip and stories generated must be clearly fictional and harmless.
The agent is explicitly instructed never to share real personal information or harmful rumors.
Interactions should always maintain a playful, respectful, and positive tone.
The agent is designed to avoid mean-spirited content.
{{< /callout >}}