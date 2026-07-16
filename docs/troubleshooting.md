| [Home](../README.md) |
|----------------------|

# Troubleshooting

---

## AI Assistant Bot Not Visible

**Symptom:** The AI Assistant bot does not appear after installing the FortiAI solution pack.

**Resolution:** Force a browser refresh or log out and log back in to your FortiSOAR instance.

---

## AI Assistant Bot Does Not Display the Microphone Button

**Symptom:** The microphone button is missing in the AI Assistant bot.

**Cause:** The voice input feature relies on the `SpeechRecognition` API, which is not supported by Mozilla Firefox.

**Resolution:** Access FortiSOAR using a supported browser (for example, Chrome or Edge).

---

## FortiAI Flyout Does Not Open

**Symptom:** The FortiAI flyout does not open, or FortiAI does not display a response for the playbook outline.

**Resolution:** Verify that the user has the required permissions:

- `Read` and `Usage` permissions on Widgets
- `Read` and `Execute` permissions on Playbooks

---

## FortiAI Cannot Generate Playbook Steps

**Symptom:** FortiAI does not generate playbook steps based on the provided prompt.

**Resolution:**

1. Retry generating the steps.
2. Rephrase the prompt. Refer to [Prompting Tips](./advanced-usage.md#prompting-tips) for guidance.
3. Verify that the Fortinet FortiAI connector is correctly configured and that the associated account has sufficient API quota.

---

## FortiAI Does Not Create or Update a Record

**Symptom:** FortiAI does not create or update a record as specified.

**Resolution:**

1. Prompt FortiAI to confirm the parameters it used:
   > *What parameters did you pass to create/update the field?*
2. Correct any incorrect field API names. Refer to the FortiSOAR module settings for the correct API names.

---

## Response Not as Expected

**Symptom:** FortiAI returns an incorrect or off-topic response.

**Resolution:**

1. Send the same prompt again.
2. Rephrase the prompt to be more specific.

---

## Response Delay

**Symptom:** The prompt text is still visible in the input field, the field appears disabled, and a three-dot loading animation is shown.

**Cause:** The prompt was not transmitted to the LLM.

**Resolution:** Refresh the page and resubmit the prompt.

---

## Connector Configuration Name Does Not Update

**Symptom:** After renaming a Fortinet FortiAI connector configuration, the updated name is not reflected in the wizard.

**Resolution:**

1. Click **Back** to return to the **LLM Configuration** page.
2. Click **Next** to proceed to the **Connector Configuration** page.

---

## FortiAI Error Messages

### Error: Session Conflict — Cannot Add Messages While a Request Is Active

**Symptom:** FortiAI returns an error indicating that the current session is busy or that a prior request is still being processed.

**Resolution:**

- Wait for the active request to complete, then resubmit the prompt.

  OR

- Clear the conversation to reset the session context.

---

### Error: `Run Cancelled Exception` Toast Notification

**Symptom:** A `Run Cancelled Exception` error appears as a toast notification.

**Cause:** This typically occurs when a subsequent prompt is sent before the previous one completes, or when the prompt includes filtering criteria across multiple modules.

> [!NOTE]
> Filtering does not support multiple modules simultaneously. For example, *Fetch alerts with severity high and cases with severity high* in a single prompt is not supported.

**Resolution:**

1. Clear the conversation to reset the context.
2. Simplify the prompt to target a single module at a time.
3. Resubmit the prompt in a new conversation.

---

### Filters Involving DateTime

**Symptom:** DateTime-based filtering returns unexpected or incomplete results.

**Resolution:**

1. **Specify the timezone.** By default, DateTime filters may use UTC. Include the preferred timezone explicitly.
   > *Filter alerts created on 1st December 2024. Consider local timezone.*

2. **Include the year.** Omitting the year can produce inaccurate results.
   > *Filter alerts created on 1st December 2024.*

3. **Cover the full day.** If only a date is specified, the filter may not include all events that day.
   > *Filter alerts created on 1st December 2024. Consider the entire day.*

---

### Field Names in Filters Do Not Update

**Symptom:** Filter field names do not reflect changes after subsequent prompts.

**Resolution:**

1. Refresh the page.
2. Click the clear filter icon to remove the current filter, then click the filter hyperlink in the bot conversation to reapply it.

> [!NOTE]
> This issue was resolved in **FortiSOAR v7.6.1** and later.

---

### FortiAI Response Is Incomplete or Off-Topic

**Symptom:** FortiAI goes off-topic or initiates an incorrect process during connector generation.

**Resolution:** Use the following prompt to redirect FortiAI:
> *Proceed to generate connector by following primary tasks step by step.*

---

### Connector Import Failed

**Symptom:** The connector import process fails due to missing or invalid files.

**Resolution:** Before retrying, prompt FortiAI to regenerate the required files:
1. *Show `info.json` file*
2. *Show Python files*
3. *Import connector now*

---

### Files Missing or Not Displayed

**Symptom:** The generated connector files (`info.json`, `connector.py`, `operations.py`) are not shown in the prompt window.

**Resolution:** Prompt FortiAI to regenerate and display the files:
1. *Generate `info.json` file*
2. *Generate Python files*

---

### FortiAI Calls the Import Connector Function Multiple Times

**Symptom:** FortiAI calls the connector import function repeatedly without user input.

**Resolution:** Use the following prompts to recover:
1. *Show `info.json` file*
2. *Show Python files*
3. *Import connector now*

---

### Connector Imported Automatically Without User Confirmation

**Symptom:** The connector is imported immediately after generation without waiting for the user to confirm.

**Resolution:** Prompt FortiAI to update specific parts of the connector and request a re-import with a **different** version. Alternatively, delete the connector via the Content Hub and prompt FortiAI to import it again.

---

### Error: API Rate Limit or Quota Exceeded

**Symptom:** FortiAI returns an error during connector or playbook generation indicating that an API rate limit or quota has been exceeded.

**Resolution:**

1. Log in to the Fortinet FortiAI platform and navigate to your account's rate limit or quota settings.
2. Review and adjust the configured limits for the applicable model.
3. Save the changes and retry the operation.

> [!NOTE]
> Admin permissions on the Fortinet FortiAI project may be required to modify rate limits.

---

### Error: Indicators Not Unmasked in Playbook Steps

**Symptom:** Indicators in the playbook outline remain masked and are not automatically unmasked in the generated step.

**Resolution:** Manually replace the masked indicator placeholders with their actual values in the playbook step.

---

## Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage) | [Contents](./contents.md) |
|-----------------------------------------|-------------------------------------------|------------------|---------------------------|
