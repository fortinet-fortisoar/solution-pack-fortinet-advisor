# What's New

## Introducing Top SOC Questions

- Customize your interactions with LLM by providing specific details and guidelines for your chats through defining your own SOC Questions.
- Pre-defined questions have been added for specific modules. For instance, under the `Alert` module, questions include `Get Alert Summary`, `Generate Response Recommendations`, `Generate Investigation Report`, and `MITRE ATT&CK Insight`. Similarly, for the `Incident` module, questions comprise `Get Incident Summary`, `Generate Response Recommendations`, `Generate Investigation Report`, and `MITRE ATT&CK Insight`.
- Refer to the [Table of Content](./docs/contents.md/#table-of-content) to add/edit new questions.
- Edit or disable existing prompts or add new prompts based on your security posture.

## Playbook Generation Mode

- For playbook step generation now priority is given to the installed connector.

## LLM Configuration

Now configure the following details using the [FortiAI Configuration Wizard](https://github.com/fortinet-fortisoar/widget-fortiai-configuration/blob/release/1.0.0/README.md):

- Configure LLM Integration, such as Open AI.
- Choose the LLM model for different modes: 
  - `Playbook Generation`: gpt-4-1106-preview 
  - `Response Plans / Jinja / Playbook How To's`: gpt-3.5-turbo
  - `Conversation Mode`: gpt-3.5-turbo
- Multi-User Configuration based on the login ID of the logged-in user.