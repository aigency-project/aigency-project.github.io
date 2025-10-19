---
title: Detective Aigency
type: docs
weight: 3
next: /get_started/demos/archivist_aigency
prev: /get_started/demos
---

This example demonstrates a multi-agent system for a detective agency built with the Aigency framework. The system is composed of three specialized agents that work in coordination to solve complex cases.

## Use Cases
This system supports everything from simple inquiries to fully coordinated investigations.

{{< tabs items="Simple Investigation, Coordinated Investigation, Typical Workflows" >}}
  {{< tab >}}
    ### Direct Interaction with Agents
    You can interact directly with specialized agents for specific tasks.
    **With the Case Agent:**
    ```
    "Analyze the robbery case at 'The Diamond' jewelry store - evidence includes: fingerprints, security footage, and an eyewitness."
    ```
    **With the Informant Agent:**
    ```
    "Find informants specializing in jewelry heists in the downtown area."
    ```
  {{< /tab >}}
  {{< tab >}}
    ### Using the Detective Manager
    For complex cases, the Detective Manager orchestrates the entire investigation.
    **Example Prompt:**
    ```
    "Investigate the corporate fraud case at TechCorp - I need an analysis of financial evidence and contact with informants in the tech sector."
    ```
    The Detective Manager will automatically:
    1.  **Delegate** the evidence analysis to the `Case Agent`.
    2.  **Coordinate** with the `Informant Agent` to gather additional intel.
    3.  **Integrate** the results to provide a comprehensive investigation report.
  {{< /tab >}}
  {{< tab >}}
    ### Common Scenarios
    **Robbery Case:**
    1.  `Case Agent` analyzes physical and digital evidence.
    2.  `Informant Agent` contacts informants in the area.
    3.  `Detective Manager` coordinates the information to identify suspects.
    **Fraud Case:**
    1.  `Case Agent` examines financial documents and transaction patterns.
    2.  `Informant Agent` seeks contacts within the financial sector.
    3.  `Detective Manager` develops a comprehensive investigation strategy.
  {{< /tab >}}
{{< /tabs >}}

----

## System Architecture

The agency operates with three core agents, each with a distinct role, and two supporting MCP (Model Context Protocol) services.

### Specialized Agents
{{< tabs items="Detective Manager Agent, Case Agent, Informant Agent" >}}
   {{< tab >}}
    ### Lead Detective Orchestrator
    This agent is the brain of the operation. It doesn't investigate directly but coordinates the other agents to ensure the investigation proceeds efficiently.

    **Key Responsibilities:**
    1. Coordinates complex, multi-faceted investigations.
    2. Delegates specific tasks to specialized agents.
    3. Integrates information from all sources into a unified view.
    4. Manages the overall investigation workflow.

    {{< callout type="important" icon="chat">}}
    **Specialization**: Strategic orchestration and coordination.
    {{< /callout >}}
    {{< callout type="warning" icon="clipboard-list" >}}
    **Capabilities**: Intelligent delegation, results integration.
    {{< /callout >}}
    {{< callout  icon="identification" >}}
    **Skills**: Coordination of complex investigations, specialized delegation.
    {{< /callout >}}
  {{< /tab >}}
  {{< tab >}}
    ### Case Specialist Detective
    This agent is responsible for analyzing all tangible information in the case to build a solid foundation for the investigation.
    
    **Key Responsibilities:**
    1. Analyzes evidence and develops case theories.
    2. Creates detailed profiles of suspects.
    3. Generates investigation reports for the team.
    4. Manages and updates the status of cases.

    {{< callout type="important" icon="chat">}}
    **Specialization**: Forensic analysis, theory development, report creation.
    {{< /callout >}}
    {{< callout type="info" icon="puzzle" >}}
    **MCP Tools**: Case management, evidence analysis, reporting.
    {{< /callout >}}
    {{< callout  icon="identification" >}}
    **Skills**: Case analysis, evidence investigation, suspect profiling.
    {{< /callout >}}

    ### MCP (Model Context Protocol) Services
    -   **Case Management MCP**: Handles cases, evidence, and reports.

  {{< /tab >}}
  {{< tab >}}
    ### Informant Network Specialist
    Acts as the link to the outside world, managing a network of contacts to obtain information not found in official reports.

    **Key Responsibilities:**
    1. Manages the agency's network of informants.
    2. Schedules secure and discreet meetings.
    3. Evaluates the credibility of received information.
    4. Maintains a reliability record for informants.

    {{< callout type="important" icon="chat">}}
    **Specialization**: Contact network management, credibility assessment.
    {{< /callout >}}
    {{< callout type="info" icon="puzzle" >}}
    **MCP Tools**: Informant management, meeting scheduling.
    {{< /callout >}}
    {{< callout  icon="identification" >}}
    **Skills**: Informant management, meeting scheduling, network analysis.
    {{< /callout >}}

    ### MCP (Model Context Protocol) Services
    -   **Informant Management MCP**: Manages informants and their meetings.


  {{< /tab >}}

{{< /tabs >}}

### Diagram of the System
<image src="/images/detective_aigency_diagram.png" alt="Diagram of the System">

---
## How to Run

### Prerequisites

{{% steps %}}

### Install Docker and Docker Compose

Follow the instructions for your operating system to install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/).

### Download the Repository

```bash title=".env"
    git clone https://github.com/aigency-project/demo-detective-aigency
```
### Configure your environment variables in a `.env` file in the project root

Visit [Google AI Studio](https://aistudio.google.com/app/apikey) to generate your Gemini API key, since this agent uses the gemini-2.0-flash model.

```bash title=".env"
    GEMINI_API_KEY=your_gemini_api_key
    GOOGLE_GENAI_USE_VERTEXAI=FALSE
```

{{% /steps %}}

### Execution

Run the following command from the `detective_agency` directory:

```bash copy
docker-compose up --build
```

### Access Ports
Once running, the services are available at these ports:

- **`Detective Manager Agent`:** [http://localhost:8080](http://localhost:8080) (Main entry point)
- **`Case Agent`:** [http://localhost:8082](http://localhost:8082)
- **`Informant Agent`:** [http://localhost:8084](http://localhost:8084)
- **`Phoenix Observability`:** [http://localhost:6006](http://localhost:6006)
- **`A2A Inspector`:** [http://localhost:6007](http://localhost:6007)

## Monitoring and Observability
- **Phoenix:** An observability dashboard is available at http://localhost:6006.
- **A2A Inspector:** Agent inspection tools can be found at http://localhost:6007.
- **Logs:** Each agent generates detailed logs for tracking and debugging.

## Extensibility
The system is designed to be easily expanded:

- **New Agents:** Add a Forensics Agent, Cybersecurity Agent, or Legal Agent.
- **New MCPs:** Integrate a criminal database, surveillance system, or communications analysis service.
- **New Skills:** Implement DNA analysis, digital investigation, or social media analysis.

{{< callout type="info" title="Development Notes" >}}
Each agent maintains its specialization and does not perform tasks outside its domain.
The Detective Manager acts as an orchestrator without conducting direct investigations.
MCPs provide persistence and specialized tools.
The system is designed to be scalable and modular.
{{< /callout >}}

{{< callout type="warning" title="Security Considerations" >}}
Informants are handled using codes and key names.
Sensitive information is protected during exchanges between agents.
Meetings are scheduled in secure and discreet locations.
Logs do not contain personally identifiable information (PII).
{{< /callout >}}