|[Home](../README.md) |
|--------------------------------------------|

# Installation

1. To install a solution pack, click **Content Hub** > **Discover**.
2. From the list of solution pack that appears, search **Fortinet Advisor**.
3. Click the **Fortinet Advisor** solution pack card.
4. Click **Install** on the lower part of the screen to begin the installation.

## Prerequisites

The **Fortinet Advisor** solution pack is not dependent on any other solution pack. However, it is recommended that you have purchased an OpenAI account and have a valid API key to access the OpenAI APIs. Also, ensure that the 'GPT4' model is enabled for use in your OpenAI account. Versions prior of 'GPT4' do not generate correct responses. 

# Configuration

For optimal performance of the **Fortinet Advisor** solution pack, install and configure the following connectors and widget:

- The Fortinet Advisor connector that bundles helper methods, which aid with content generation. 

  >**NOTE**: The Fortinet Advisor connector comes pre-configured. For more details, see the [Fortinet Advisor Connector](https://docs.fortinet.com/document/fortisoar/1.0.0/fortinet-advisor/690/fortinet-advisor-v1-0-0) document.

- The OpenAI connector as Fortinet Advisor uses OpenAI models as a backing LLM.

    - To configure and use the OpenAI connector, see the OpenAI connector document. Note that you must add a configuration for this connector. Also, in case of multiple configurations, ensure that you mark at least one configuration as 'Default', since the solution uses the connector configuration that is marked as 'Default'. For more details, see the [OpenAI Connector](https://docs.fortinet.com/document/fortisoar/2.0.0/openai/706/openai-v2-0-0) document.

- The Fortinet Advisor widget that adds the Advisor bot to the FortiSOAR User Interface.




# Next Steps
| [Usage](./usage.md) | [Contents](./contents.md) |
|---------------------|---------------------------|