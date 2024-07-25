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

| Name                                                       | Description                                                                                          |
|:-----------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|
| AI Assistant                                               | Adds the Advisor bot to the FortiSOAR User Interface.                                                |
| AI Assistance Configuration![icon-new](./res/icon-new.svg) | Launches a wizard that walks a user through the process of setting up LLM Integration Configuration. |

## Attachment - Record Set

| Name                     | Description                                                                                                                                       |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| FortiAI - SOC Assistant Instructions   | Contains the set of instruction of which SOC Assistant will get created.            |


## Key Store - Record Set

| Name                     | Description                                                                                                                                       |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| fortiai-configurations   | Contains keys like `llmIntegrations`, `llmIntegrationToUse`, and `llmIntegrationData`            |
| fortiai-static-questions | Contains questions for different modules along with field of interest to be used. |

### Table of Contents

<table>
    <tr>  
        <th rowspan=3>fortiai-configurations</th>  
        <th>llmIntegrations</th>
        <td>Sets the integration such as OpenAI, Google Bard, etc., to be used as the LLM. By default, 'OpenAI' is configured to be used as the LLM.
            <table>
                <tr>
                    <th>name</th>
                    <td>LLM Integration name as per Connector. By default, `openai` is set.</td>
                </tr>
                <tr>
                    <th>title</th>
                    <td>LLM Integration title as per Connector. By default, `OpenAI` is set.</td>
                </tr>
                <tr>
                    <th>modelList</th>
                    <td>List of LLM Integration models. By default, `gpt-3.5-turbo`, `gpt-3.5-turbo-0301`, `gpt-4`, `gpt-4-1106-preview` is present.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <th>llmIntegrationToUse</th>
        <td>Sets the integration such as OpenAI, Google Bard, etc., to be used as the LLM. By default, `OpenAI` is configured to be used as the LLM.</td>
    </tr>
    <tr> 
        <th>llmIntegrationData</th>
        <td>Contain the data for each LLM Integration.
            <table>
                <tr>
                    <th>conversationModel</th>
                    <td>Sets the model of LLM Integration to use in <i>Conversation</i> and <i>Response Plans / Jinja / Playbook How To's </i> Mode. By Default, `gpt-4-1106-preview` is to be used. </td>
                </tr>
                <tr>
                    <th>pBGenerationModel</th>
                    <td>Sets the model of LLM Integration to use in <i>Playbook Generation</i> Mode. By Default, `gpt-4-1106-preview` is to be used. </td>
                </tr>
                <tr>
                    <th>isMultiConfigAvailable</th>
                    <td>Sets as <b>true</b> or <b>false</b> to support the Multiple Configuration. By Default, it is set to `false`</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>  
        <th rowspan=1>fortiai-static-questions</th>  
        <td>moduleAPIName</td>
        <td>
            <table>
                <tr>
                    <th>questions</th>
                    <td>
                        <table>
                            <tr>
                                <th>question</th>
                                <th>Question name to be displayed based as per module type. For instance, the <b>alerts</b> module includes specific questions such as <i>Generate Alert Summary</i>, <i>Generate Alert Report</i></i>
                                </th>
                            </tr>
                            <tr>
                                <th>description</th>
                                <td>Description of the question to be displayed in the chatbot interface.</td>
                            </tr>
                            <tr>
                                <th>enable</th>
                                 <td>Flag it as either true or false to determine whether it should be rendered on the AI bot.</td>
                            </tr>
                        </table>
                    </td> 
                </tr>
                <tr> 
                    <th>fieldsOfInterest</th>
                    <td>To include the field data for the that module in conversation.</td>
                </tr>
            </table>
        </td>
    </tr>    
</table>

<table>
    <tr>
        <th>NOTE</th>
    </tr>
    <tr>
        <td>
            <ol>
                <li>To add the new LLM or LLM Models, refer <a href="./llm-configuration.json">JSON</a>.</li>
                <li>To add the new question, refer <a href="./question-sample.json">JSON</a>.</li>
            </ol>
        </td>
    </tr>
</table>

## Playbook Collection

|10 - SP - Fortinet Advisor |
|:-------------------------:|


| Playbook Name                                             | Description                                                                       |
|:----------------------------------------------------------|:----------------------------------------------------------------------------------|
| Get Playbook Step Suggestion                              | Suggests steps to create a playbook based on user's query.                        |
| Get Playbook Step Suggestion (Loop)                       | Suggests steps to create a playbook based on user's query, in a loop.             |
| Get Playbook Block Suggestion                             | Creates a suggested playbook block to perform actions based on user requirements. |
| > Get LLM Response                                        | Reference playbook for getting a response from the LLM.                           |
| > Get LLM Configuration | Get the LLM configuration based on the value defined for the key "isMultiConfigAvailable" |

>**Warning:** We recommend that you clone these playbooks before customizing to avoid loss of information while upgrading the solution pack.


# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) |
|-----------------------------------------|-------------------------------------------|---------------------|