|[Home](../README.md) |
|---------------------|

# Installation

1. To install a solution pack, click **Content Hub** > **Discover**.
2. From the list of solution pack that appears, search **FortiAI**.
3. Click the **FortiAI** solution pack card.
4. Click **Install** on the lower part of the screen to begin the installation.

## Prerequisites

The **FortiAI** solution pack depends on the following solution packs.

| Name               | Type          | Version          | Purpose                                |
|:-------------------|:--------------|:-----------------|:---------------------------------------|
| SOAR Framework     | Solution Pack | v3.0.0 and later | Required for incident response modules |
| Platform Utilities | Solution Pack | v1.0.0 and later | Required for the key store module      |

You must have the following access and credentials to use this solution pack:

- An OpenAI account and a valid project level API key to access the OpenAI APIs. For information refer to [API Keys](https://platform.openai.com/docs/api-reference/api-keys) section of the OpenAI documentation. Following are the **_minimum_** permissions that must be assigned to users on the OpenAI interface:

    - **Administrator**
        - Model - **Read**
        - Model Capabilities - **Write**
        - Assistant - **Write**
        - Threads - **Write**
        - Files - **Write**

    - **User**
        -  Model - **Read**
        - Model Capabilities - **Write**
        - Assistants - **Read**
        - Threads - **Write**
        - Files - **Write**

    - The user must be a member of the project whose Project ID is being used.

- Access to supported OpenAI LLM models as versions prior to *`GPT4`* do not generate responses as expected.

- To utilize the Fortinet Advisor solution pack, user must have the following access, along with other appropriate permissions:

    - `Read` and `Usage` permissions on Widgets
    - `Read` and `Execute` permissions on Playbooks

### Administration Permissions

The following permission allow an administrator to run the [configuration wizard](#fortiai-configuration-wizard):

| Module         | Create                             | Read                               | Update                             | Delete                             | Other   |
|:---------------|:-----------------------------------|:-----------------------------------|:-----------------------------------|:-----------------------------------|:--------|
| Attachment     | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | -       |
| Connectors     | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | Execute |
| Content Hub    | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | -       |
| Files          | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | -       |
| Key Store      | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | -       |
| Playbooks      | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | Execute |
| Solution Packs | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | -       |
| Widgets        | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | Usage   |

### User Permissions

The following permission allow a user to interact with the **FortiSOAR AI Assistant** bot. Apart from these, users needs CRU (create, read, and update) permissions on the modules they are assigned to work. For example: users need to be assigned CRU permissions for the **Alert** module for them to manage or take action on an alert.

| Module      | Create                             | Read                               | Update                             | Delete                             | Other   |
|:------------|:-----------------------------------|:-----------------------------------|:-----------------------------------|:-----------------------------------|:--------|
| Application | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | -       |
| Connectors  | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | Execute |
| Key Store   | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | -       |
| Playbooks   | ![No](./res/icon-close.svg)        | ![Yes](./res/icon-green-check.svg) | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | Execute |
| Widgets     | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | ![No](./res/icon-close.svg)        | Usage   |
| Files       | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | ![Yes](./res/icon-green-check.svg) | -       |

> [!Note]
> The **FortiSOAR AI Assistant** bot becomes available to interact on modules that contain records like Alerts, Indicators, or Incidents. The bot is still available to interact on all such modules even if there are no records present.

## Configuring Voice Support

**Microphone Setup**: Confirm that a functional microphone is connected and enabled. The browser must have permissions to access the microphone.

### Best Practices for Voice Commands

- **Speak Clearly**: Enunciate clearly and at a moderate pace.
- **One Command at a Time**: Issue one command at a time to ensure accurate processing.
- **Pause Between Commands**: Allow brief pauses to enable FortiAI to process each command.

> [!Note]
> The *Voice Recognition* feature is currently unsupported on the Firefox browser as the webkit `SpeechRecognition` is not compatible with Mozilla Firefox. Hence, the mic button is not available when the FortiSOAR&trade; environment is accessed using the Firefox browser.

# Configuration

The **FortiAI** solution depends on the following connectors and widgets:

- **AI Assistant Utils** connector to help interact with LLMs like OpenAI.

>[!NOTE]
>The AI Assistant Utils connector does not require a configuration. For more details, see the [AI Assistant Utils Connector](https://docs.fortinet.com/fortisoar/connectors/ai-assitant-utils) document.

- The **OpenAI** connector to get a response from **FortiSOAR AI Assistant**.
    - To configure and use the OpenAI connector, see the [OpenAI Connector](https://docs.fortinet.com/fortisoar/connectors/openai) document.

## FortiAI Configuration Wizard

The wizard helps select the LLM Model, configure the OpenAI connector, and create &ndash; or update &ndash; the OpenAI Assistant. The OpenAI assistant handles SOC conversations and playbook generation.

The FortiAI Configuration wizard guides you through the following steps to setup FortiAI:

1. After [installation](#installation), click the **Configure** button.

    ![FortiAI Configuration](./res/configure-button.png)

2.  On the following wizard screen, click **Let's Get Started** to proceed.

    ![FortiAI Configuration](./res/config-wizard-00.png)

3. On the **Configuration** page, select a value for the following fields:

    ![](./res/config-wizard-01.png)

    - **LLM Integration** &mdash; *OpenAI* (default).
    - **Conversation Model**: Select one from the following options:

        - `gpt-4o-mini-2024-07-18`
        - `gpt-4o-mini` (default)
        - `gpt-4o-2024-05-13`
        - `gpt-4-turbo-2024-04-09`


    - **Playbook Generation Model**: Select one from the following options:

        - `gpt-4o-mini-2024-07-18`
        - `gpt-4o-mini` (default)
        - `gpt-4o-2024-05-13`
        - `gpt-4-turbo-2024-04-09`

    -  Select **Enable multi user configuration** to use the connector configuration that matches the login ID of the logged-in user. Clear the selection to use the default configuration for the LLM integration.

> [!NOTE]
> When using a fine-tuned model &mdash; or any model whose name differs from the default models provided by the LLM provider &mdash; add that custom model's name to the [`modelList`](./contents.md#fortiai-configurations).

4. Click **Next** on the lower-right corner.

    - Configure your LLM Integration (OpenAI) on the **Connect LLM** page using the project-level API key. For configuration details, refer to the [OpenAI connector configuration](https://docs.fortinet.com/fortisoar/connectors/openai) section on FortiSOAR connector page.

    ![Connect LLM](./res/config-wizard-02.png)

5. Click **Next** on the lower-right corner.

    ![Finish Configuration](./res/config-wizard-03.png)

6. Click **Finish** to complete the configuration.

> [!IMPORTANT]  
> By default, all these fields are loaded from, and saved to, the **Key Store** record named *`fortiai-configuration`*.

Navigate to *Incident Response*, *Automation*, or *Resources* navigation menu to interact with **FortiSOAR AI Assistant**.

# Next Steps
| [Usage](./usage.md) | [Contents](./contents.md) |
|---------------------|---------------------------|
