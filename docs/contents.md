| [Home](../README.md) |
|----------------------|

# Contents

The **FortiAI** solution pack contains the following resources:

## Connectors

| Name               | Description                                                |
|:-------------------|:-----------------------------------------------------------|
| AI Assistant Utils | Bundles helper methods that aid with content generation.   |
| OpenAI             | Provides the OpenAI models that are used as a backing LLM. |

## Widget

| Name                                                        | Description                                                                                          |
|:------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|
| AI Assistant                                                | Adds the Advisor bot to the FortiSOAR User Interface.                                                |
| FortiAI Configuration Wizard![icon-new](./res/icon-new.svg) | Launches a wizard that walks a user through the process of setting up LLM Integration Configuration. |

## Attachments

| Name                                 | Description                                                              |
|:-------------------------------------|:-------------------------------------------------------------------------|
| FortiAI - SOC Assistant Instructions | Contains the set of instruction of which SOC Assistant will get created. |

## Attachment - Record Set

| Name                                 | Description                                                              |
|:-------------------------------------|:-------------------------------------------------------------------------|
| FortiAI - SOC Assistant Instructions | Contains the set of instruction of which SOC Assistant will get created. |


## Key Store - Record Set

| Name                       | Description                                                                           |
|:---------------------------|:--------------------------------------------------------------------------------------|
| `fortiai-configurations`   | Contains keys like `llmIntegrations`, `llmIntegrationToUse`, and `llmIntegrationData` |
| `fortiai-static-questions` | Contains questions for different modules along with field of interest to be used.     |

### Key Store Contents

<table>
    <tr>  
        <th rowspan=3><code>fortiai-configurations</code></th>
        <th><code>llmIntegrations</code></th>
        <td>Sets the integration such as OpenAI, Google Bard, etc., to be used as the LLM. By default, 'OpenAI' is configured to be used as the LLM.
            <table>
                <tr>
                    <th><code>name</code></th>
                    <td>LLM Integration name as per Connector. By default, `openai` is set.</td>
                </tr>
                <tr>
                    <th><code>title</code></th>
                    <td>LLM Integration title as per Connector. By default, `OpenAI` is set.</td>
                </tr>
                <tr>
                    <th><code>modelList</code></th>
                    <td>List of LLM Integration models. By default, `gpt-3.5-turbo`, `gpt-3.5-turbo-0301`, `gpt-4`, `gpt-4-1106-preview` is present.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <th><code>llmIntegrationToUse</code></th>
        <td>Sets the integration such as OpenAI, Google Bard, etc., to be used as the LLM. By default, `OpenAI` is configured to be used as the LLM.</td>
    </tr>
    <tr> 
        <th><code>llmIntegrationData</code></th>
        <td>Contain the data for each LLM Integration.
            <table>
                <tr>
                    <th><code>conversationModel</code></th>
                    <td>Sets the model of LLM Integration to use in <i>Conversation</i> and <i>Response Plans / Jinja / Playbook How To's </i> Mode. By Default, `gpt-4-1106-preview` is to be used. </td>
                </tr>
                <tr>
                    <th><code>pBGenerationModel</code></th>
                    <td>Sets the model of LLM Integration to use in <i>Playbook Generation</i> Mode. By Default, `gpt-4-1106-preview` is to be used. </td>
                </tr>
                <tr>
                    <th><code>isMultiConfigAvailable</code></th>
                    <td>Sets as <b>true</b> or <b>false</b> to support the Multiple Configuration. By Default, it is set to `false`</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>  
        <th rowspan=1><code>fortiai-static-questions</code></th>  
        <td>moduleAPIName</td>
        <td>
            <table>
                <tr>
                    <th><code>questions</code></th>
                    <td>
                        <table>
                            <tr>
                                <th><code>question</code></th>
                                <th>Question name to be displayed based as per module type. For instance, the <b>alerts</b> module includes specific questions such as <i>Generate Alert Summary</i>, <i>Generate Alert Report</i></i>
                                </th>
                            </tr>
                            <tr>
                                <th><code>description</code></th>
                                <td>Description of the question to be displayed in the chatbot interface.</td>
                            </tr>
                            <tr>
                                <th><code>enable</code></th>
                                 <td>Flag it as either true or false to determine whether it should be rendered on the AI bot.</td>
                            </tr>
                        </table>
                    </td> 
                </tr>
                <tr> 
                    <th><code>fieldsOfInterest</code></th>
                    <td>To include the field data for the that module in conversation.</td>
                </tr>
            </table>
        </td>
    </tr>    
</table>

>[!NOTE]
>To add a deprecated question for different modules, follow these steps:
>   1. Add the question in JSON format under the particular module's API name. A sample [Question JSON](./question-sample.json) is attached to the document.
>   2. Add new LLM or LLM models in [](./),Write a playbook along with the tag mentioned in the JSON above.

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