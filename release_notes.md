# What's New

## Introducing Top SOC Questions

Edit or disable existing prompts or add new prompts based on your security posture.

- You can now customize your interactions with the LLM by providing specific details and guidelines for your chats. Define your own SOC questions to customize your LLM interactions.

- Specific modules now have pre-defined questions. For example, under the **Alerts** module, questions include:

    - Get Alert Summary
    - Generate Response Recommendations
    - Generate Investigation Report
    - MITRE ATT&CK Insight
    
    Similarly, for the **Incident** module, questions may be:
    
    - Get Incident Summary
    - Generate Response Recommendations
    - Generate Investigation Report
    - MITRE ATT&CK Insight

- Refer to the [Table of Contents](./docs/contents.md#table-of-contents) to add or edit new questions.

## Playbook Generation Mode

- An installed connector now gets priority for generating playbook steps.

## LLM Configuration

[FortiAI Configuration Wizard](https://github.com/fortinet-fortisoar/widget-fortiai-configuration/blob/release/1.0.0/README.md) now helps configure the following details:

- Configure LLM integration, such as Open AI.

- Choose the LLM model for different modes: 

    - **Playbook Generation**: gpt-4-1106-preview 
    - **Response Plans / Jinja / Playbook How To's**: gpt-3.5-turbo
    - **Conversation Mode**: gpt-3.5-turbo

- Multi-user configuration based on the login ID of the logged-in user is now possible.