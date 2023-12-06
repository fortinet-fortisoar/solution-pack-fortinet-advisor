| [Home](../README.md) |
|--------------------------------------------|

# Contents

The **Fortinet Advisor** solution pack contains the following resources:

## Connectors

| **Name**           | **Description**                          |
| :----------------- | :--------------------------------------- |
| AI Assistant Utils | Bundles helper methods that aid with content generation. |
| OpenAI             | Provides the OpenAI models that are used as a backing LLM. |

## Widget

| **Name**     | **Description**                          |
| :----------- | :--------------------------------------- |
| AI Assistant | Adds the Advisor bot to the FortiSOAR User Interface. |

## Global Variables

| **Name**        | **Description**                          |
| :-------------- | :--------------------------------------- |
| LLM_Integration | Sets the integration such as OpenAI, Google Bard, etc., to be used as the LLM. By default, 'OpenAI' is configured to be used as the LLM. Note that Google Bard is not supported in the preview release. |
| OpenAI_Model    | Sets the OpenAI model to be used as the LLM. By default, the 'gpt-4-1106-preview' model is configured to be used as the LLM. |

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
| > Get LLM Response (Conversation)   | Reference playbook for getting a conversational response from the LLM. |


>**Warning:** We recommend that you clone these playbooks before customizing to avoid loss of information while upgrading the solution pack.


# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) |
|-----------------------------------------|-------------------------------------------|---------------------|