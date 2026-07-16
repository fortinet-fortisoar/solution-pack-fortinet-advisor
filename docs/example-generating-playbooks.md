| [Home](../README.md) |
|----------------------|

# Generating Playbooks Using Prompts

The following prompts can be submitted to FortiAI to generate playbooks. Each prompt corresponds to a common SOC use case. Submit the prompt in the Playbook Designer input field and follow the on-screen steps.

For general guidance on playbook generation, see [Generating Playbooks](./usage#generating-playbooks) in the Usage guide.

---

## Example: Handling Suspicious Email Alerts

> When an alert is created of type "Suspicious Email":
>
> 1. Send an acknowledgement email to the sender.
> 2. Mark the alert status as "Investigation."
> 3. If email spoofing is detected, add the "Spoofing" tag. Otherwise, add the "No Spoofing" tag.
> 4. Find related indicators of type URL.
> 5. Check the URL rating in FortiSandbox.
> 6. Ask the user if it is a "Drive-By Download." If yes, add the tag "Drive By Download." If no, add the tag "Not Drive By Download."
> 7. Ask the user if the alert is about phishing.
>    - If phishing: mark the alert type as "Phishing" and send a suspicious response email to the sender.
>    - If not phishing: mark the email classification as "Non-Phishing," set the severity to "Low," and send a closure response email to the reporter.

---

## Example: Automated Alert Creation from Unread Emails

> 1. Get all unread emails from Exchange.
> 2. Create an alert record for each unread email.
> 3. Reply to each email with a thank-you message.
> 4. Change the newly created alerts' status to "Investigating."

---

## Example: Enrich IP Indicators Using VirusTotal

> Upon the creation of an indicator of type IP Address:
>
> - Search the IP in VirusTotal.
> - Retrieve and record the risk score of the IP.

---

## Example: Blocking Malicious Indicators

> 1. Trigger manually on an indicator if its reputation is "Malicious."
> 2. Block the indicator in FortiGate to prevent threats.
> 3. Update the indicator's status to "Blocked."

---

## Example: Sending Alert Details via Email

> Manually select an alert and send its details to `noreply@example.com`.

---

## Example: IP Reputation Assessment

> Upon the creation of an indicator:
>
> - Check the IP's reputation using VirusTotal.
>   - If malicious, set the indicator reputation as "Malicious."
>   - If suspicious, set the indicator reputation as "Suspicious."
>   - Otherwise, set the indicator reputation as "Good."

---

## Example: CVE Record Enrichment

> Upon the creation of a CVE record:
>
> - Retrieve the latest report from NIST NVD.
> - Obtain the EPSS score.
> - Update the CVE record accordingly.

---

## Example: Sandbox Analysis for High-Risk Files

> If a file indicator's risk is "High" or above:
>
> - Send the sample to the sandbox for analysis.

---

## Example: Asset Identification

> Find and identify the asset related to IP address `10.10.10.10`.

---

## Example: File Download from URL

> Download a file from a given URL and save it as an attachment.

---

## Example: Attachment Analysis

> Analyze the downloaded attachment using both a sandbox environment and VirusTotal.

---

## Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage) | [Contents](./contents.md) |
|-----------------------------------------|-------------------------------------------|------------------|---------------------------|
