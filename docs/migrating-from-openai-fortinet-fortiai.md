| [Home](../README.md) |
|----------------------|


# Migrating from OpenAI to Fortinet FortiAI Connector

The following section helps migrate from OpenAI as the primary LLM to Fortinet FortiAI.

## Step 1: Update the `fortiai-configurations` Keystore Record

Edit the **`fortiai-configurations`** keystore record and add the following JSON:

> [!Important]
>  
> The **`fortinet-fortiai-proxy`** configuration must be added as the **first entry (index 0)** in the `llmIntegrations` array.
> 

```json
{
  "llmIntegrations": [
    {
      "name": "fortinet-fortiai-proxy",
      "title": "fortinet-fortiai-proxy",
      "modelList": [
        "AI_MODEL_MEDIUM",
        "AI_MODEL_LARGE",
        "AI_MODEL_LOCAL"
      ]
    },
    {
      "name": "openai",
      "title": "OpenAI",
      "modelList": [
        "gpt-4o-mini",
        "gpt-4o-mini-2024-07-18",
        "gpt-4o-2024-05-13",
        "gpt-4-turbo-2024-04-09"
      ]
    }
  ],
  "isMultiConfigAvailable": false,
  "pastConversationMsgLimit": 20
}
```
## Step 2: Re-run the Configuration Wizard

1. Navigate to **Content Hub** > **FortiAI**.
2. Click the button **Configure** to re-run the **Configuration Wizard**.
3. When prompted, select the **LLM Integration** as **`fortinet-fortiai-proxy`**.
4. Complete the wizard to apply the updated configuration.

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |
