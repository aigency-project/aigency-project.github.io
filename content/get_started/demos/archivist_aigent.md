---
title: Archivist Aigent
type: docs
sidebar:
  open: true
weight: 4
next: /docs/aigency
prev: /get_started/demos/detective_aigency
---

This example demonstrates a specialized archivist agent built with the Aigency framework. The Archivist Aigent acts as an investigation case librarian: it queries a RAG (Retrieval-Augmented Generation) database with historical cases to provide relevant information, patterns, and precedents that can help in current investigations.

## Use Cases
The Archivist Aigent is ideal for precedent search, pattern analysis, and historical case consultation.

{{< tabs items="Similar Case Search, Pattern Analysis, Precedent Consultation" >}}
  {{< tab >}}
    ### Similar Case Search
    Finds historical cases with characteristics similar to the current case.
    **Example Query:**
    ```
    "Search for previous cases of corporate document theft involving internal employees."
    ```
    **Agent's Likely Response:**
    "I found 3 similar cases in the archives: Case #2019-045 (internal theft at tech company), Case #2021-112 (document leak by disgruntled employee), and Case #2020-089 (confidential information theft). Common patterns include: after-hours access, USB device usage, and economic motivation or personal revenge."
  {{< /tab >}}
  {{< tab >}}
    ### Pattern Analysis
    Identifies trends and recurring methods in historical cases.
    **Example Query:**
    ```
    "What behavioral patterns do missing person cases in urban areas show?"
    ```
    **Agent's Likely Response:**
    "Based on 15 archived urban disappearance cases, the most frequent patterns are: 72% occur between 6:00 PM-2:00 AM, 45% involve public transportation as the last known point, and 60% are resolved within the first 48 hours when there are witnesses. I recommend prioritizing security cameras at transportation stations."
  {{< /tab >}}
  {{< tab >}}
    ### Precedent Consultation
    Provides detailed information about specific cases and their resolutions.
    **Example Query:**
    ```
    "I need details on how financial fraud case #2018-234 was resolved."
    ```
    **Agent's Likely Response:**
    "Case #2018-234: Financial fraud resolved through bank transaction analysis and collaboration with financial institutions. Key methods: electronic transfer tracking, spending pattern analysis, and bank employee testimonies. Resolution time: 6 weeks. Crucial evidence: IP records and transaction geolocation."
  {{< /tab >}}
{{< /tabs >}}

----

## System Architecture

A central agent with MCP services for accessing the RAG database of historical cases.

### Archivist Aigent
This agent serves as the specialized librarian, providing intelligent access to historical cases and pattern analysis.

**Key Responsibilities:**
1. Query the RAG database with historical investigation cases
2. Identify patterns and trends in similar cases
3. Provide relevant historical context for current investigations
4. Suggest investigation methods based on previous successful cases
5. Maintain confidentiality and privacy of sensitive information

{{< callout type="important" icon="database">}}
**Specialization**: Archive consultation, pattern analysis, precedent search, and recommendations based on historical cases.
{{< /callout >}}
{{< callout type="info" icon="puzzle" >}}
**MCP Tools**: Historical cases RAG database, semantic search system.
{{< /callout >}}
{{< callout  icon="identification" >}}
**Skills**: `RAG Search`, `Pattern Analysis`, `Precedent Consultation`, `Historical Recommendations`.
{{< /callout >}}

### System Diagram
<image src="/images/archivist-agent_diagram.png" alt="Archivist Aigent System Diagram">

---
## How to Run

### Prerequisites

{{% steps %}}

### Install Docker and Docker Compose

Follow the instructions for your operating system to install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/).

### Download the Repository

```bash
git clone https://github.com/aigency-project/demo-archivist-agent
```

### Configure your environment variables in a .env file in the project root
Visit [Google AI Studio](https://aistudio.google.com/app/apikey) to generate your Gemini API key, since this agent uses the gemini-2.0-flash model.

```bash title=".env"
GEMINI_API_KEY=your_gemini_api_key
GOOGLE_GENAI_USE_VERTEXAI=FALSE
```
{{% /steps %}}

### Execution
Run the following command from the `archivist_agent` directory:

```Bash
docker-compose up --build
```
### Access Ports
Once running, the services are available at these ports:

- **`Archivist Agent`**: [http://localhost:8083](http://localhost:8083) (Main entry point)
- **`A2A Inspector`**: [http://localhost:6008](http://localhost:6008)

## Monitoring and Observability
- **A2A Inspector:** Agent inspection tools at http://localhost:6008.
- **Logs:** The agent generates logs for tracking and debugging.

## Extensibility
The system is designed to be easily expanded:

- **New Data Sources**: Integration with police files, forensic databases, judicial records
- **New Skills**: Temporal case analysis, pattern prediction, automatic report generation
- **New Integrations**: Connection with current case management systems, forensic analysis tools

{{< callout type="info" title="Development Notes" >}}

The agent must maintain case confidentiality and provide only relevant and anonymized information when necessary. Prioritizes search accuracy and relevance of historical results.
{{< /callout >}}

{{< callout type="warning" title="Content & Safety Considerations" >}}

Never reveal personally identifiable information from historical cases. Maintain confidentiality of sensitive data and ensure queries comply with privacy regulations. Provide only information necessary for the current investigation.
{{< /callout >}}