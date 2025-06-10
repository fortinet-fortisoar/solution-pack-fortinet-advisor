| [Home](../README.md) |
|----------------------|

# Generating Playbooks Using Prompts

## Introduction

This document provides structured prompts that can be submitted to FortiAI to automatically generate playbooks. These playbooks aim to accelerate the development of automated workflows for SOC (Security Operations Center) analysts, reducing manual effort and ensuring consistency in threat detection and response.

By following these prompts, analysts and engineers can quickly create actionable automation tasks without needing to design workflows manually.

---

## Playbook Generation Prompts

### Example: Handling Suspicious Email Alerts

Send the following prompt to FortiAI:

> When an alert is created of type "Suspicious Email":
> 1. Send an acknowledgement email to the sender.
> 2. Mark the alert status as "Investigation."
> 3. If you find email spoofing:
>    - Add the "Spoofing" tag.
>    - Otherwise, add the "No Spoofing" tag.
> 4. Find related indicators of type URL.
> 5. Check the URL rating in FortiSandbox.
> 6. Ask the user if it is a "Drive-By Download":
>    - If yes, add the tag "Drive By Download."
>    - If no, add the tag "Not Drive By Download."
> 7. Ask the user if the alert is about phishing:
>    - If phishing:
>       - Mark the alert type as "Phishing."
>       - Send a suspicious response email to the sender.
>    - If not phishing:
>       - Mark the email classification as "Non-Phishing."
>       - Set the severity to "Low."
>       - Send a closure response email to the reporter.

---

### Example: Automated Alert Creation from Unread Emails

Send the following prompt to FortiAI:

> 1. Get all unread emails from Exchange.
> 2. Create an alert record for each unread email.
> 3. Reply to each email with a thank-you message.
> 4. Change the newly created alerts' status to "Investigating."

---

### Example: Enrich IP Indicators Using VirusTotal

Send the following prompt to FortiAI:

> Upon the creation of an indicator of type IP Address:
> - Search the IP in VirusTotal.
> - Retrieve and record the risk score of the IP.

---

### Example: Blocking Malicious Indicators

Send the following prompt to FortiAI:

> 1. Trigger manually on an indicator if its reputation is "Malicious."
> 2. Block the indicator in FortiGate to prevent threats.
> 3. Update the indicator’s status to "Blocked."

---

### Example: Sending Alert Details via Email

Send the following prompt to FortiAI:

> Manually select an alert and send its details to `noreply@example.com`.

---

### Example: IP Reputation Assessment

Send the following prompt to FortiAI:

> Upon the creation of an indicator:
> - Check the IP’s reputation using VirusTotal.
>   - If malicious, set the indicator reputation as "Malicious."
>   - If suspicious, set the indicator reputation as "Suspicious."
>   - Otherwise, set the indicator reputation as "Good."

---

### Example: CVE Record Enrichment

Send the following prompt to FortiAI:

> Upon the creation of a CVE record:
> - Retrieve the latest report from NIST NVD.
> - Obtain the EPSS score.
> - Update the CVE record accordingly.

---

### Example: Sandbox Analysis for High-Risk Files

Send the following prompt to FortiAI:

> If a file indicator's risk is "High" or above:
> - Send the sample to the sandbox for analysis.

---

### Example: Asset Identification

Send the following prompt to FortiAI:

> Find and identify the asset related to IP address `10.10.10.10`.

---

### Example: File Download from URL

Send the following prompt to FortiAI:

> Download a file from a given URL and save it as an attachment.

---

### Example: Attachment Analysis

Send the following prompt to FortiAI:

> Analyze the downloaded attachment using both a sandbox environment and VirusTotal.

---

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |
