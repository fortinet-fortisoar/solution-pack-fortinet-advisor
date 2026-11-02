| [Home](../README.md) |
|----------------------|

# AI Configurations

The **AI Configurations** section appears in the FortiSOAR **Settings** menu after an administrator [enables AI features](./setup.md#enabling-ai-features). It provides the configuration layer that governs how AI agents analyze data, interact with external tools, and generate responses.

> [!Note]
> Review these configurations carefully before making changes. Incorrect modifications may affect AI investigation functionality. Fortinet recommends leaving default settings in place unless a specific customization is required.

For complete procedural detail on each section, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

## MCP Servers

Model Context Protocol (MCP) servers act as a secure communication bridge between the LLM and external tools, data sources, and APIs. AI agents use MCP servers to interact with external systems using natural language.

The following MCP servers are configured by default.

| MCP server                        | Description                                                                                                                                                          |
|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **FortiSOAR Module Management**   | Enables AI agents to access FortiSOAR modules, retrieve schemas, and query module data.                                                                              |
| **FortiSOAR Playbook Management** | Enables AI agents to retrieve, run, and monitor FortiSOAR playbooks. Playbooks can be tagged and exposed as tools.                                                   |
| **SOC Framework**                 | Enables AI agents to perform security operations tasks such as retrieving alerts, fetching correlated alerts and indicators, enriching indicators, and hunting IOCs. |
| **Utility Tools**                 | Provides common helper functions, such as retrieving the current date and time, for general workflow tasks.                                                          |

The tools each server exposes are discovered when the server connects, rather than fixed in the solution pack. To see the current tools for a server, open the server record and click **Test Connection**. The tools appear under **Discovered Capabilities**.

You can create a custom MCP server to extend LLM capabilities using any configured connector, or connect to an external MCP server by providing its URL and authentication details.

> [!Note]
> To create an MCP server, users require at least Read permissions on the Security, Application, and Connector modules, and Create and Read permissions on MCP Configurations.

For full creation and connection procedures, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

## Prompts

AI agents use structured prompts to interact with the LLM. The **Prompts** page lists the predefined prompts used during investigations. Each prompt defines the identity, capabilities, constraints, and operational behavior of an agent, and specifies the required response format.

Each prompt record includes the following fields.

| Field                      | Description                                                                                                                                                   |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Name**                   | The prompt name.                                                                                                                                              |
| **Description**            | A summary of the purpose of the prompt.                                                                                                                       |
| **System Prompt Template** | Defines the identity, core capabilities, and constraints of the agent. Read-only, and cannot be modified.                                                     |
| **User Prompt Template**   | Contains the specific task, data, and context for a request. Uses `{{variable}}` placeholders that are replaced with actual values before the prompt is sent. |
| **Response Format**        | Specifies the required output format, such as a JSON object with predefined fields.                                                                           |

For details on viewing and using prompts, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

## Organizational Context

Organizational context provides AI agents with structured, predefined knowledge about your organization, including investigation procedures, roles, risk criteria, and environment-specific details. Agents reference this context during investigations to improve decision accuracy and ensure outputs align with organizational requirements.

The solution pack ships 28 organizational context records, grouped into the following categories.

| Category          | Description                                                                                                        |
|-------------------|--------------------------------------------------------------------------------------------------------------------|
| Organization      | Organization-level context, such as working hours, maintenance windows, risk criteria, and network schemes.        |
| SecOps            | Roles and responsibilities within the security operations team.                                                    |
| Investigation SOP | Standard operating procedures for investigating specific activity, such as malware detection or data exfiltration. |
| Normalized schema | Field mappings that let agents read alert data consistently across sources.                                        |
| SecOps lifecycle  | Knowledge of FortiSOAR modules and how they are used across the response lifecycle.                                |
| Regex             | Extraction patterns used when masking indicators.                                                                  |

You can add custom organizational contexts to extend agent knowledge for your specific environment. For the full procedure, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

> [!Caution]
> An investigation SOP is a set of default steps, not a mandate, and an agent asks for approval before it performs a state-changing action that the analyst did not request. When you author an SOP that includes a remediation step, state the approval expectation in the procedure itself so reviewers can see it.

---

## Insights

Insights analyze data within FortiSOAR to surface actionable observations, patterns, and recommendations generated during investigations and response activities. They help identify risks, monitor performance, and highlight operational issues.

Insights are accessible from **AI** > **AI Insights** or **Dashboard** > **AI Insights** in the left navigation pane.

Each insight consists of three sections.

| Section    | Description                                                                          |
|------------|--------------------------------------------------------------------------------------|
| **Intent** | Defines the analysis objective and desired outcome.                                  |
| **Plan**   | Describes how the system achieves the intent, expressed as a chain of logical steps. |
| **Result** | Displays the analysis output and recommended actions.                                |

Insights run automatically on a defined schedule. From each insight card you can **Edit** or **Delete** the insight, or click **Explore** to open the AI Assistant bot for follow-up analysis in context.

The **Insights** page in **Settings** > **AI Configurations** allows administrators to activate, deactivate, or delete insights. Deactivating an insight also deactivates its associated schedule. Deleting an insight removes it from the AI Insights dashboard.

### Insight templates

Insight templates are reusable insight queries, each associated with a SOC role, so a new insight can start from a definition that already suits the reader. The solution pack ships three templates.

Each template carries the following fields.

| Field        | Description                                                                                              |
|--------------|----------------------------------------------------------------------------------------------------------|
| **Title**    | The template name.                                                                                       |
| **Query**    | The analysis the template performs.                                                                      |
| **Plan**     | The steps used to satisfy the query.                                                                     |
| **SOC Role** | The role the template is written for: SOC Analyst, SOC Manager, Threat Analyst, or Infrastructure Admin. |

For full procedures on creating, scheduling, and managing insights, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |