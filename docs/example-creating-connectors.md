| [Home](../README.md) |
|----------------------|

# Building a connector through prompts

> [!Important]
>
> Connector generation currently does not support file attachments (PDF, Swagger specifications, Postman collections) when using the Fortinet FortiAI connector. This is a server-side limitation.
> As a workaround, you can provide API details inline, through chat, as curl commands or JSON request/response structures.
> 

The following is an example that contains prompts to help you create a connector.

1. Navigate to **Automation** > **Connectors** or Content Hub.
    - Alternatively, you can navigate to the **Content Hub** and select **Connectors** as the content type.

2. Click the **Create** tab, and then click the AI Assistant icon to open the FortiAI Window:

    ![](./res/byoc_bot_dialog.png)

3.	Enter appropriate prompts to generate a connector. The prompt must include the connector's purpose, the actions it has to perform, and the API endpoint. The API endpoint can be provided in several formats, including curl commands, JSON data, or attachments in the following formats: `.json`, `.yml`, `.txt`, or `.pdf`.

## Example: Create a Criminal IP connector

In this example, we create a connector for the product Criminal IP with API details as `curl` commands in prompts.

1. Enter the following prompt:

    _Build connector for the product Criminal IP with following actions:_
    - _Get IP Reputation_

    - _Get Domain Reputation_

    `curl --location --request GET "https://api.criminalip.io/v1/feature/ip/malicious-info?ip=8.8.8.8" --header "x-api-key: <YOUR_OpenAI_API_KEY>"`

    `curl --location --request GET "https://api.criminalip.io/v1/domain/reports?query=example.com&offset=0"--header "x-api-key: <YOUR_OpenAI_API_KEY>`

2. Press **Enter** to submit your inputs. *FortiAI* analyzes the provided inputs and prompts you for additional details, such as the authorization type for the product.
 
    FortiAI also displays a summary of the `info.json` file, among other information, and creates `operations.py` and `connector.py`.
    
    At each stage, you can view the generated files by using prompts like *show `operations.py`*. The next prompt explains the process being executed before importing the connector into FortiSOAR&trade;, and offers to import it for you.

### Expected Outcome

After refreshing the page, the generated connector appears under the **Create** tab.

### Reviewing results

Click **Edit** on the connector's tile to review and make changes to the connector, if required.

### Publishing the Connector

Click **Publish** to make the connector available for all users in the system. The published connector appears under the **Manage** tab on **Content Hub**. Associated sample playbooks are added to the Playbooks page.

---

## Example: Create a WiGLE connector

In this example, we create a connector for the product WiGLE with API details as a JSON attachment in the prompts.

1. Enter the following prompt:

    _Build connector for the product WiGLE with following actions:_
    - _Get General Statistics_

    - _Get Country Statistics_

    - _Get Region Statistics_

    - _Get User Statistics_

    Use attached swagger file `WiGLE.json` for API details.

> [!TIP]
> For more specifications and information, refer to the [WiGLE Swagger API Doc](https://api.wigle.net/swagger).

2. Press **Enter** to submit your inputs and follow the prompts. *FortiAI* analyzes the provided inputs and prompts you for additional details, such as the authorization type for the product.
 
### Expected Outcome

After refreshing the page, the generated connector appears under the **Create** tab.

### Reviewing results

Click **Edit** on the connector's tile to review and make changes to the connector, if required.

### Publishing the Connector

Click **Publish** to make the connector available for all users in the system. The published connector appears under the **Manage** tab on **Content Hub**. Associated sample playbooks are added to the Playbooks page.

---

## Example: Create a Logic Monitor connector

In this example, we create a connector for the product Logic Monitor with API details as text.

1. Enter the following prompt:

    > _Build a connector for Logic monitor using the following details:_<br />

    >**Operation**: Get Alert List<br />
    >**Endpoint**: `/alert/alerts`<br />
    >**HTTP Method**: GET<br />
    >**Parameters**:<br />
    >**Fields (Optional)**: Fields to exclude from response.<br />
    >**Size (Optional)**: Alert count to return as response. Default `50`.<br />
    > **Offset (Optional)**: Records to skip when returning the response. Default `0`.<br />
    > **Filter (Optional)**: Filter query for segregating alert types.<br />

    >**Operation**: Get Device Group List<br />
    >**Endpoint**: `/device/groups`<br />
    >**HTTP Method**: GET<br />
    >**Parameters**:<br />
    >**Fields (Optional)**: Fields to exclude from response.<br />
    >**Size (Optional)**: Device group count to return as response. Default `50`.<br />
    > **Offset (Optional)**: Records to skip when returning the response. Default `0`.<br />
    > **Filter (Optional)**: Filter query for segregating alert types.<br />

    >**Operation**: Get Device List<br />
    >**Endpoint**: `/device/devices`<br />
    >**HTTP Method**: GET<br />
    >**Parameters**:<br />
    >**Fields (Optional)**: Fields to exclude from response.<br />
    >**Size (Optional)**: Device count to return as response. Default `50`.<br />
    > **Offset (Optional)**: Records to skip when returning the response. Default `0`.<br />
    > **Filter (Optional)**: Filter query for segregating alert types.<br />

    >**Operation**: Get Device Alerts<br />
    >**Endpoint**: `/device/devices/{id}/alerts`<br />
    >**HTTP Method**: GET<br />
    >**Parameters**:<br />
    >**ID (Required)**: Device ID to retrieve associated alerts
    >**needMessage (Optional)**
    >**customColumns (Optional)**
    >**Fields (Optional)**: Fields to exclude from response.<br />
    >**Size (Optional)**: Device count to return as response. Default `50`.<br />
    > **Offset (Optional)**: Records to skip when returning the response. Default `0`.<br />
    > **Filter (Optional)**: Filter query for segregating alert types.<br />

    >**Operation**: Get Report List<br />
    >**Endpoint**: `/report/reports`<br />
    >**HTTP Method**: GET<br />
    >**Parameters**:<br />
    >**Fields (Optional)**: Fields to exclude from response.<br />
    >**Size (Optional)**: Records to return as response. Default `50`.<br />
    > **Offset (Optional)**: Records to skip when returning the response. Default `0`.<br />
    > **Filter (Optional)**: Filter query for segregating alert types.<br />

    >**Operation**: Get Report by ID<br />
    >**Endpoint**: `/report/reports/{id}`<br />
    >**HTTP Method**: GET<br />
    >**Parameters**:<br />
    >**ID (Required)**: Device ID to retrieve associated alerts
    >**Fields (Optional)**: Fields to exclude from response.<br />

2. Press **Enter** to submit your inputs and follow the prompts. *FortiAI* analyzes the provided inputs and prompts you for additional details, such as the authorization type for the product.
 
### Expected Outcome

After refreshing the page, the generated connector appears under the **Create** tab.

### Reviewing results

Click **Edit** on the connector's tile to review and make changes to the connector, if required.

### Publishing the Connector

Click **Publish** to make the connector available for all users in the system. The published connector appears under the **Manage** tab on **Content Hub**. Associated sample playbooks are added to the Playbooks page.

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |
