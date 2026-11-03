| [Home](../README.md) |
|---|

# Building a connector through prompts

The following examples show how to use FortiAI to generate a FortiSOAR connector.

> [!Important]
> API specifications cannot be supplied as file attachments, such as PDF files, Swagger specifications, or Postman collections. Enter the specification in the chat instead, using `curl` commands or JSON.

---

## Example: Criminal IP connector

This example creates a connector for Criminal IP using `curl` commands to provide API details.

1. Enter the following prompt:

   *Build a connector for the product Criminal IP with the following actions:*

   - *Get IP Reputation*
   - *Get Domain Reputation*

   ```
   curl --location --request GET "https://api.criminalip.io/v1/feature/ip/malicious-info?ip=8.8.8.8" \
     --header "x-api-key: <YOUR_API_KEY>"

   curl --location --request GET "https://api.criminalip.io/v1/domain/reports?query=example.com&offset=0" \
     --header "x-api-key: <YOUR_API_KEY>"
   ```

2. Press **Enter**. FortiAI analyzes the input, requests any missing details, such as the authorization type, and generates `info.json`, `operations.py`, and `connector.py`.

   At each stage, you can view individual files by entering a prompt such as *show `operations.py`*.

   - **Expected outcome**: After refreshing the page, the generated connector appears under the **Create** tab.

   - **Reviewing results**: Click **Edit** on the connector tile to review and modify the connector as needed.

   - **Publishing the connector**: Click **Publish** to make the connector available to all users. The connector then appears under the **Manage** tab in the Content Hub, and its associated sample playbooks are added to the Playbooks page.

---

## Example: WiGLE connector

This example creates a connector for WiGLE using `curl` commands to provide API details.

1. Enter the following prompt:

   *Build a connector for the product WiGLE with the following actions:*

   - *Get General Statistics*
   - *Get Country Statistics*
   - *Get Region Statistics*
   - *Get User Statistics*

   ```
   curl --location --request GET "https://api.wigle.net/api/v2/stats/general" \
     --header "Authorization: Basic <YOUR_ENCODED_TOKEN>"

   curl --location --request GET "https://api.wigle.net/api/v2/stats/countries" \
     --header "Authorization: Basic <YOUR_ENCODED_TOKEN>"

   curl --location --request GET "https://api.wigle.net/api/v2/stats/regions?country=US" \
     --header "Authorization: Basic <YOUR_ENCODED_TOKEN>"

   curl --location --request GET "https://api.wigle.net/api/v2/stats/user" \
     --header "Authorization: Basic <YOUR_ENCODED_TOKEN>"
   ```

> [!Tip]
> For the full WiGLE API specification, refer to the [WiGLE Swagger API documentation](https://api.wigle.net/swagger).

2. Press **Enter** and follow the prompts. FortiAI analyzes the input, requests any missing details, and generates the connector files.

   - **Expected outcome**: After refreshing the page, the generated connector appears under the **Create** tab.

   - **Reviewing results**: Click **Edit** on the connector tile to review and modify the connector as needed.

   - **Publishing the connector**: Click **Publish** to make the connector available to all users. The connector appears under the **Manage** tab in the Content Hub, and its associated sample playbooks are added to the Playbooks page.

---

## Example: Logic Monitor connector

This example creates a connector for Logic Monitor using structured text to define API operations.

1. Enter the following prompt:

   > *Build a connector for Logic Monitor using the following details:*
   >
   > **Operation**: Get Alert List
   > **Endpoint**: `/alert/alerts`
   > **HTTP Method**: GET
   > **Parameters**:
   > - **Fields** *(optional)*: Fields to exclude from the response.
   > - **Size** *(optional)*: Number of alerts to return. Default: `50`.
   > - **Offset** *(optional)*: Records to skip. Default: `0`.
   > - **Filter** *(optional)*: Filter query for alert types.
   >
   > **Operation**: Get Device Group List
   > **Endpoint**: `/device/groups`
   > **HTTP Method**: GET
   > **Parameters**:
   > - **Fields** *(optional)*: Fields to exclude from the response.
   > - **Size** *(optional)*: Number of device groups to return. Default: `50`.
   > - **Offset** *(optional)*: Records to skip. Default: `0`.
   > - **Filter** *(optional)*: Filter query for device groups.
   >
   > **Operation**: Get Device List
   > **Endpoint**: `/device/devices`
   > **HTTP Method**: GET
   > **Parameters**:
   > - **Fields** *(optional)*: Fields to exclude from the response.
   > - **Size** *(optional)*: Number of devices to return. Default: `50`.
   > - **Offset** *(optional)*: Records to skip. Default: `0`.
   > - **Filter** *(optional)*: Filter query.
   >
   > **Operation**: Get Device Alerts
   > **Endpoint**: `/device/devices/{id}/alerts`
   > **HTTP Method**: GET
   > **Parameters**:
   > - **ID** *(required)*: Device ID.
   > - **needMessage** *(optional)*
   > - **customColumns** *(optional)*
   > - **Fields** *(optional)*: Fields to exclude from the response.
   > - **Size** *(optional)*: Number of records to return. Default: `50`.
   > - **Offset** *(optional)*: Records to skip. Default: `0`.
   > - **Filter** *(optional)*: Filter query.
   >
   > **Operation**: Get Report List
   > **Endpoint**: `/report/reports`
   > **HTTP Method**: GET
   > **Parameters**:
   > - **Fields** *(optional)*: Fields to exclude from the response.
   > - **Size** *(optional)*: Number of records to return. Default: `50`.
   > - **Offset** *(optional)*: Records to skip. Default: `0`.
   > - **Filter** *(optional)*: Filter query.
   >
   > **Operation**: Get Report by ID
   > **Endpoint**: `/report/reports/{id}`
   > **HTTP Method**: GET
   > **Parameters**:
   > - **ID** *(required)*: Report ID.
   > - **Fields** *(optional)*: Fields to exclude from the response.

2. Press **Enter** and follow the prompts. FortiAI analyzes the input, requests any missing details, and generates the connector files.

     - **Expected outcome**: After refreshing the page, the generated connector appears under the **Create** tab.

     - **Reviewing results**: Click **Edit** on the connector tile to review and modify the connector as needed.

     - **Publishing the connector**: Click **Publish** to make the connector available to all users. The connector appears under the **Manage** tab in the Content Hub, and its associated sample playbooks are added to the Playbooks page.

---

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |