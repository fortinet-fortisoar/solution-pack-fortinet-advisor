| [Home](../README.md) |
|---|

# Installation

The FortiAI solution pack is installed by default in FortiSOAR v8.0.0. If you need to reinstall it — for example, after an accidental removal or during troubleshooting — follow these steps:

1. In FortiSOAR, click **Content Hub** > **Discover**.
2. Search for **FortiAI** in the solution pack list.
3. Click the **FortiAI** solution pack card.
4. Click **Install** at the bottom of the screen.

## Prerequisites

### Dependent Solution Packs

| Name               | Type          | Version          | Purpose                             |
|--------------------|---------------|------------------|-------------------------------------|
| SOAR Framework     | Solution Pack | v4.0.0 and later | Required for case response modules. |
| Platform Utilities | Solution Pack | v1.0.0 and later | Required for the Key Store module.  |

### Access and Credentials

- A Fortinet FortiAI account. Refer to the [Fortinet FortiAI connector](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) documentation for details on obtaining and configuring API credentials.
- Access to supported Fortinet FortiAI LLM models.
- The following FortiSOAR permissions to use the FortiAI solution pack:
  - `Read` and `Usage` permissions on Widgets.
  - `Read` and `Execute` permissions on Playbooks.

### Enable AI Features

Before the FortiAI solution pack can be used, an administrator must enable AI features in FortiSOAR system settings.

1. Navigate to **Settings** <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-settings-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-settings-dark.svg"><img alt="" src="./res/icon-settings-dark.svg"></picture>.
2. Click the tab **FortiAI**.
3. Select the **Enable AI Features** toggle and click **Save**.
4. In the confirmation dialog, click **Acknowledge**.

Enabling AI features adds the **AI Configurations** section to the **Settings** menu. For details on configuring MCP servers, prompts, organizational context, and insights, see [AI Configurations](ai-configurations.md).

> [!NOTE]
> Token usage information is displayed on the FortiAI page. For details on token allocation and usage, refer to the [FortiAI topic](https://docs.fortinet.com/document/fortisoar/8.0.0/administration-guide/249178/introduction) in the Administration Guide.

### Advanced Development Features

To allow users to import or upload custom AI agents, create custom connectors, or create custom widgets, an administrator with **Security Update** permission must provide explicit consent through the **Advanced Development Features** tab.

> [!WARNING]
> These capabilities can introduce unverified code into the environment. Review the associated risks before enabling them.

**To enable import or upload of custom AI agents:**
1. Open the **Advanced Development Features** tab under **System Settings**.
2. Check *I understand the risks and accept responsibility for enabling Import/Export and Upload of AI Agent*.
3. Click **Submit**.

**To enable custom connector creation (BYOC):**
1. Check *I understand the risks and accept responsibility for enabling Custom Code Execution*.
2. Click **Submit**.

**To enable custom widget creation (BYOW):**
1. Check *I understand the risks and accept responsibility for enabling Build Your Own Widget (BYOW)*.
2. Click **Submit**.

To modify or remove any of these settings, click **Edit** on the Advanced Development Features page. To revert all settings, click **Reset to Default**.

> [!NOTE]
> Until administrator consent is granted, users will not see **Upload Connector**, **Upload Widget**, or **Upload AI Agent** options in the Content Hub **Manage** tab, and the **New Connector** and **New Widget** options will not appear under the **Create** tab.

### Administration Permissions

The following permissions are required for an administrator to run the [Configuration Wizard](#fortiai-configuration-wizard):

| Module         | Create                             | Read                               | Update                             | Delete                             | Other   |
|----------------|------------------------------------|------------------------------------|------------------------------------|------------------------------------|---------|
| Attachment     | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | —       |
| Connectors     | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | Execute |
| Content Hub    | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | —       |
| Files          | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | —       |
| Key Store      | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | —       |
| Playbooks      | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | Execute |
| Solution Packs | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | —       |
| Widgets        | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | Usage   |

### User Permissions

The following permissions are required for a user to interact with the **AI Assistant** bot. Users also require CRU (Create, Read, Update) permissions on the modules they are assigned to. For example, users managing alerts require CRU permissions on the **Alerts** module.

| Module      | Create                             | Read                               | Update                             | Delete                             | Other   |
|-------------|------------------------------------|------------------------------------|------------------------------------|------------------------------------|---------|
| Application | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | —       |
| Connectors  | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | Execute |
| Key Store   | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | —       |
| Playbooks   | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | Execute |
| Widgets     | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | Usage   |
| Files       | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | —       |

> [!NOTE]
> 
> The AI Assistant bot is available on any FortiSOAR module that contains records, such as Alerts, Cases, and Indicators. The bot remains accessible even when a module has no records.
> ![[Chat Assistant Icon](./res/icon-chat-assistant.svg)](./res/icon-chat-assistant.svg)


> [!NOTE]
> Users must have access to AI Agents, Widgets (Usage), Alerts, and Indicators to use the AI Investigation tab.

## Configuring Voice Input

**Microphone Setup**: Confirm that a microphone is connected and enabled. The browser must have permission to access the microphone.

### Best Practices for Voice Commands

- **Speak clearly**: Enunciate at a moderate pace.
- **One command at a time**: Issue a single command per input to ensure accurate processing.
- **Pause between commands**: Allow a brief pause between commands so FortiAI can process each one.

> [!NOTE]
> The voice input feature is not supported on Firefox. The `SpeechRecognition` API used by FortiAI is not compatible with Mozilla Firefox, so the microphone button does not appear when FortiSOAR is accessed via Firefox.

---

# Configuration

The **FortiAI** solution pack depends on the following connectors and widgets:

- **AI Assistant Utils** connector — handles communication between FortiSOAR and the Fortinet FortiAI LLM. This connector does not require a separate configuration. See the [AI Assistant Utils connector](https://docs.fortinet.com/fortisoar/connectors/ai-assitant-utils) documentation for details.
- **Fortinet FortiAI** connector — provides LLM responses to the AI Assistant bot and playbook generation features. See the [Fortinet FortiAI connector](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) documentation for configuration steps.

## FortiAI Configuration Wizard

The configuration wizard guides you through selecting an LLM reasoning tier, configuring the Fortinet FortiAI connector, and creating or updating the AI assistant. The assistant handles SOC conversations and playbook generation.

**To run the wizard:**

1. After [installation](#installation), click the **Configure** button on the FortiAI solution pack card.

   [![FortiAI Configuration](res/configure-button.png)](res/configure-button.png)

2. On the welcome screen, click **Let's Get Started**.

   [![FortiAI Configuration Wizard — Welcome](res/config-wizard-00.png)](res/config-wizard-00.png)

3. On the **Configuration** page, set the following fields:

   [![FortiAI Configuration Wizard — Configuration](res/config-wizard-01.png)](res/config-wizard-01.png)

   - **LLM Integration** — Select **Fortinet FortiAI** (default).
   - **Conversation Model** — Select the reasoning tier for SOC Assistant conversations:
     - **Low Reasoning** (default)
     - **High Reasoning**
   - **Playbook Generation Model** — Select the reasoning tier for playbook generation:
     - **Low Reasoning** (default)
     - **High Reasoning**
   - **Enable multi-user configuration** — When selected, FortiAI uses the connector configuration matching the logged-in user's login ID. When cleared, FortiAI uses the default connector configuration.

4. Click **Next**.

5. On the **Connect LLM** page, configure the **Fortinet FortiAI** connector using your API key. Refer to the [Fortinet FortiAI connector](https://docs.fortinet.com/fortisoar/connectors/fortinet-fortiai) documentation for configuration details.

   [![FortiAI Configuration Wizard — Connect LLM](res/config-wizard-02.png)](res/config-wizard-02.png)

6. Click **Finish** to complete the configuration.

> [!IMPORTANT]
> All configuration values are loaded from and saved to the **Key Store** record named `fortiai-configuration`. Navigate to *Security Operations <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-incident-response-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-incident-response-dark.svg"><img alt="" src="./res/icon-incident-response-dark.svg"></picture>*, *Orchestration* <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-orchestration-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-orchestration-dark.svg"><img alt="" src="./res/icon-orchestration-dark.svg"></picture>, *Resources* <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-resources-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-resources-dark.svg"><img alt="" src="./res/icon-resources-dark.svg"></picture>, or *AI* <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-ai-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-ai-dark.svg"><img alt="" src="./res/icon-ai-dark.svg"></picture> in the navigation menu to begin interacting with the AI feature.

The playbook developer assistant icon appears you launch the playbook designer:

![[Chat Assistant Icon](./res/icon-playbook-developer-assistant.svg)](./res/icon-playbook-developer-assistant.svg)

---

## Next Steps

| [Usage](usage.md) | [AI Configurations](ai-configurations.md) | [Contents](contents.md) |
|-------------------|-------------------------------------------|-------------------------|
