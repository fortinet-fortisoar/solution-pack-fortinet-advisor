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

## Key Store - Record Set

| Name                     | Description                                                                                                                                       |
|:-------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| FortiAI Configurations   | Contains keys like `llmIntegrations`, `llmIntegrationToUse`, and `llmIntegrationData`            |
| FortiAI Static Questions | Contains questions for different modules along with playbook tags to execute on each question, prompt, fields to be used, include similar records, display recommended playbook. |

### Table of Contents

<table>
    <tr>  
        <th rowspan=3>FortiAI Configurations</th>  
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
        <th rowspan=1>FortiAI Static Question</th>  
        <td>moduleAPIName</td>
        <td>
            <table>
                <tr>
                    <th>questions</th>
                    <td>Includes a list of questions to be displayed based on the module type and specifies the playbook tag to be executed for each question. For instance, the <b>alerts</b> module includes specific questions such as <i>Generate Alert Summary</i>, which is associated with the playbook tag <i>aibot-alertRecordSummary</i></td>
                </tr>
                <tr>
                    <th>description</th>
                    <td>Description of the question to be displayed in the chatbot interface.</td>
                </tr>
                <tr>
                    <th>pbTag</th>
                    <td>Playbook tag indicating the execution of the playbook specific to that particular question.</td>
                </tr>
                <tr>
                    <th>enabled</th>
                    <td>Flag it as either true or false to determine whether it should be rendered on the AI bot.</td>
                </tr>
                <tr>
                    <th>prompt</th>
                    <td>Define the prompt to be sent to the LLM model, along with any additional details.</td>
                </tr>
                <tr> 
                    <th>fieldsOfInterest</th>
                    <td>Each module type contains the keys <b>primaryFields</b> and <b>coRelatedFields</b> to be utilized in prompts. <b>coRelatedFields</b> includes keys such as <i>moduleName</i>, <i>recordCount</i>, and <i>primaryFields</i>, which incorporate data pertaining to correlated fields, including the record count and the fields intended for use in coRelatedFields.</td>
                </tr>
                <tr>
                    <th>showRecommendedPlaybooks</th>
                    <td>Flag it as true or false to determine whether to retrieve recommended playbooks based on the output of that question.</td>
                </tr>
                <tr>
                    <th>getSimilarRecords</th>
                    <td>Set it as true or false to determine whether similar records should be included for that question.</td>
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
                <li>Write a playbook along with the tag mentioned in the JSON to execute it on a particular question.</li>
            </ol>
        </td>
    </tr>
</table>

## Playbook Collection

|10 - SP - Fortinet Advisor |
|:-------------------------:|


| Playbook Name                                             | Description                                                                       |
|:----------------------------------------------------------|:----------------------------------------------------------------------------------|
| Converse with LLM                                         | Starts a conversation using the LLM.                                              |
| Get Playbook Step Suggestion                              | Suggests steps to create a playbook based on user's query.                        |
| Get Playbook Step Suggestion (Loop)                       | Suggests steps to create a playbook based on user's query, in a loop.             |
| Get Playbook Block Suggestion                             | Creates a suggested playbook block to perform actions based on user requirements. |
| Generate WorkPlan for User Inputs                         | Creates a response plan for the scenario specified by the user.                   |
| > Get LLM Response                                        | Reference playbook for getting a response from the LLM.                           |
| Get Alert Summary![icon-new](./res/icon-new.svg)          | Get the Alert summary from LLM.                                                   |
| Get Incident Summary![icon-new](./res/icon-new.svg)       | Get the Incident summary from LLM.                                                |
| Get Alert Response Plan![icon-new](./res/icon-new.svg)    | Get the Alert response plan from LLM.                                             |
| Get Incident Response Plan![icon-new](./res/icon-new.svg) | Get the Incident response plan from LLM.                                          |
| Get Alert Report![icon-new](./res/icon-new.svg)           | Get the Alert report from LLM.                                                    |
| Get Incident Report![icon-new](./res/icon-new.svg)        | Get the Incident report from LLM.                                                 |
| Get Alert MITRE Insight![icon-new](./res/icon-new.svg)    | Get the Alert MITRE insight from LLM.                                             |
| Get Incident MITRE Insight![icon-new](./res/icon-new.svg) | Get the Incident MITRE insight from LLM.                                          |


>**Warning:** We recommend that you clone these playbooks before customizing to avoid loss of information while upgrading the solution pack.


# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) |
|-----------------------------------------|-------------------------------------------|---------------------|