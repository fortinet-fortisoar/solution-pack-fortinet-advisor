| [Home](../README.md) |
|--------------------------------------------|

# Advanced Usage

This section includes information that may be helpful to administrators and users interacting with OpenAI Assistant.

## Prompting tips

Simple tweaks to the input prompts could improve the playbook block generation process using **FortiAI**. While asking queries or giving input to the Assistant bot keep some tips in mind:

- To use a specific integration in a use case, provide it as part of the prompt. For example;

    - Use *Get IP Reputation using VirusTotal*

        instead of

    - *Get IP Reputation*.
    
    In the second prompt, FortiAI may include any enrichment source such as IP Quality Score, AlienVault-OTX, VirusTotal, etc. You must also ensure that any connector specified in the prompt is installed on your system.

- To create playbooks intended to add a record in FortiSOAR, avoid using *Create <`module name`> record* as the first step. Instead, place it in the next step after gathering details from a previous action.

    >For example, use *Fetch Unread Emails from Exchange and create Alert record*

- To update a record in FortiSOAR with some value, use *Update <`module name`>....*.

    >For example, *Update Alert Severity to Critical* works better than *Increase Alert Severity to Critical*. 

- To create playbooks with On Create, On Update, or On Delete triggers, add terms such as 'On create/on update/on delete of <`module name`> record, perform further <actions>...'.

    >For example, On Create of alert add a comment *Hello, Analyst!*

- To create playbooks with manual triggers, use 'Manual Trigger on <`module name`>, perform further <actions>...'

    >For example, Manually trigger a playbook upon a Phishing type Alert Record to change the status to Investigating.

- To create playbooks with manual inputs, add terms such as 'Prompt the user for further <`name some actions`>...'

    >For example, Check the reputation of the indicator using VirusTotal and prompt the user for action: either block it or take no action.

- To create playbooks with decision blocks, use If...else statements.

    >For example, Check the IP's reputation using VirusTotal. If it's considered malicious, set the indicator reputation as malicious. If it's considered suspicious, set the indicator reputation as suspicious. Otherwise, set the indicator reputation as good.

## Utilizing your playbook collections to train the solution

By default, FortiAI is trained using the large collection of use cases available on the [FortiSOAR Content Hub](https://fortisoar.contenthub.fortinet.com/list.html). 

Simultaneously, we recognize that every organization develops automated content according to its own style and naming practice. You can add your playbook collections to the FortiAI's training set to have it speak your language when creating the playbook blocks.

>[!NOTE]
>To achieve better training results, the playbook collections used for training must have appropriate step names with clear descriptions. This is because the FortiAI uses these to generate the response playbook and steps. Additionally, when asking FortiAI to generate playbooks, it is recommended to use similar step names or keywords as those used in your trained playbook collections. For example, if 'Indicators' are used in step names, then do not use 'IOCs'.

Use the following steps to update the training using your playbook collections: 

1. Log onto FortiSOAR.

2. Navigate to **Settings** > **Application Editor** > **Export Wizard**.

3. On the `Export Wizard` page, click **New Template** to create a template that contains playbook collections you want to add as part of the training:

   ![Creating a new Export template with playbooks collections as part of training](../docs/res/exportWiz_pbTraining.png)

4. Select the playbook collections to be included in the training, provide an appropriate name for the export, and then click **Save and Run Export** to complete the export process. 

5. Download the exported file.  

   The exported file is the latest entry in the **Export History** tab. Capture its unique identifier, as shown in the following image:  

    ![Capturing the ID of the exported file](../docs/res/exportWiz_template.png)

6. Click **Automation** > **Playbooks** and search for **FortiAI**.

7. Open the 'Sample - AI Assistant Utils - 2.0.0' playbook collection and clone the 'Refresh Training Data' playbook:

   ![Cloning the Refresh Training Data playbook](../docs/res/clonePBcollection.png)

8. Open the 'Refresh Training Data' playbook and click the **Refresh Training Data** step. In the **Export File IRI** box, enter the file IRI to the value you had captured in step 5, and save the step and the playbook: 

   ![Updated the file IRI in the Refresh Training Data step](../docs/res/refreshtrainingdata.png)

9. Run the updated playbook.  
   Once this playbook is successfully executed, your selected custom playbook collections become part of the training dataset.

## Using an alternate connector configuration

To use the connector configuration other than the default configuration to get responses from the LLM, follow these steps:

1. Go to the '10 - SP - FortiAI' playbook collection and click the > 'Get LLM Response' playbook to open the same in the playbook designer.
2. In the  'Get LLM Response' playbook, double-click the 'Get OpenAI Response' connector step, and select the configuration you want to use:  
   ![Selecting the configuration to be used](../docs/res/alternateConnectorConfig.png)
3. Click **Save** to save the updated connector configuration and then click **Save Playbook** to save the playbook.  

## Restricting access to FortiAI

To restrict access to FortiAI by specifying the teams that are authorized to use the OpenAI connector, perform the following steps:

1. To limit access, open the OpenAI configuration, mark its **Visibility** as **Private**, and then click the **Ownership** icon:  
   ![OpenAI Connection configuration dialog - Ownership icon](../docs/res/rbac_openai.png)
2. In the **Assign Owners** dialog, you will see that the logged-in user's teams are automatically assigned ownership. To remove ownership of any team, click the **Red Cross** beside its name; similarly, to assign ownership to any team, select the team from the **Owners** drop-down list, click **Assign**, and then click **Submit**:  
   ![OpenAI Connection configuration - Assigning owners for the connector](../docs/res/openai_assignownership.png)  
3. Mark the following playbooks in the '10 - SP - FortiAI' playbook collection as **Private** and assign their ownership to the same teams that are assigned as owners in the OpenAI connector.
   - Generate WorkPlan For User Input
   - Get Playbook Block Suggestion
   - Converse with LLM  
     To mark a playbook, for example, the *Converse with LLM* playbook, as 'Private' and restrict its visibility to specific teams, follow these steps:
     1. Open the Converse with LLM playbook in the playbook designer, and in the top bar, mark its **Visibility** as **Private**, and then click the **Ownership** icon.  
        ![Marking playbooks as Private](../docs/res/pb_mark_private.png)  
     2. In the **Assign Owners** dialog, assign the ownership of the playbook to the same teams that are assigned as owners in the OpenAI connector, and then click **Submit**.   
        Once the teams are assigned in both the playbooks and the OpenAI connector, only those teams will have access to the OpenAI connector and will be able to receive responses from FortiAI.

## Adding New modules to Preset Questions

This section details steps to add new modules and context-sensitive questions when that module's record is opened.

As an example, let us add the **Assets** module (Module API Name: `assets`) and related questions (say `foo`, `bar`, and `baz`) with *Lorem Text* as descriptions. For context, let's select `id`, `name`, and `description` as fields of interest.

1. Open the **Key Store** record named `fortiai-static-questions`

2. Click the **Edit Record** button to edit the record.

3. Enter the following JSON under the parent object `modules`:

```JSON
"assets": {
    "questions": [
    {
        "enabled": true,
        "question": "foo",
        "description": "Lorem ipsum dolor sit amet"
    },
    {
        "enabled": true,
        "question": "bar",
        "description": "Consectetur adipiscing elit"
    },
    {
        "enabled": true,
        "question": "baz",
        "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit"
    }
    ],
    "fieldsOfInterest": [
    "id",
    "name",
    "description"
    ]
}
```

Now when you open a record under **Assets** module, you can see the 3 questions `foo`, `bar`, and `baz` with *Lorem Text* as descriptions.

![](./res/new_module_questions.png)

## Troubleshooting

### FortiAI bot not visible

The FortiAI bot is not visible after installing the **FortiAI** solution pack.

**Resolution**

To resolve this issue, you can either force a browser refresh or log out and log back in, to your FortiSOAR instance.

### FortiAI flyout does not open

The FortiAI flyout does not launch, or the FortiAI does not display any response for the playbook outline.

**Resolution**

To resolve this issue, check if the user is assigned appropriate permissions. To utilize the FortiAI solution pack, users must have the following permissions, along with other appropriate permissions:

- Read and Usage permissions on Widgets
- Read and Execute permissions on Playbooks

### FortiAI is unable to generate playbook steps

Based on your prompt, the FortiAI cannot generate the playbook steps.

**Resolution**

To resolve this issue, try the following:

- Try to regenerate the steps.
- Rephrase the prompt and try to generate the playbook steps, see [Prompting tips](#prompting-tips).
- Verify that your OpenAI account is operational and has enough credit.

### FortiAI does not create or update record

FortiAI does not create or update record as per specified fields in FortiSOAR.

**Resolution**

- Prompt the FortiAI 

    >*What parameter did you pass to create/update field.*

- Correct the parameters as per field API names as mentioned in FortiSOAR settings.

### Renaming OpenAI Connector Configuration

Sometimes, on changing the configuration name of OpenAI connector, it may not correctly render the updated name.

1. Press the **Back** button to return to the **LLM Configuration** page.

2. Click **Next** to advance to the **Connector Configuration** page.

### Response not as Expected

The prompt may not always be as expected, in such cases you may:

1. Send the prompt again

2. Rephrase the prompt to send a more targeted request.

### Response delay

After entering the prompt the text may still be visible; however, the text input field appears disabled and with 3-dot loader gif on screen.

**Resolution**

- The prompt has not passed to the LLM. Refresh the page and try again with the same prompt.

### OpenAI Error Messages

1. Can't add messages to thread_123ndasda341 while a run run_134314hh1 is active.
**Resolution**
- Try to cancel the RUN on OpenAI platform - while loading the same thread on assistant using URL - https://platform.openai.com/playground/assistants?mode=assistant&assistant=asst_id&thread=thread_id and cancel the run
- OR Clear the Conversation







| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Contents](./contents.md) |
|-----------------------------------------|-------------------------------------------|---------------------------|
