# What's New

> [!IMPORTANT]
> 
> FortiAI `v6.0.0` requires **FortiSOAR `v8.0.0` or later**. Deployments running an earlier version of FortiSOAR must upgrade before installing or upgrading to FortiAI `v6.0.0`.
> 

## Enhancements

### Agentic AI Support

FortiAI `v6.0.0` introduces agentic AI capabilities. A coordinated set of AI agents can autonomously plan and execute multi-step investigation workflows, query external data sources, correlate records, and produce structured investigation outputs — without requiring manual prompting at each step.

Refer to the individual AI agent documentation on [FortiSOAR Content Hub](https://fortisoar.contenthub.fortinet.com//list.html?contentType=ai_agent) for details.

### AI Investigation

**AI Investigation** is a new tab on the **Alert** detail page. It runs an automated investigation using a coordinated pipeline of AI agents — including hypothesis generation, investigation planning, data source querying, alert correlation, and summarization — and surfaces results directly in context.

### AI Insights Dashboard

The **AI Insights** dashboard aggregates AI-generated intelligence across alerts, cases, and indicators. It is accessible via **AI** > **AI Insights** or **Dashboard** > **AI Insights** in the left navigation pane.

### AI Configurations

A new **AI Configurations** section is available in the FortiSOAR **Settings** menu after an administrator enables AI features. It provides centralized configuration for the following:

- **MCP Servers**: Model Context Protocol servers that act as a communication bridge between the LLM and external tools, data sources, and APIs. Four MCP servers are configured by default: FortiSOAR Module Management, FortiSOAR Playbook Management, SOC Framework, and Utility Tools.
- **Prompts**: Structured prompt templates used by AI agents during investigations.
- **Organizational Context**: Predefined knowledge records that provide AI agents with organization-specific investigation procedures, risk criteria, and environment context.
- **Insights**: Scheduled AI-generated analyses surfaced on the AI Insights dashboard.

---

### Change in LLM Provider

The FortiSOAR AI uses the *Fortinet FortiAI* connector instead of OpenAI.

### Automatic IOC Masking and FortiAI Proxy

Before any data is sent to Fortinet FortiAI, FortiSOAR automatically masks sensitive information — including IP addresses, MAC addresses, and usernames — using the **IOC Masking** agent. All prompts pass through the Fortinet FortiAI proxy before reaching FortiAI services.

### FortiAI Installed by Default

The FortiAI solution pack is installed by default in FortiSOAR `v8.0.0`.
 