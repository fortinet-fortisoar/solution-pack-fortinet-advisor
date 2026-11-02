| Compatible Version         |
|----------------------------|
| FortiSOAR v8.0.1 and later |

# What's New

FortiAI `v6.1.0` adds traceability for AI agent runs, four AI agents, four MCP servers, reusable insight templates, quick prompts on module list views, and AI verdict and summary fields on the **Alert** record.

> [!Important]
> FortiAI `v6.1.0` requires FortiSOAR `v8.0.1` and later. Deployments running an earlier version of FortiSOAR must upgrade before installing or upgrading to FortiAI `v6.1.0`.

## Enhancements

This release includes the following enhancements.

### AI Agent Traceability

**AI Agent Traceability** shows every step of the agent run that produced a result. Open it from **AI Investigation Details** to review the run as an expandable list of steps, with the total number of steps and the total run time. Selecting a step shows its status, duration, input, and output, along with the model, provider, token usage, and MCP server used for that step.

For details, see [Using the AI Agent Traceability](./docs/ai-agent-traceability.md).

### AI verdict and summary on alerts

The **Alert** module now carries two AI fields that persist the outcome of an investigation:

- **AI Verdict**: The verdict reached for the alert. Values are **Not Investigated**, **Benign**, **Inconclusive**, **Suspicious**, **False Positive**, **Malicious**, and **Pending**.
- **AI Summary**: The summary produced for the alert.

### Insight templates

Insight templates provide reusable queries for the **AI Insights** dashboard, each associated with a SOC role. Supported roles are **SOC Analyst**, **SOC Manager**, **Threat Analyst**, and **Infrastructure Admin**.

Manage templates from **Settings** > **AI Configurations** > **Insights**. For details, see [AI Configurations](./docs/ai-configurations.md).

### Quick prompts on list views

The **Alert**, **Case**, and **Indicator** modules now show quick prompts on their list views, in addition to the quick prompts shown in the AI chat window when a record is open.

To change which questions appear, including the questions shown on list views, edit the `fortiai-static-questions` Key Store record. For details, see [Customizing quick prompts](./docs/advanced-usage.md#customizing-quick-prompts) in the Advanced Usage guide.

### New AI agents

This release adds the following AI agents:

- **Orchestrator**: Interprets a natural language request that requires planning, plans the work, and runs it. The **Chat Assistant** agent decides when to call it.
- **SOC Response Action**: Performs response and remediation actions, such as blocking an indicator or creating and updating a ticket in the connected ITSM system. It runs only as part of an Orchestrator plan.
- **Connector Generation**: Generates a FortiSOAR connector from a natural language description and API specification.
- **Playbook Generator**: Generates playbook content from a natural language description.

For agent details, refer to the individual AI agent documentation on [FortiSOAR Content Hub](https://fortisoar.contenthub.fortinet.com/list.html?contentType=ai_agent).

### New MCP servers

This release adds the following MCP servers.

- **FortiSOAR Module Management**: Enables AI agents to access available FortiSOAR modules, retrieve their schemas, and query records.
- **FortiSOAR Playbook Management**: Enables AI agents to retrieve, run, and monitor FortiSOAR playbooks.
- **SOC Framework**: Enables AI agents to perform SOC operations, such as retrieving alerts, fetching correlated alerts and indicators, enriching indicators, and hunting IOCs.
- **Utility Tools**: Provides commonly used utility functions, such as retrieving the current date and time.

### Approval before a state-changing action

Orchestrator asks for approval before it runs an action that changes state, when the analyst did not ask for that action directly. The plan pauses until the request is approved or denied.

### Upgrade migration

A post-installation playbook migrates existing Key Store records to the Integration SDK and restructures LLM metadata during an upgrade. No manual action is required.

---

## Changes

This release includes the following changes.

- **Chat Assistant** agent now supports copying conversations using a copy button.

- **AI Assistant Utils connector removed**: The **AI Assistant Utils** connector is no longer used and is not shipped with the solution pack. FortiSOAR reaches Fortinet FortiAI through the **Fortinet FortiAI** connector.

- **Alert escalation playbook renamed**: The **Alert - Escalate To Incident (Referenced)** playbook is renamed to **Alert - Escalate To Case (Referenced)**, to match the terminology used across FortiSOAR.

- **Voice input removed**: Voice input is no longer available. Commands that were previously issued by voice must be entered in the chat.

- **File attachment removed**: The option to attach a file is no longer available. Instructions or `curl` commands must be entered in the chat.