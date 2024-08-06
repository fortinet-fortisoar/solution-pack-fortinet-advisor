# What's New

## Support for FortiAI GenAI Assistant

FortiAI is a context-aware GenAI security assistant that transforms how security professionals operate and interact with threat alerts. It makes complex analysis and response tasks more intuitive and accessible. Analysts can easily issue commands for analyzing data, identifying threats, and performing remediation tasks within FortiSOAR.

The power of natural language processing allows even those with limited technical training to quickly investigate potential threats. The AI capabilities accelerate review and response cycles and empower security teams to handle detection, analysis, and mitigation tasks with unprecedented speed and accuracy.

FortiAI empowers security teams and addresses the evolving challenges of the modern threat landscape with several key new features:

- The AI assistant now understands and responds to context-sensitive conversations, performing SOC tasks directly within the conversation. This transforms complex security operations into straightforward dialogue:
  - Block or enrich indicators
  - Escalate alerts to an incident
  - Create a war room for a given incident
  - Create or update FortiSOAR module records
  - Correlate records
  - Generate a FortiSOAR playbook
  - Create Jinja expressions and Regex to speed up playbook development in FortiSOAR
  - Navigate to a FortiSOAR module such as Alerts, Incidents, or Indicators
  - Navigate to a specific record in a FortiSOAR module

- The bot asks questions if it needs more information or context to perform a task. For example, when blocking an indicator, it requests the indicator's value, type, and reason for blocking.

>[!Note]
>The bot honors RBAC (Role-based Access Control) settings are when executing tasks requested in the conversation.

- The bot is not limited to the aforementioned SOC tasks and can assist in investigations by asking cybersecurity questions.

- The bot holds conversations to understand requirements and generate a more targeted playbook. The experience is streamlined, allowing users to engage with the bot during the creation of a playbook outline, and making it easier to modify the outline by adding, updating, or removing steps.

- Previous conversations remain in the conversation window and provide context to the bot until users clear the conversation. Conversations persist throughout repeated logins and logouts.

- With the bot's enhanced understanding of natural language, it derives its operating modes from the conversation, making the Playbook Blocks and Conversation Mode, unnecessary.

>[!Note]
>Sensitive data is still actively masked in all conversations with the LLM.

- Updated the conversation and playbook models to the following:
  - `gpt-4o-mini-2024-07-18`
  - `gpt-4o-mini`
  - `gpt-4o-2024-05-13`
  - `gpt-4-turbo-2024-04-09`

- The playbook collection *10 - SP - Fortinet Advisor* has been renamed to **10 - SP - FortiAI**.

- The following playbooks have been deprecated, as these actions can be performed by the bot without triggering any of these playbooks:
  - Converse with LLM
  - Generate WorkPlan for User Inputs
  - Get Alert Summary
  - Get Incident Summary
  - Get Alert Response Plan
  - Get Incident Response Plan
  - Get Alert Report
  - Get Incident Report
  - Get Alert MITRE Insight
  - Get Incident MITRE Insight

>[!Note]
>Delete these playbooks manually when upgrading from an older **FortiAI** version.