| [Home](../README.md) |
|----------------------|

# Advanced Usage

This page covers information that helps administrators and users get better results from FortiAI.

The chat assistant icon appears at the lower left of the screen.

![Chat assistant icon](./res/icon-chat-assistant.svg)

## Making requests that require planning

Each message you send is evaluated on its own, except a reply to a paused plan, which goes back to Orchestrator. Simple requests (querying, filtering, or summarizing records, answering questions about the open record, or reviewing work that is already complete) are handled directly by the Chat Assistant agent. Requests that cannot be satisfied by a single action, such as following a standard operating procedure, gathering evidence across multiple sources, or coordinating a response, are handed to the **Orchestrator** agent. Orchestrator plans the work, runs it, and returns a single response.

| Request type                                                       | Handled by     |
|--------------------------------------------------------------------|----------------|
| Query, list, filter, or summarize records                          | Chat Assistant |
| Create or update records using known information                   | Chat Assistant |
| Take a single action, such as blocking or enriching one indicator  | Chat Assistant |
| Write out an SOP as text                                           | Chat Assistant |
| Review or explain a completed investigation or SOP                 | Chat Assistant |
| Investigate, correlate, or threat-hunt across multiple sources     | Orchestrator   |
| Follow an SOP, or run a multi-step response objective              | Orchestrator   |
| Coordinate containment or remediation across systems               | Orchestrator   |

Because intent can change during a conversation, a single conversation can move between the two agents more than once. For example, you might ask for an alert to be summarized (Chat Assistant), investigated and contained (Orchestrator), and then ask for the completed investigation to be explained (Chat Assistant).

> [!Note]
> Asking to summarize or review the output of a completed investigation does not start a new one.

The following request is an example of one that Orchestrator plans and runs:

> Using the following SOP, enrich IP `10.10.10.10`.
>
> - Enrich the IP address using available threat intelligence sources.
> - Block the IP address if it is malicious or suspicious.
> - Create or update the corresponding indicator record.

At the end of a plan, Orchestrator reports the overall outcome, such as completed, partially completed, failed, or denied, and lists the actions it performed with the status of each.

A plan can pause and wait for you, in two cases.

| Pause type              | What happens                                                                                              |
|-------------------------|-----------------------------------------------------------------------------------------------------------|
| Clarification requested | A value needed by the plan is missing or ambiguous. Answer the question to continue.                      |
| Approval requested      | A step changes state, and you did not ask for that change directly. Approve or deny the step to continue. |

Remediation steps, such as blocking an indicator, run through the **SOC Response Action** agent as part of an Orchestrator plan.

> [!Caution]
> Approve a remediation step only when you are satisfied that the target and the action are correct. An approved step runs immediately.

> [!Tip]
> Naming the action you want in your own request avoids an approval pause, because the step is no longer one you did not ask for. Only include the action when you intend it to run.

## Prompting tips

Small changes to a prompt improve the quality of generated playbook blocks. Keep the following in mind when you prompt the AI Assistant bot.

- To use a specific integration in a use case, name it in the prompt. For example, use *Get IP Reputation using VirusTotal* instead of *Get IP Reputation*.

  In the second prompt, FortiAI may include any enrichment source, such as IP Quality Score, AlienVault OTX, or VirusTotal. Ensure that any connector named in the prompt is installed on your system.

- To create playbooks that add a record in FortiSOAR, avoid using *Create `<module-name>` record* as the first step. Place it in the step after gathering details from a previous action.

  > For example, use *Fetch Unread Emails from Exchange and create Alert record*.

- To update a record with a value, use *Update `<module name>`*.

  > For example, *Update Alert Severity to Critical* works better than *Increase Alert Severity to Critical*.

- To create playbooks with On Create, On Update, or On Delete triggers, add terms such as *On create, on update, or on delete of `<module name>` record, perform further actions*.

  > For example, *On Create of alert add a comment Hello, Analyst!*

- To create playbooks with manual triggers, use *Manual Trigger on `<module name>`, perform further actions*.

  > For example, *Manually trigger a playbook upon a Phishing type Alert Record to change the status to Investigating.*

- To create playbooks with manual inputs, add terms such as *Prompt the user for further actions*.

  > For example, *Check the reputation of the indicator using VirusTotal and prompt the user for action: either block it or take no action.*

- To create playbooks with decision blocks, use if and else statements.

  > For example, *Check the reputation of the IP using VirusTotal. If it is considered malicious, set the indicator reputation as malicious. If it is considered suspicious, set the indicator reputation as suspicious. Otherwise, set the indicator reputation as good.*

> [!Note]
> For more filtering prompts, see [Prompt examples](./prompt-examples.md).

## Customizing quick prompts

Quick prompts appear in two places:

- In the AI chat window, when a record in a module is open. These questions come from the module's `questions` array.
- On the module's list view. These questions come from the module's `listQuestions` array.

You can modify the quick prompts that ship with the solution pack, add questions to a module that is already configured, or add a new module with its own questions.

For the structure of the `fortiai-static-questions` record, see [`fortiai-static-questions`](./contents.md#fortiai-static-questions) in the Contents guide.

To change the quick prompts, edit the Key Store record named `fortiai-static-questions`:

1. Open the Key Store record named `fortiai-static-questions`.

2. Click **Edit Record**.

3. Make your changes under the parent object `modules`:

   - **Modify an existing question**: Change its `question` or `description` text, or set `enabled` to `false` to hide it without removing it.
   - **Add a question to a configured module**: Add a question object with `question`, `description`, and `enabled` fields to the module's `questions` or `listQuestions` array.
   - **Add a new module**: Add an object keyed by the module's API name, containing `questions`, `listQuestions`, and `fieldsOfInterest`.

4. Save the record.

As an example, add the **Assets** module, whose module API name is `assets`, with the record questions `foo`, `bar`, and `baz` and the list question `qux`, using placeholder text as descriptions. For context, select `id`, `name`, and `description` as fields of interest:

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
    "listQuestions": [
    {
        "enabled": true,
        "question": "qux",
        "description": "Sed do eiusmod tempor incididunt ut labore"
    }
    ],
    "fieldsOfInterest": [
    "id",
    "name",
    "description"
    ]
}
```

When you open a record in the **Assets** module, the three questions `foo`, `bar`, and `baz` appear with their descriptions in the AI chat window.

The question `qux` appears on **Assets** list view.

---

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |