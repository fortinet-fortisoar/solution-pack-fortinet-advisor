# Release Information

- **Version**: 6.0.0
- **Certified**: Yes
- **Publisher**: Fortinet
- **Compatible Version**: FortiSOAR v8.0.0 and later
- [Release Notes](release_notes.md)


## Overview

**FortiAI** is a context-aware generative AI security assistant integrated into FortiSOAR. It enables security analysts to interact with FortiSOAR using natural language for data analysis, threat identification, record management, and automation. FortiAI uses **Fortinet FortiAI** as its backing large language model (LLM), communicating through the **AI Assistant Utils** connector.

Version 6.0.0 introduces **agentic AI** capabilities, enabling FortiAI to autonomously plan and execute multi-step investigation workflows using a suite of specialized AI agents. It also introduces **AI Investigation**, a new tab on the Alert detail page that surfaces AI-driven investigation results directly in context.

---

## Capabilities

### AI Assistant Bot

The **AI Assistant** bot is accessible globally within FortiSOAR and supports the following operations:

- **Record Filtering**: Filter alerts, cases, or indicators by severity, status, date range, assigned user, and other field criteria.
- **Voice Input**: Issue commands by voice using the built-in voice-to-text feature. Supported on all browsers except Firefox.
- **Alert Escalation**: Escalate an alert to a case via natural language command.
- **War Room Setup**: Create a war room for a case to coordinate team response.
- **Jinja Expression Assistance**: Generate and debug Jinja expressions for use in playbooks.
- **Record Operations**: Create, update, link, and filter records across FortiSOAR modules.
- **Indicator Actions**: Block or enrich indicators using configured connectors.
- **Contextual Q&A**: Ask questions about the currently open record or module.

### AI Investigation

**AI Investigation** is a tab on the **Alert** detail page that provides an AI-driven investigation of the alert. It uses a coordinated set of AI agents to gather context, correlate related records, query threat intelligence, and produce an investigation summary &ndash; without requiring manual prompting.

### AI Insights Dashboard

The **AI Insights** dashboard surfaces aggregated metrics and AI-generated intelligence across alerts, cases, and indicators.

### Playbook Generation

FortiAI supports natural language playbook generation directly from the Playbook Designer:

- Generates playbook blocks with contextually appropriate steps.
- Automatically selects Jinja expressions for each step.
- Detects loop requirements for record traversal.

### Connector Generation

FortiAI can generate a FortiSOAR connector from natural language descriptions and API specifications. Supported input formats include `curl` commands, JSON request/response structures, and file attachments (`.json`, `.yml`, `.txt`, `.pdf`, up to 100 MB).

---

## Data Privacy Notice

The FortiAI Solution Pack (SP) activates FortiSOAR's AI features using Fortinet FortiAI entitlements, established through the Fortinet FortiAI connector. Before data is sent to Fortinet FortiAI, FortiSOAR automatically masks sensitive information, including IP addresses, MAC addresses, and other IoCs. All prompts from FortiSOAR pass through the Fortinet FortiAI proxy, where additional security checks are performed to help protect your data. Fortinet FortiAI then processes the masked data and returns responses, which are displayed in FortiSOAR. Fortinet does not verify or correct these responses and has no responsibility for them.

Before using FortiAI, review Fortinet FortiAI's privacy policy to understand how your data may be used and protected. By continuing to use FortiAI, you acknowledge and agree to the terms outlined in that privacy policy.

For further questions or concerns about your privacy, refer to [Fortinet's privacy policy](https://www.fortinet.com/corporate/about-us/privacy).

---

## Additional Resources

- [Setup](docs/setup.md)
- [Advanced Usage](docs/advanced-usage.md)
- [AI Configurations](docs/ai-configurations.md)
- [Troubleshooting](docs/troubleshooting.md)
- [Prompts for filtering *alert* records](docs/prompts-for-filtering-alert-records.md)
- [Prompts for filtering *case* records](docs/prompts-for-filtering-case-records.md)
- [Prompts for filtering *indicator* records](docs/prompts-for-filtering-indicator-records.md)
- [Example: Building a connector](docs/example-creating-connectors.md)
- [Example: Generating a playbook](docs/example-generating-playbooks.md)

---

## Next Steps

| [Installation](docs/setup.md#installation) | [Configuration](docs/setup.md#configuration) | [Usage](docs/usage.md) | [Contents](docs/contents.md) |
|--------------------------------------------|----------------------------------------------|------------------------|------------------------------|
