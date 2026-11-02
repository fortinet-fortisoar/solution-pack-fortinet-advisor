| [Home](../README.md) |
|----------------------|

# Usage

The AI Assistant bot accepts requests in natural language, from single actions to multi-step tasks. Common requests fall into the following groups.

- **Work with records**: [create](#creating-records), [update](#updating-records), [link](#linking-records), and [filter](#filtering-records) records.
- **Respond to threats**: [block](#blocking-indicators) and [enrich](#enriching-indicators) indicators, [escalate an alert to a case](#escalating-an-alert-to-a-case), and [set up a war room](#setting-up-a-war-room).
- **Investigate**: run [AI Investigation](#ai-investigation) on an alert, or make [requests that require planning](./advanced-usage.md#making-requests-that-require-planning).
- **Build content**: generate [connectors](#generating-a-connector) and [playbooks](#generating-playbooks), and get help with [response plans](#building-response-plans) and [Jinja expressions](#getting-help-with-jinja-expressions).

> [!Note]
> Restart the MCP server service after creating a new module to query records.

---

## Generating a connector

FortiAI can generate a FortiSOAR connector from natural language inputs and API specifications, producing all required connector files without manual coding.

### Procedure

Use the following steps to generate a connector.

1. **Provide input**: Navigate to **Content Hub** <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-chevron-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-chevron-dark.svg"><img alt=">" src="./res/icon-chevron-dark.svg"></picture> **Create**, open the AI Assistant bot, and enter a prompt that specifies:
   - The purpose of the connector.
   - The actions it must perform.
   - The associated API endpoint(s).

   API details can be provided as:
   - `curl` commands
   - JSON request/response structures

> [!Note]
> API specifications cannot be supplied as file attachments, such as PDF files, Swagger specifications, or Postman collections. Enter the specification in the chat instead, using `curl` commands or JSON.

2. **Review generated files**: FortiAI generates the following standard connector files:
   - `info.json`
   - `connector.py`
   - `operations.py`
   - `requirements.txt` (generated only when code dependencies are present)

3. **Review import**: The generated files and associated sample playbooks are bundled and the connector is automatically imported into the **Create** tab of the Content Hub. Refresh the page to view the generated connector tile.

4. **Edit the connector**: Access the connector under the **Create** tab in the Content Hub and review or modify it using the Build Your Own Connector tools.

### Best practices

Follow these practices for better results.

- Complete the full generation flow before making any modifications to the generated files.
- Provide clear and unambiguous API details. Well-structured inputs improve parameter extraction and output quality.

For step-by-step examples, see [Example: Building a connector](./example-creating-connectors.md).

> [!Note]
> It is recommended to clear a conversation before starting a new use case. This reduces token consumption and prevents context from a previous request from influencing the new request.

---

## Generating playbooks

FortiAI generates playbooks and playbook steps from natural language descriptions entered in the Playbook Designer.

> [!Tip]
> Generate smaller, focused playbook blocks for easier review. Combine multiple blocks to build larger workflows.

### Procedure

Use the following steps to generate a playbook.

1. **Open Playbook Designer**: For an introduction to the Playbook Designer, refer to [Creating Playbooks](https://docs.fortinet.com/document/fortisoar/8.0.0/user-guide/103864/get-started-with-fortisoar) in the FortiSOAR User Guide.

2. **Enter your requirements**: Describe the playbook in natural language in the Playbook Designer input field. For example:
   > *Extract Indicators from the Alert Source Data and enrich them using VirusTotal. Based upon reputation, if `malicious` update the indicator reputation to `malicious`, else if `suspicious` update the indicator reputation to `suspicious`, else update indicator reputation to `good`.*

3. **Modify the outline**: Adjust the generated playbook outline as needed. For example, replace one integration with another by editing the JSON. FortiAI tolerates minor typos in connector names.

4. **Generate the playbook**: Click **Ok, Generate Playbook**.

5. **Monitor progress**: A loading indicator is displayed while FortiAI generates the playbook steps.

6. **Review generated steps**: The generated playbook block appears in the Playbook Designer.

7. **Connect to main flow**: Connect the generated playbook block to the main playbook flow to complete the workflow.

> [!Tip]
> Clear the conversation before switching to a different use case. This reduces token consumption and prevents context from one request influencing another.

For step-by-step examples, see [Example: Generating Playbooks](./example-generating-playbooks.md).

---

## Providing context

The bot automatically loads the context of the currently open record. You can ask questions about the open record directly without restating its details. For example:

> *What is the source IP in this record?*

> [!Note]
> Ensure the context is current and relevant when making decisions based on bot responses.

---

## Linking records

The bot can correlate records with one another, such as linking an indicator to an alert or a case.

### Commands

The following examples link and correlate records.

- **Link a specific record:**
  > *Link indicator ID [INDICATOR-ID] to alert ID [ALERT-ID]*

- **Correlate records:**
  > *Correlate the newly detected IP [INDICATOR-ID] with [CASE-ID]*

> [!Tip]
> Verify that linked records are contextually relevant. Accurate links improve threat analysis and reduce noise.

---

## Creating records

The bot can create new records in any FortiSOAR module.

> [!Note]
> For *Create Record* operations, the bot requires the `ID` and `UUID` of related records if they are not already present in the conversation history.

### Commands

The following examples create records.

- **Create a record:**
  > *Create a new case record in the Cases module*

- **Create with specific field values:**
  > *Create a new alert with the following details: [Details of the alert]*

  If required fields are missing, the bot will prompt for the missing information.

---

## Updating records

The bot can update field values on existing records.

> [!Note]
> For *Update Record* operations, the bot requires the `ID` and `UUID` of the target record if not already in the conversation history.

### Commands

The following examples update records.

- **Update a record:**
  > *Update the case with ID [CASE-ID] with the following details: [Updated details]*

- **Update a specific field:**
  > *Update the alert status to "Resolved" and add a note: [Note text]*

> [!Warning]
> Updating a record overwrites any existing value in the specified field.

---

## Filtering records

The bot applies filter conditions to records in a module and returns a hyperlink to the filtered view.

### Commands

The following examples filter records.

- **Filter by a single condition:**
  > *Filter alerts where severity is `high`*

- **Add additional conditions:**
  > *Add condition to show alerts created in the last 24 hours*

> [!Note]
> Filter conditions must target a single module at a time. Prompts that combine filter criteria across multiple modules (for example, cases and alerts simultaneously) are not supported.

For a reference of example filtering prompts, see [Prompt examples](./prompt-examples.md).

---

## Blocking indicators

The bot triggers a playbook to block an indicator using a configured connector.

### Commands

The following examples block indicators.

- **Block by IP address:**
  > *Block IP address `[IP-ADDRESS]`*

- **Block by domain:**
  > *Block domain `[DOMAIN]` due to malicious activity*

  If the playbook execution takes time, the bot returns a link to the playbook execution log.

> [!Note]
> Verify that the connector used for blocking is correctly configured before issuing a block command.

---

## Enriching indicators

The bot retrieves the current reputation for an indicator from configured threat intelligence sources.

### Commands

The following examples enrich indicators.

- **Enrich by IP address:**
  > *Retrieve the reputation of IP address `[IP-ADDRESS]`*

- **Enrich by domain:**
  > *Get the latest reputation for domain `[DOMAIN]`*

---

## Escalating an alert to a case

The bot triggers the alert escalation playbook, which collects required details (case name, severity) before creating the case.

### Commands

The following examples escalate an alert.

- **Escalate an alert:**
  > *Promote alert with ID [ALERT-ID] to a case*

- **Escalate with additional context:**
  > *Escalate alert [ALERT-ID] with subject [ALERT-SUBJECT] to a case*

> [!Note]
> If the alert record is open, the bot presents a manual input prompt. Pending manual inputs are also accessible under **Pending Tasks** in the FortiSOAR toolbar.

---

## Setting up a war room

The bot creates a war room associated with a specified case.

### Commands

The following examples create a war room.

- **Create a war room:**
  > *Establish a war room for case [CASE-ID]*

- **Create with context:**
  > *Create a war room for case [CASE-ID] involving [CASE-DESCRIPTION]*

> [!Note]
> If the case record is open, the bot presents a manual input prompt. Pending manual inputs are also accessible under **Pending Tasks** in the FortiSOAR toolbar.

> [!Tip]
> Keep the war room updated with the latest findings and ensure all relevant team members have access.

---

## Building response plans

The bot can generate a structured response plan framework for a security event, which can then be used as the basis for playbook creation.

### Commands

The following example requests a response plan.

- **Request a response plan:**
  > *Can you help me with a plan to handle a phishing attack?*

  FortiAI returns a structured framework (for example: identify phishing emails, isolate affected systems, notify stakeholders). Use the **Playbook Generation** option to convert the framework into executable playbook steps.

> [!Tip]
> Review and update response plans regularly to reflect current threat intelligence and organizational requirements.

---

## Getting help with Jinja expressions

FortiAI can generate or explain Jinja expressions for use in playbooks.

### Commands

The following examples request Jinja expressions.

- **Request an expression:**
  > *Help me create a Jinja expression to extract the IP address from the alert data*

- **Request a specific field:**
  > *I need a Jinja expression to extract the field `source_ip` from the alert*

> [!Tip]
> Test Jinja expressions in a non-production playbook before deploying them.

---

## AI Investigation

**AI Investigation** is a tab on the **Alert** detail page. It runs an automated investigation of the alert using a coordinated set of AI agents, without requiring manual prompting.

### Running an investigation

Use the following steps to run an investigation.

1. Open the alert you want to investigate.
2. Click the **AI Investigation** tab.
3. Click **Begin AI-Powered Alert Investigation**.

The investigation runs automatically. The left pane displays progress steps such as *Enriching Alert Context*, *Executing Investigation Plan*, *Evaluating Hypothesis*, and *Generating Investigation Verdict*.

### Investigation output

After the investigation completes, the view displays three sections:

**AI Agents**
Lists the AI agents that participated in the investigation (for example, Alert Investigation Agent, Threat Intelligence Provider Agent).

**Hypotheses**
FortiAI generates five competing hypotheses for the alert, each representing a possible explanation for the observed activity:

| Classification | Description                               |
|----------------|-------------------------------------------|
| Benign         | Activity is expected and non-threatening. |
| False Positive | Alert was triggered incorrectly.          |
| Malicious      | Activity indicates a confirmed threat.    |
| Suspicious     | Activity warrants further investigation.  |
| Inconclusive   | Insufficient evidence to classify.        |

Select a hypothesis to view its **Investigative Results**, **Hypothesis Details** (supporting and weakening factors, mapped MITRE ATT&CK tactics and techniques), and **Questions** (structured investigation questions with AI agent inputs and responses).

**Verdict**
Summarizes the overall alert classification. The Verdict section contains three tabs:

| Tab              | Description                                                                                     |
|------------------|-------------------------------------------------------------------------------------------------|
| **Highlights**   | Narrative summary of the triage process, including key supporting evidence and identified gaps. |
| **Key Findings** | Significant findings from the investigation. Select a finding to view additional detail.        |
| **Next Steps**   | Recommended actions for further investigation or response, for execution by the SOC analyst.    |

Click **Re-investigate** to rerun the investigation after making changes such as updating configurations, adding threat intelligence sources, or modifying alert data.

> [!Note]
> AI Investigation results depend on the AI agents installed and configured in your environment. Users must have access to AI Agents, Widgets (Usage), Alerts, and Indicators. Refer to the individual AI agent documentation for prerequisites and configuration details.

---

## Contextual questions

The AI Assistant bot maintains conversation context, loading the last 20 messages in the conversation window on login. Access the bot from any module list view or detail view, or via **AI** <picture><source media="(prefers-color-scheme: dark)" srcset="./res/icon-chevron-light.svg"><source media="(prefers-color-scheme: light)" srcset="./res/icon-chevron-dark.svg"><img alt=">" src="./res/icon-chevron-dark.svg"></picture> **AI Agents** in the left navigation pane.

> [!Note]
> To change the message limit, edit the `messagesLimit` parameter in the `fortiai-configurations` **Key Store** record.

For example, with a Dragonfly malware alert open:

> *Can you provide me with more information about the Dragonfly Malware?*

---

## Module-specific quick prompts

When a record is open, the AI Assistant bot displays module-specific quick prompts. Click a question to retrieve information about the open record. Quick prompts are also shown on a module's list view.

For the default quick prompts configured for each module, see [`fortiai-static-questions`](./contents.md#fortiai-static-questions) in the Contents guide.

For advanced usage, including prompting tips, see [Advanced Usage](./advanced-usage.md).

---

## Adding a response as a comment

Save an AI Assistant bot response to the open record as a comment, so the response stays with the record.

1. Open the detail page of the record, for example an alert, a case, or an indicator.
2. Open the AI Assistant bot and enter your request.
3. Under the response, click **Add as comment**.
   The response is added to the record as a comment, posted under your user name and tagged **FortiAI**.
4. To view the comment, click **Comments** in the record header.
   The **Workspace** panel opens on the **Comments** tab.

> [!Note]
> **Add as comment** works only on a record detail page. On a list view, clicking it has no effect.

---

## Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Contents](./contents.md) |
|-----------------------------------------|-------------------------------------------|---------------------------|
