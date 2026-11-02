| [Home](../README.md) |
|---|

# Contents

The **FortiAI** solution pack contains the following resources.

## Connectors

The solution pack ships the following connector.

| Name             | Description                                                   |
|------------------|---------------------------------------------------------------|
| Fortinet FortiAI | Provides the Fortinet FortiAI models used as the backing LLM. |

## Widgets

The solution pack ships the following widgets.

| Name                      | Description                                                                                                                |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------|
| AI Assistant              | Adds the FortiAI bot to the FortiSOAR user interface.                                                                      |
| AI Configuration          | Sets up the LLM integration and the reasoning level used across AI features.                                               |
| AI Investigation Overview | Shows the AI verdict, summary, key findings, and highlighted features for an alert.                                        |
| AI Investigation Details  | Shows the detail of an AI investigation, including the AI summary.                                                         |
| AI Agent Traceability     | Shows every step of the agent run that produced a result, with its status, duration, input, output, and model information. |
| Insight Cards             | Presents insight data as cards.                                                                                            |

## Modules

The solution pack ships the following modules.

| Name                    | Description                                                                                   |
|-------------------------|-----------------------------------------------------------------------------------------------|
| Insights                | Scheduled analyses surfaced on the AI Insights dashboard.                                     |
| Insight Templates       | Reusable insight queries, each associated with a SOC role.                                    |
| Organizational Contexts | Knowledge records that give AI agents organization-specific procedures and environment context. |

## Picklists

The solution pack ships the following picklists.

| Name       | Values                                                                                     |
|------------|--------------------------------------------------------------------------------------------|
| AI Verdict | Not Investigated, Benign, Inconclusive, Suspicious, False Positive, Malicious, Pending      |
| SOC Role   | SOC Analyst, SOC Manager, Threat Analyst, Infrastructure Admin                              |

## Roles

The solution pack ships the following roles.

| Name                 | Description                                 |
|----------------------|---------------------------------------------|
| Agentic AI           | Manages required permission for Agentic AI. |
| Full App Permissions | Essentially the root user. Use carefully.   |

## Records

The solution pack ships the following record sets.

| Record set              | Count | Description                                                                   |
|-------------------------|:-----:|-------------------------------------------------------------------------------|
| Organizational Contexts |  58   | Investigation procedures, risk criteria, and environment context.             |
| Insight Templates       |  15   | Reusable insight queries for the AI Insights dashboard.                       |
| Attachments             |   1   | Contains the instructions used to create or update the SOC Assistant.         |
| Key Store               |   2   | Manages configurations and quick prompts that appear on module records.    |

## Key Store record sets

The solution pack ships the following Key Store records.

| Name                       | Description                                                                               |
|----------------------------|-------------------------------------------------------------------------------------------|
| `fortiai-configurations`   | Contains keys such as `llmIntegrations`, `llmIntegrationToUse`, and `llmIntegrationData`. |
| `fortiai-static-questions` | Contains module-specific quick prompts and the associated fields of interest.          |

## Key Store contents

The following sections describe the contents of each Key Store record.

### `fortiai-configurations`

This record defines the LLM integration and related display settings.

- **`llmIntegrations`**: Defines the LLM integration. Defaults to Fortinet FortiAI.
  - `name`: LLM integration name as defined in the connector. Default: `fortinet-fortiai-proxy`.
  - `title`: LLM integration display title. Default: `fortinet-fortiai-proxy`.
  - `modelList`: List of available LLM models. Refer to the [Fortinet FortiAI connector](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) documentation for supported model names.
- `isMultiConfigAvailable`: Controls whether multiple connector configurations are available. Default: `false`.
- `pastConversationMsgLimit`: Maximum number of messages loaded in the conversation window on login. Default: `20`.

> [!Note]
> The raw configuration file is available at [`llm-configuration.json`](./res/llm-configuration.json).

### `fortiai-static-questions`

This record defines the quick prompts shown for each module in the list view as well as the detailed view.

- **`modules`**: Parent object containing the list of modules and their associated quick prompts.
  - *Module API name*: Specify the API name of the module on which to display quick prompts. By default, `alerts`, `incidents`, and `indicators` are configured.
    - **`questions`**: Array of question objects shown in the AI chat window when a record in the module is open. Each question object contains:
      - `question`: Display name of the question, for example **Generate Alert Summary**.
      - `description`: Description shown in the chatbot interface.
      - `enabled`: Set to `true` or `false` to control whether the question is rendered.
    - **`listQuestions`**: Array of question objects shown on the module's list view. Each question object uses the same `question`, `description`, and `enabled` fields.
    - **`fieldsOfInterest`**: Array of field API names used to build context for the quick prompts. Each module may define different fields of interest.

> [!Note]
> To add a quick prompt for a module, add a question object with `question`, `description`, and `enabled` fields to the module's `questions` or `listQuestions` array. A sample [question JSON](./res/question-sample.json) file is available for reference.

## Playbook collections

The solution pack ships the following playbook collections.

### 10 - SP - FortiAI

This collection supports assistant and insight operations.

| Playbook name                         | Description                                                                          |
|---------------------------------------|--------------------------------------------------------------------------------------|
| Alert - Escalate To Case (Referenced) | Creates a case with the given inputs and links the alerts to the newly created case. |
| Trigger Insight                       | Scheduled playbook that triggers an insight.                                         |
| Get Assistant Details By LLM Type     | Gets assistant metadata and its details.                                             |
| Clear Assistant Metadata              | Clears the assistant metadata from the integration cache, based on the GenAI type.   |
| > Get OpenAI Assistant Details        | Gets assistant details from OpenAI.                                                  |

### 10 - Knowledge Base Update

This collection maintains the search index used by the Organization Context Provider agent.

| Playbook name                                 | Description                                                                      |
|-----------------------------------------------|----------------------------------------------------------------------------------|
| Create Organizational Contexts Index          | Creates the index of the record used by the Organization Context Provider agent. |
| Create Organizational Context Index on update | Updates the index record used by the Organization Context Provider agent.        |
| Delete Organizational Context Index           | Deletes the index of the record used by the Organization Context Provider agent. |

> [!Warning]
> Clone playbooks before customizing them to avoid data loss during solution pack upgrades.

## Post-installation playbooks

These playbooks run automatically after installation or upgrade.

| Playbook name                 | Description                                                                                             |
|-------------------------------|-----------------------------------------------------------------------------------------------------------|
| LLM Metadata Migration        | Migrates Key Store records to the Integration SDK and restructures LLM metadata during an upgrade.      |
| Create Index                  | Creates the index of records after installation.                                                         |
| Set FortiAI SP Configuration  | Updates the FortiAI configuration to configured.                                                         |

## AI agents

Each AI agent installs as separate content and is documented individually on [FortiSOAR Content Hub](https://fortisoar.contenthub.fortinet.com/list.html?contentType=ai_agent). The following agents are available.

| Agent name                                    |
|-----------------------------------------------|
| AI Agent: IOC Masking                         |
| AI Agent: Alert Investigation                 |
| AI Agent: Investigation Hypothesis Generation |
| AI Agent: Investigation Planner               |
| AI Agent: Investigation Summarization         |
| AI Agent: Alert Correlation                   |
| AI Agent: Threat Intelligence Provider        |
| AI Agent: Query SIEM                          |
| AI Agent: FortiSOAR Data Access               |
| AI Agent: ITSM Context Provider               |
| AI Agent: Query Endpoint                      |
| AI Agent: Organization Context Provider       |
| AI Agent: Identity Context Provider           |
| AI Agent: Asset Context Provider              |
| AI Agent: Chat Assistant                      |
| AI Agent: Metric Computation                  |
| AI Agent: Task Planner                        |
| AI Agent: Impact Analysis                     |
| AI Agent: Summary                             |
| AI Agent: Orchestrator                        |
| AI Agent: SOC Response Action                 |
| AI Agent: Connector Generation                |
| AI Agent: Playbook Generator                  |


## MCP servers

The solution pack ships the following MCP servers.

| Name                          | Description                                                                                                                                                |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FortiSOAR Module Management   | Enables AI agents to access available FortiSOAR modules, retrieve their schemas, and query records.                                                        |
| FortiSOAR Playbook Management | Enables AI agents to retrieve, run, and monitor FortiSOAR playbooks.                                                                                       |
| SOC Framework                 | Enables AI agents to perform SOC operations, such as retrieving alerts, fetching correlated alerts and indicators, enriching indicators, and hunting IOCs. |
| Utility Tools                 | Provides commonly used utility functions, such as retrieving the current date and time.                                                                    |


---

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- |