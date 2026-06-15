| [Home](../README.md) |
|---|

# Contents

The **FortiAI** solution pack contains the following resources.

## Connectors

| Name               | Description                                                                                                                 |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------|
| AI Assistant Utils | Provides helper methods for content generation and acts as the intermediary between FortiSOAR and the Fortinet FortiAI LLM. |
| Fortinet FortiAI   | Provides the Fortinet FortiAI models used as the backing LLM.                                                               |

## Widgets

| Name                         | Description                                                    |
|------------------------------|----------------------------------------------------------------|
| AI Assistant                 | Adds the FortiAI bot to the FortiSOAR user interface.          |
| FortiAI Configuration Wizard | Launches the setup wizard for configuring the LLM integration. |
| AI Investigation Overview    |                                                                |
| AI Configuration             |                                                                |
| AI Investigation Details     |                                                                |
| AI Insight Cards             |                                                                |


## Attachments

| Name                                 | Description                                                        |
|--------------------------------------|--------------------------------------------------------------------|
| FortiAI - SOC Assistant Instructions | Contains the instruction set used to initialize the SOC Assistant. |

## Key Store — Record Sets

| Name                       | Description                                                                               |
|----------------------------|-------------------------------------------------------------------------------------------|
| `fortiai-configurations`   | Contains keys such as `llmIntegrations`, `llmIntegrationToUse`, and `llmIntegrationData`. |
| `fortiai-static-questions` | Contains module-specific preset questions and the associated fields of interest.          |

## Key Store Contents

### `fortiai-configurations`

- **`llmIntegrations`**: Defines the LLM integration. Defaults to Fortinet FortiAI.
  - `name`: LLM integration name as defined in the connector. Default: `fortinet-fortiai`.
  - `title`: LLM integration display title. Default: `Fortinet FortiAI`.
  - `modelList`: List of available LLM models. Refer to the [Fortinet FortiAI connector](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) documentation for supported model names.
- `isMultiConfigAvailable`: Controls whether multiple connector configurations are available. Default: `false`.
- `pastConversationMsgLimit`: Maximum number of messages loaded in the conversation window on login. Default: `20`.

> [!NOTE]
> The raw configuration file is available at [`llm-configuration.json`](res/llm-configuration.json).

### `fortiai-static-questions`

- **`modules`**: Parent object containing the list of modules and their associated preset questions.
  - *Module API Name*: Specify the API name of the module on which to display preset questions. By default, `alerts`, `incidents`, and `indicators` are configured.
    - **`questions`**: Array of question objects, each containing:
      - `question`: Display name of the question (for example, *Generate Alert Summary*).
      - `description`: Description shown in the chatbot interface.
      - `enable`: Set to `true` or `false` to control whether the question is rendered.
    - **`fieldsOfInterest`**: Array of field API names used to build context for the preset questions. Each module may define different fields of interest.

> [!NOTE]
> To add a preset question for a module, add a question object with `description` and `enable` fields under the module's API name. A sample [Question JSON](res/question-sample.json) is available for reference.

## Playbook Collection

### 10 - SP - FortiAI

| Playbook Name                       | Description                                                                         |
|-------------------------------------|-------------------------------------------------------------------------------------|
| Clear Assistant Metadata            | Clears assistant metadata from the Integration Cache for the configured GenAI type. |
| Get Playbook Step Suggestion        | Suggests playbook steps based on a user query.                                      |
| Get Playbook Step Suggestion (Loop) | Suggests playbook steps based on a user query, iterating in a loop.                 |
| Get Playbook Block Suggestion       | Generates a playbook block to perform actions based on user requirements.           |
| > Get LLM Response                  | Reference playbook for obtaining a response from the LLM.                           |
| > Get LLM Configuration             | Retrieves the LLM configuration based on the `isMultiConfigAvailable` key.          |
|Alert - Escalate To Incident (Referenced)|Creates a new incident with the given inputs and links the alert(s) to the newly created Incident.|

### 10 - AI Utilities



### 10 - Knowledge Base Update



> [!WARNING]
> 
> Clone playbooks before customizing them to avoid data loss during solution pack upgrades.
> 

## AI Agents

FortiAI v6.0.0 introduces agentic AI support. Each AI agent is delivered as a separate solution pack and is documented individually. The following agents are available:

| Agent Name                                    | Description |
|-----------------------------------------------|-------------|
| AI Agent: IOC Masking                         |             |
| AI Agent: Alert Investigation                 |             |
| AI Agent: Investigation Hypothesis Generation |             |
| AI Agent: Investigation Planner               |             |
| AI Agent: Investigation Summarization         |             |
| AI Agent: Alert Correlation                   |             |
| AI Agent: Threat Intelligence Provider        |             |
| AI Agent: Query SIEM                          |             |
| AI Agent: FortiSOAR Data Access               |             |
| AI Agent: ITSM Context Provider               |             |
| AI Agent: Query Endpoint                      |             |
| AI Agent: Organization Context Provider       |             |
| AI Agent: Identity Context Provider           |             |
| AI Agent: Asset Context Provider              |             |
| AI Agent: Chat Assistant                      |             |
| AI Agent: Metric Computation                  |             |
| AI Agent: Task Planner                        |             |
| AI Agent: Impact Analysis                     |             |
| AI Agent: Summary                             |             |

---

## Next Steps

| [Installation](setup.md#installation) | [Configuration](setup.md#configuration) | [Usage](usage.md) |
|---------------------------------------|-----------------------------------------|-------------------|
