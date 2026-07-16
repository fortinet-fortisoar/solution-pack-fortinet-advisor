| [Home](../README.md) |
|----------------------|

# AI Configurations

The **AI Configurations** section appears in the FortiSOAR **Settings** menu after an administrator [enables AI features](./setup.md#enable-ai-features). It provides the configuration layer that governs how AI agents analyze data, interact with external tools, and generate responses during investigations.

> [!NOTE]
> Review these configurations carefully before making changes. Incorrect modifications may affect AI investigation functionality. Fortinet recommends leaving default settings in place unless a specific customization is required.

For complete procedural detail on each section, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

## MCP Servers

Model Context Protocol (MCP) servers act as a secure communication bridge between the LLM and external tools, data sources, and APIs. AI agents use MCP servers to interact with external systems using natural language.

The following MCP servers are configured by default:

| MCP Server                        | Description                                                                                                                                                          |
|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **FortiSOAR Module Management**   | Enables AI agents to access FortiSOAR modules, retrieve schemas, and query module data.                                                                              |
| **FortiSOAR Playbook Management** | Enables AI agents to retrieve, execute, and monitor FortiSOAR playbooks. Playbooks can be tagged and exposed as tools.                                               |
| **SOC Framework**                 | Enables AI agents to perform security operations tasks such as retrieving alerts, fetching correlated alerts and indicators, enriching indicators, and hunting IOCs. |
| **Utility Tools**                 | Provides common helper functions, such as retrieving the current date and time, for general workflow tasks.                                                          |

You can create a custom MCP server to extend LLM capabilities using any configured connector, or connect to an external MCP server by providing its URL and authentication details.

> [!NOTE]
> To create an MCP server, users require at least Read permissions on the Security, Application, and Connector modules, and Create and Read permissions on MCP Configurations.

For full creation and connection procedures, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

## Prompts

AI agents use structured prompts to interact with the LLM. The **Prompts** page lists the predefined prompts used during investigations. Each prompt defines an agent's identity, capabilities, constraints, and operational behavior, and specifies the required response format.

Each prompt record includes:

| Field                      | Description                                                                                                                                                   |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Name**                   | The prompt name.                                                                                                                                              |
| **Description**            | A summary of the prompt's purpose.                                                                                                                            |
| **System Prompt Template** | Defines the agent's identity, core capabilities, and constraints. Read-only; cannot be modified.                                                              |
| **User Prompt Template**   | Contains the specific task, data, and context for a request. Uses `{{variable}}` placeholders that are replaced with actual values before the prompt is sent. |
| **Response Format**        | Specifies the required output format, such as a JSON object with predefined fields.                                                                           |

For details on viewing and using prompts, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

## Organizational Context

Organizational context provides AI agents with structured, predefined knowledge about your organization — including investigation procedures, roles, risk criteria, and environment-specific details. Agents reference this context during investigations to improve decision accuracy and ensure outputs align with organizational requirements.

Default organizational context records include:

| Context                           | Description                                                                                                                                                                          |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Account Lockout Investigation** | Helps agents determine whether an account lockout is caused by malicious activity (such as a brute-force attack) or a benign cause (such as user error or service misconfiguration). |
| **Organization Context**          | Defines organization-level risk context and business priorities, such as asset criticality classifications and threat impact thresholds.                                             |
| **Port Scanning Investigation**   | Supports agents in analyzing network scanning activity by evaluating source IP, target systems, ports, and scan patterns to determine whether behavior is legitimate or suspicious.  |

You can add custom organizational contexts to extend agent knowledge for your specific environment. For the full procedure, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

## Insights

Insights analyze data within FortiSOAR to surface actionable observations, patterns, and recommendations generated during investigations and response activities. They help identify risks, monitor performance, and highlight operational issues.

Insights are accessible via **AI** > **AI Insights** or **Dashboard** > **AI Insights** in the left navigation pane.

Each insight consists of three sections:

| Section    | Description                                                                              |
|------------|------------------------------------------------------------------------------------------|
| **Intent** | Defines the analysis objective and desired outcome.                                      |
| **Plan**   | Describes how the system will achieve the intent, expressed as a chain of logical steps. |
| **Result** | Displays the analysis output and recommended actions.                                    |

Insights run automatically on a defined schedule. From each insight card you can **Edit**, **Delete**, or click **Explore** to open the AI Assistant bot for follow-up analysis in context.

The **Insights** page in **Settings** > **AI Configurations** allows administrators to activate, deactivate, or delete insights. Deactivating an insight also deactivates its associated schedule. Deleting an insight removes it from the AI Insights dashboard.

For full procedures on creating, scheduling, and managing insights, refer to the [Administration Guide](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction).

---

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |
