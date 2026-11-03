# Release Information

- **Version**: 6.1.0
- **Certified**: Yes
- **Publisher**: Fortinet
- **Compatible Version**: FortiSOAR v8.0.1 and later
- [Release Notes](./release_notes.md)


## Overview

**FortiAI** is a context-aware AI security assistant integrated into FortiSOAR. It enables security analysts to interact with FortiSOAR using natural language for data analysis, threat identification, record management, and automation. FortiAI uses **Fortinet FortiAI** as its backing large language model (LLM), reached through the **Fortinet FortiAI** connector.

Version 6.1.0 adds traceability for AI agent runs, four AI agents, four MCP servers, reusable insight templates, quick prompts on module list views, and AI verdict and summary fields on the **Alert** record.

---

## Capabilities

FortiAI provides the following capabilities.

### AI Assistant bot

The **AI Assistant** bot is accessible globally within FortiSOAR and supports the following operations:

- **Record filtering**: Filter alerts, cases, or indicators by severity, status, date range, assigned user, and other field criteria.
- **Alert escalation**: Escalate an alert to a case using a natural language command.
- **War room setup**: Create a war room for a case to coordinate team response.
- **Jinja expression assistance**: Generate and debug Jinja expressions for use in playbooks.
- **Record operations**: Create, update, link, and filter records across FortiSOAR modules.
- **Indicator actions**: Block or enrich indicators using configured connectors.
- **Contextual questions**: Ask questions about the currently open record or module.
- **Planned multi-step requests**: Ask for a task that requires planning, such as following a standard operating procedure. For details, see [Advanced Usage](./docs/advanced-usage.md).

### AI Investigation

**AI Investigation** is a tab on the **Alert** detail page that provides an AI-driven investigation of the alert. It uses a coordinated set of AI agents to gather context, correlate related records, query threat intelligence, and produce an investigation summary, without requiring manual prompting.

Version 6.1.0 records the outcome of an investigation on the alert itself, in the **AI Verdict** and **AI Summary** fields.

### AI Agent Traceability

**AI Agent Traceability** shows every step of an agent run that produced a result, so an analyst can see how a conclusion was reached. For details, see [Using the AI Agent Traceability](./docs/ai-agent-traceability.md).

### AI Insights dashboard

The **AI Insights** dashboard surfaces aggregated metrics and AI-generated intelligence across alerts, cases, and indicators. Insight templates supplied with the solution pack provide reusable queries for common SOC roles.

### Playbook generation

FortiAI supports natural language playbook generation directly from the Playbook Designer:

- Generates playbook blocks with contextually appropriate steps.
- Automatically selects Jinja expressions for each step.
- Detects loop requirements for record traversal.

### Connector generation

FortiAI can generate a FortiSOAR connector from natural language descriptions and API specifications. Supported input formats are `curl` commands and JSON.

> [!Note]
> API specifications cannot be supplied as file attachments, such as PDF files, Swagger specifications, or Postman collections. Enter the specification in the chat instead, using `curl` commands or JSON.

---

## Data privacy notice

The FortiAI solution pack activates FortiSOAR AI features using Fortinet FortiAI entitlements, established through the Fortinet FortiAI connector. Before data is sent to Fortinet FortiAI, FortiSOAR automatically masks sensitive information, including IP addresses, MAC addresses, and other indicators of compromise. All prompts from FortiSOAR pass through the Fortinet FortiAI proxy, where additional security checks are performed to help protect your data. Fortinet FortiAI then processes the masked data and returns responses, which are displayed in FortiSOAR. Fortinet does not verify or correct these responses and has no responsibility for them.

Before using FortiAI, review the Fortinet FortiAI privacy policy to understand how your data may be used and protected. By continuing to use FortiAI, you acknowledge and agree to the terms outlined in that privacy policy.

For further questions or concerns about your privacy, refer to [Fortinet's privacy policy](https://www.fortinet.com/corporate/about-us/privacy).

---

## Additional resources

The following pages cover setup, configuration, and usage in detail.

- [Setup](./docs/setup.md)
- [Usage](./docs/usage.md)
- [Advanced Usage](./docs/advanced-usage.md)
- [AI Configurations](./docs/ai-configurations.md)
- [Using the AI Agent Traceability](./docs/ai-agent-traceability.md)
- [Prompt examples](./docs/prompt-examples.md)
- [Example: Building a connector](./docs/example-creating-connectors.md)
- [Example: Generating a playbook](./docs/example-generating-playbooks.md)
- [Troubleshooting](./docs/troubleshooting.md)

---

## Next Steps

| [Installation](./docs/setup.md#installation) | [Configuration](./docs/setup.md#configuration) | [Usage](./docs/usage.md) | [Contents](./docs/contents.md) |
|----------------------------------------------|------------------------------------------------|--------------------------|--------------------------------|