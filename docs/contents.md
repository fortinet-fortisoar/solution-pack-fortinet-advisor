| [Home](../README.md) |
|--------------------------------------------|

# Contents

The **FortiAI** solution pack contains the following resources:

## Connectors

| **Name**           | **Description**                          |
| :----------------- | :--------------------------------------- |
| AI Assistant Utils | Bundles helper methods that aid with content generation. |
| OpenAI             | Provides the OpenAI models that are used as a backing LLM. |

## Widget

| **Name**     | **Description**                          |
| :----------- | :--------------------------------------- |
| AI Assistant | Adds the Advisor bot to the FortiSOAR User Interface. |
| AI Assistance Configuration <sup>New</sup> | Launches a wizard that walks a user through the process of setting up LLM Integration Configuration. |

## Key Store - Record Set

| **Name**        | **Description**                          |
| :-------------- | :--------------------------------------- |
| FortiAI Configurations | Contains the key like `llmIntegrationToUse`, `llmIntegrationData`, `conversationModel`, `pBGenerationModel`, and `isMultiConfigAvailable` |
| FortiAI Static Questions | Contains the question for different modules along with the playbook tag to execute on each question. Also the contain the list of fields to be use for question. |

#### Table of Content
<table>
    <tr>  
        <th rowspan=5>FortiAI Configurations</th>  
        <th>llmIntegrationToUse</th>
        <td>Sets the integration such as OpenAI, Google Bard, etc., to be used as the LLM. By default, 'OpenAI' is configured to be used as the LLM.</td>
    </tr>
    <tr> 
        <th>llmIntegrationData</th>
        <td>Contain the data for each LLM Integration.</td>
    </tr>
    <tr>
        <th>conversationModel</th>
        <td>Sets the model of LLM Integration to use in <i>Conversation</i> and <i>Response Plans / Jinja / Playbook How To's </i> Mode.</td>
    </tr>
    <tr>
        <th>pBGenerationModel</th>
        <td>Sets the model of LLM Integration to use in <i>Playbook Generation</i> Mode.</td>
    </tr>
    <tr>
        <th>isMultiConfigAvailable</th>
        <td>Sets as <b>true</b> or <b>false</b> to support the Multiple Configuration.</td>
    </tr>
    <tr>  
        <th rowspan=8>FortiAI Static Question</th>  
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

<table>
    <tr>
        <th>NOTE</th>
    </tr>
    <tr>
        <td>
            To add a new question for different modules, follow these steps:
            <ol>
                <li>Add the question in JSON format under the particular module's API name. <a href="./question-sample.json">Question JSON</a></li>
                <li>Write a playbook along with the specific tag mentioned in the JSON above.</li>
            </ol>
        </td>
    </tr>
</table>

## Playbook Collection

|10 - SP - Fortinet Advisor |
| :--------------------------------------- |

| **Playbook Name**                   | **Description**                          |
| :---------------------------------- | :--------------------------------------- |
| Converse with LLM                   | Starts a conversation using the LLM.     |
| Get Playbook Step Suggestion        | Suggests steps to create a playbook based on user's query. |
| Get Playbook Step Suggestion (Loop) | Suggests steps to create a playbook based on user's query, in a loop. |
| Get Playbook Block Suggestion       | Creates a suggested playbook block to perform actions based on user requirements. |
| Generate WorkPlan for User Inputs   | Creates a response plan for the scenario specified by the user. |
| > Get LLM Response                  | Reference playbook for getting a response from the LLM. |
| Get Alert Summary <sup>New</sup> | Get the Alert summary from LLM. |
| Get Incident Summary <sup>New</sup> | Get the Incident summary from LLM. |
| Get Alert Response Plan <sup>New</sup> | Get the Alert response plan from LLM. |
| Get Incident Response Plan <sup>New</sup> | Get the Incident response plan from LLM. |
| Get Alert Report <sup>New</sup> | Get the Alert report from LLM. |
| Get Incident Report <sup>New</sup> | Get the Incident report from LLM. |
| Get Alert MITRE Insight <sup>New</sup> | Get the Alert MITRE insight from LLM. |
| Get Incident MITRE Insight <sup>New</sup> | Get the Incident MITRE insight from LLM. |


>**Warning:** We recommend that you clone these playbooks before customizing to avoid loss of information while upgrading the solution pack.


# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) |
|-----------------------------------------|-------------------------------------------|---------------------|