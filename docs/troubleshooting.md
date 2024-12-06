| [Home](../README.md) |
|----------------------|

# Troubleshooting

## FortiAI bot not visible

The FortiAI bot is not visible after installing the **FortiAI** solution pack.

**Resolution**

To resolve this issue, you can either force a browser refresh or log out and log back in, to your FortiSOAR instance.

## FortiAI bot doesn't display mic

The *Voice Recognition* feature is currently unsupported on the Firefox browser as the webkit `SpeechRecognition` is not compatible with Mozilla Firefox. Hence, the mic button is not available when the FortiSOAR&trade; environment is accessed using the Firefox browser.

## FortiAI flyout does not open

The FortiAI flyout does not launch, or the FortiAI does not display any response for the playbook outline.

**Resolution**

To resolve this issue, check if the user is assigned appropriate permissions. To utilize the FortiAI solution pack, users must have the following permissions, along with other appropriate permissions:

- Read and Usage permissions on Widgets
- Read and Execute permissions on Playbooks

## FortiAI is unable to generate playbook steps

Based on your prompt, the FortiAI cannot generate the playbook steps.

**Resolution**

To resolve this issue, try the following:

- Try to regenerate the steps.
- Rephrase the prompt and try to generate the playbook steps, see [Prompting tips](#prompting-tips).
- Verify that your OpenAI account is operational and has enough credit.

## FortiAI does not create or update record

FortiAI does not create or update record as per specified fields in FortiSOAR.

**Resolution**

- Prompt the FortiAI 

    >*What parameter did you pass to create/update field.*

- Correct the parameters as per field API names as mentioned in FortiSOAR settings.

## Renaming OpenAI Connector Configuration

Sometimes, on changing the configuration name of OpenAI connector, it may not correctly render the updated name.

1. Press the **Back** button to return to the **LLM Configuration** page.

2. Click **Next** to advance to the **Connector Configuration** page.

## Response not as Expected

The prompt may not always be as expected, in such cases you may:

1. Send the prompt again

2. Rephrase the prompt to send a more targeted request.

## Response delay

After entering the prompt the text may still be visible; however, the text input field appears disabled and with 3-dot loader gif on screen.

**Resolution**

- The prompt has not passed to the LLM. Refresh the page and try again with the same prompt.

## OpenAI Error Messages

### Error: Cannot add messages to `thread_123ndasda341` while a run thread `run_134314hh1` is active.

**Resolution**
- Try to cancel the RUN on OpenAI platform - while loading the same thread on assistant using URL - https://platform.openai.com/playground/assistants?mode=assistant&assistant=asst_id&thread=thread_id and cancel the run

    OR

- Clear the Conversation

### Error: `Run Cancelled Exception` as toast notification

This error typically occurs when:  
- A subsequent prompt is sent in the same conversation.  
- A prompt involves filtering across multiple modules (e.g., incidents and alerts).  

>[!Note]
>Filtering operations do not support multiple modules simultaneously.This usually happens on subsequent prompting or with prompts including multiple modules.
>For example: *Fetch alerts with severity high, reputation good, and incidents with severity high*

#### Resolution

1. **Clear the Conversation**:  
   - End the current conversation to reset the context.

2. **Rephrase the Prompt**:  
   - Simplify the request to focus on a single module at a time.  
   - Avoid combining filtering criteria across different modules (e.g., incidents and alerts).

3. **Send the Prompt Again**:  
   - Issue the rephrased prompt in a new conversation to ensure proper execution.

### Filters Involving DateTime  

DateTime filtering may sometimes yield unexpected results due to default behaviors or incomplete prompts. Follow these steps to ensure accurate outcomes.

#### Resolution

1. **Specify the Timezone**:  
   - By default, DateTime filters may use UTC rather than your local timezone.  
   - Rephrase your prompt to explicitly include your preferred timezone.  

     **Example**:  
     > _"Filter alerts created on 1st December 2024. Consider local timezone."_

2. **Include the Year**:  
   - Omitting the year in DateTime filters can lead to inaccurate results.  
   - Always include the year to ensure the system applies the correct date range.  

     **Example**:  
     > _"Filter alerts created on 1st December 2024."_

3. **Account for the Entire Day**:  
   - If only a date or day is mentioned, the filter might not cover all events of that day.  
   - Rephrase the prompt to explicitly request filtering for the entire day.  

     **Example**:  
     > _"Filter alerts created on 1st December 2024. Consider entire day."_

### Field Names in Filters Do Not Update  

In some cases, the field names in filters may not reflect changes after subsequent prompts. Follow these steps to resolve the issue.

#### Resolution

1. **Refresh the Page**:  
   - Reload the page to ensure the filters reflect the updated field names.  

2. **Clear and Reapply the Filter**:  
   - Click ![](./res/icon-clear-filter.svg) to remove the current filter.  
   - Reapply the filter by clicking on the filter hyperlink, within the bot conversation, again.  


>[!Note]
>This issue has been resolved in **FortiSOAR v7.6.1** and later.

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |
