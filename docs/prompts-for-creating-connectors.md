| [Home](../README.md) |
|----------------------|

# Creating a connector through prompts

This guide contains prompts that help you create a connector using a set of prompts sent to the FortiAI's AI Assistant.

1. Login to FortiSOAR.

2. Navigate to **Content Hub**.

3. Click to open the **Create** tab.

4. Click the bot icon

### Example: Create a Criminal IP connector

* **Prompt**:

>   1. _Build connector for Criminal IP product for following actions:_

>    - Get IP Reputation 

>   - Get Domain Reputation "_

* **Expected Outcome**: Displays only alerts whose *Status* is **Investigating**.

![Under investigation alerts filtered](./res/filter-alert-investigating.png)

#### Review results

Verify that the results include only alerts marked as **Investigating**, ensuring that irrelevant alerts are excluded as per the filtering criteria.

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |
