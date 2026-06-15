# What's New

> [!IMPORTANT]
> 
> FortiAI v6.0.0 requires **FortiSOAR v8.0.0 or later**. Deployments running an earlier version of FortiSOAR must upgrade before installing or upgrading to FortiAI v6.0.0.
> 

## Enhancements

### Agentic AI Support

FortiAI v6.0.0 introduces agentic AI capabilities. A coordinated set of AI agents can autonomously plan and execute multi-step investigation workflows, query external data sources, correlate records, and produce structured investigation outputs — without requiring manual prompting at each step.

Each AI agent is also available separately on Content Hub. The following agents are available in this release:

| AI Agent                                      |
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

Refer to the individual AI agent documentation for prerequisites, configuration details, and usage.

### AI Investigation

**AI Investigation** is a new tab on the **Alert** detail page. It runs an automated investigation using a coordinated pipeline of AI agents — including hypothesis generation, investigation planning, data source querying, alert correlation, and summarization — and surfaces results directly in context.

Investigation output includes:

- **Hypotheses**: Five competing classifications (Benign, False Positive, Malicious, Suspicious, Inconclusive) with supporting and weakening evidence and mapped MITRE ATT&CK tactics and techniques.
- **Verdict**: A structured summary with three tabs — **Highlights**, **Key Findings**, and **Next Steps**.
- **Re-investigate**: Reruns the investigation after configuration changes or new data is available.

For details, see [AI Investigation](docs/usage.md#ai-investigation).

### AI Configurations

A new **AI Configurations** section is available in the FortiSOAR **Settings** menu after an administrator enables AI features. It provides centralized configuration for the following:

- **MCP Servers**: Model Context Protocol servers that act as a communication bridge between the LLM and external tools, data sources, and APIs. Four MCP servers are configured by default: FortiSOAR Module Management, FortiSOAR Playbook Management, SOC Framework, and Utility Tools.
- **Prompts**: Structured prompt templates used by AI agents during investigations.
- **Organizational Context**: Predefined knowledge records that provide AI agents with organization-specific investigation procedures, risk criteria, and environment context.
- **Insights**: Scheduled AI-generated analyses surfaced on the AI Insights dashboard.

For details, see [AI Configurations](docs/ai-configurations.md).

### AI Insights Dashboard

The **AI Insights** dashboard aggregates AI-generated intelligence across alerts, cases, and indicators. It is accessible via **AI** > **AI Insights** or **Dashboard** > **AI Insights** in the left navigation pane.

---

## Enhancements

### Fortinet FortiAI Replaces OpenAI as the Backing LLM

The OpenAI connector has been replaced by the **Fortinet FortiAI** connector. The **AI Assistant Utils** connector continues to act as the intermediary between FortiSOAR and the LLM. Existing configurations using the OpenAI connector are not migrated automatically; the configuration wizard must be rerun after upgrading.

### LLM Configuration: Reasoning Tiers

Named model strings (for example, `gpt-4o-mini`) have been replaced by two reasoning tiers selectable in the configuration wizard:

| Tier | Use Case |
|---|---|
| **Low Reasoning** | Default. Suitable for most SOC Assistant and playbook generation tasks. |
| **High Reasoning** | For complex investigations and tasks that benefit from deeper reasoning. |

Separate reasoning tiers can be configured for the SOC Assistant and for playbook generation.

### Automatic IOC Masking and FortiAI Proxy

Before any data is sent to Fortinet FortiAI, FortiSOAR automatically masks sensitive information — including IP addresses, MAC addresses, and usernames — using the **AI Agent: IOC Masking** agent. All prompts pass through the Fortinet FortiAI proxy before reaching FortiAI services.

### FortiAI Installed by Default

The FortiAI solution pack is installed by default in FortiSOAR v8.0.0. Manual installation from the Content Hub is required only for reinstallation scenarios such as accidental removal or troubleshooting.

### Enable AI Features Prerequisite

Before the FortiAI solution pack can be used, an administrator must explicitly enable AI features via **System Configuration and Management** > **System Settings** > **FortiAI** > **Enable AI Features**. Enabling this setting also activates the **AI Configurations** section in the Settings menu.

### AI Navigation Menu

A dedicated **AI** entry has been added to the FortiSOAR left navigation pane, providing direct access to **AI** > **AI Agents** and **AI** > **AI Insights**.

### Advanced Development Features

Administrators with **Security Update** permission can now grant explicit consent for importing custom AI agents, creating custom connectors (BYOC), and creating custom widgets (BYOW) via **Advanced Development Features** in System Settings.

## Known Issues

- Connector generation does not support file attachments (PDF, Swagger specifications, Postman collections) when using the Fortinet FortiAI connector. This is a server-side limitation.

As a workaround, you can provide API details inline, through chat, as `curl` commands or JSON request/response structures. 

---

*For the full list of changes, refer to the [documentation](README.md).*
