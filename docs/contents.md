| [Home](../README.md) |
|----------------------|

# Contents

The **FortiAI** solution pack contains the following resources:

## Connectors

| Name               | Description                                                                                     |
|:-------------------|:------------------------------------------------------------------------------------------------|
| AI Assistant Utils | Bundles helper methods that aid with content generation and communicates with LLMs like OpenAI. |
| OpenAI             | Provides the OpenAI models that are used as a backing LLM.                                      |

## Widget

| Name                         | Description                                                                                          |
|:-----------------------------|:-----------------------------------------------------------------------------------------------------|
| AI Assistant                 | Adds the Advisor bot to the FortiSOAR User Interface.                                                |
| FortiAI Configuration Wizard | Launches a wizard that walks a user through the process of setting up LLM Integration Configuration. |

## Attachments

| Name                                 | Description                                                              |
|:-------------------------------------|:-------------------------------------------------------------------------|
| FortiAI - SOC Assistant Instructions | Contains the set of instruction of which SOC Assistant will get created. |

## Key Store - Record Set

| Name                       | Description                                                                           |
|:---------------------------|:--------------------------------------------------------------------------------------|
| `fortiai-configurations`   | Contains keys like `llmIntegrations`, `llmIntegrationToUse`, and `llmIntegrationData` |
| `fortiai-static-questions` | Contains questions for different modules along with field of interest to be used.     |

### Key Store Contents

#### `fortiai-configurations`

- **`llmIntegrations`**: Sets the integration to OpenAI as the default LLM.
    - `name`: LLM Integration name as per Connector. By default, `openai` is set.
    - `title`: LLM Integration title as per Connector. By default, `OpenAI` is set.
    - `modelList`: List of LLM Integration models. By default, `gpt-4o-mini-2024-07-18`, `gpt-4o-mini`, `gpt-4o-2024-05-13`, and `gpt-4-turbo-2024-04-09` is present.
- **`llmIntegrationToUse`**: Sets the integration to OpenAI as the default LLM.
- **`llmIntegrationData`**: Contains the data for each LLM Integration.
    - `messagesLimit`: Specify the maximum messages to be loaded in the conversation window on login. By default, it is set to `20`.
    - `conversationModel`: Sets the model of LLM Integration to use in conversations. By Default, `gpt-4o-mini` is to be used.
    - `pBGenerationModel`: Sets the model of LLM Integration to use for playbook generation. By Default, `gpt-4o-mini` is to be used.
    - `isMultiConfigAvailable`: Sets the availability of multiple configuration. By Default, it is set to `false`.

#### `fortiai-static-questions`

- **`modules`**: The parent object that contains the list of modules, respective questions and  their descriptions.
    - *Module-API-Name*: Specify the module's API name on which to display the preset questions. By Default, `alerts`, `incidents`, and `indicators` are present as modules on which the static questions are displayed.
        - **`questions`**: An array containing following keys as separate objects:
            - `question`: Question name to be displayed based as per module type. For instance, the **Alerts** module includes specific questions such as *Generate Alert Summary*, *Generate Alert Report*
            - `description`: Description of the question to be displayed in the chatbot interface.
            - `enable`: Flag it as either `true` or `false` to determine whether it should be rendered on the AI bot.
        - **`fieldsOfInterest`**: An array containing the various fields to use for building context for generating data requested by the preset questions (contained within the `question` key). Each module may have different fields of interest.

>[!NOTE]
>To add a preset question for a module:
>Add the question, with `description` and `enable` flag, in as JSON under the particular module's API name. A sample [Question JSON](./question-sample.json) is attached to the document.

## Playbook Collection

|10 - SP - FortiAI |
|:----------------:|


| Playbook Name                                                                  | Description                                                                               |
|:-------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------|
| Get Playbook Step Suggestion                                                   | Suggests steps to create a playbook based on user's query.                                |
| Get Playbook Step Suggestion (Loop)                                            | Suggests steps to create a playbook based on user's query, in a loop.                     |
| Get Playbook Block Suggestion                                                  | Creates a suggested playbook block to perform actions based on user requirements.         |
| > Get LLM Response                                                             | Reference playbook for getting a response from the LLM.                                   |
| > Get LLM Configuration                                                        | Get the LLM configuration based on the value defined for the key "isMultiConfigAvailable" |
| Generate WorkPlan for User Inputs![icon-deprecated](./res/icon-deprecated.svg) | Creates a response plan for the scenario specified by the user.                           |
| Converse with LLM![icon-deprecated](./res/icon-deprecated.svg)                 | Starts a conversation using the LLM.                                                      |
| Get Alert Summary![icon-deprecated](./res/icon-deprecated.svg)                 | Get the Alert summary from LLM.                                                           |
| Get Incident Summary![icon-deprecated](./res/icon-deprecated.svg)              | Get the Incident summary from LLM.                                                        |
| Get Alert Response Plan![icon-deprecated](./res/icon-deprecated.svg)           | Get the Alert response plan from LLM.                                                     |
| Get Incident Response Plan![icon-deprecated](./res/icon-deprecated.svg)        | Get the Incident response plan from LLM.                                                  |
| Get Alert Report![icon-deprecated](./res/icon-deprecated.svg)                  | Get the Alert report from LLM.                                                            |
| Get Incident Report![icon-deprecated](./res/icon-deprecated.svg)               | Get the Incident report from LLM.                                                         |
| Get Alert MITRE Insight![icon-deprecated](./res/icon-deprecated.svg)           | Get the Alert MITRE insight from LLM.                                                     |
| Get Incident MITRE Insight![icon-deprecated](./res/icon-deprecated.svg)        | Get the Incident MITRE insight from LLM.                                                  |


>[!Warning]
>We recommend that you clone these playbooks before customizing to avoid loss of information while upgrading the solution pack.


# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) |
|-----------------------------------------|-------------------------------------------|---------------------|