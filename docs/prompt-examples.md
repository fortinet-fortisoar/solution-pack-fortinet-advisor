| [Home](../README.md) |
|----------------------|

# Prompt examples

This reference contains example prompts for filtering alert, case, and indicator records in FortiSOAR using the AI Assistant bot. Each section lists some of the more complex prompts that combine multiple filter criteria, or that group, sort, and summarize the results.

> [!Note]
> Filtering operations apply to a single module at a time. Prompts that combine filter criteria across multiple modules (for example, alerts and cases simultaneously) are not supported.

> [!Note]
> These prompts read the fields and relationships already on your records. Results depend on what your modules contain. If a requested field is not available, the bot reports it instead of inventing a value. To enrich an indicator or update a record, ask for it in a separate prompt.

---

## Alert records

The following examples filter, group, and summarize alerts.

### Example: combining severity, status, type, date range, and source IP

Retrieves alerts filtered by multiple criteria at once.

**Prompt:**
> *Show me all alerts where the severity is either high or critical, the status is open or in progress, and the type is malware or phishing. The alerts should have been created within the last 7 days, and the source IP should start with `192.168.1`.*

**Expected outcome:** Displays only alerts matching all of the specified severity, status, type, creation-period, and source-IP criteria.

Verify that every returned alert satisfies all the combined conditions.

---

### Example: excluding records by type

Retrieves alerts of one status while excluding certain types.

**Prompt:**
> *List all in-progress alerts, excluding those of the phishing or suspicious type.*

**Expected outcome:** Displays only in-progress alerts whose *Type* is neither **Phishing** nor **Suspicious**.

Verify that no phishing or suspicious alerts are included in the results.

---

### Example: status report with a recommended first alert

Retrieves recent high-severity alerts, summarizes their status, and recommends which alert to review first.

**Prompt:**
> *Give me a status report of high-severity alerts created in the last 24 hours and recommend which alert I should look at first.*

**Expected outcome:** Displays high-severity alerts created in the last 24 hours with their current status, and recommends one alert to review first, based on fields such as severity, age, and status.

Verify that the recommendation refers only to fields present on the returned alerts.

---

### Example: grouping unresolved alerts by severity

Retrieves your unresolved alerts, groups them, and calculates how long each has been open.

**Prompt:**
> *List all unresolved alerts assigned to me, grouped by severity, and show how long each alert has been open.*

**Expected outcome:** Displays unresolved alerts assigned to the current user, grouped by *Severity*, with the time each alert has been open.

Verify that each open time matches the alert's creation date.

> [!Tip]
> The **Try Asking** panel in the AI Assistant bot offers the last two prompts in this section.

---

## Case records

The following examples filter and summarize cases.

### Example: combining tags and assignment

Retrieves cases filtered by tag while excluding cases led by a specific user.

**Prompt:**
> *Give me cases tagged as `super`, and not led by `[user name]`.*

**Expected outcome:** Displays only cases tagged **super** whose lead is not the specified user.

Verify that no cases led by the specified user are included in the results.

---

### Example: combining type and phase

Retrieves cases filtered by both type and lifecycle phase.

**Prompt:**
> *Fetch cases of type phishing which are in the containment phase.*

**Expected outcome:** Displays only cases with a *Type* of **Phishing** that are currently in the **Containment** phase.

Verify that only phishing cases in the containment phase are returned.

---

### Example: status report of open cases

Retrieves open cases of the highest severities with their case lead, age, and status.

**Prompt:**
> *Give me a status report of open critical and high-severity cases, showing the case lead, age, and current status.*

**Expected outcome:** Displays open cases with a *Severity* of **Critical** or **High**, with the **Case Lead**, age, and current status of each case.

Verify that only open critical and high-severity cases are returned.

---

### Example: finding cases without a case lead

Retrieves recent cases that have no case lead, in priority order.

**Prompt:**
> *List cases created in the last 7 days that have no case lead, sorted by severity and creation time.*

**Expected outcome:** Displays cases created in the last 7 days that have no **Case Lead**, sorted by *Severity* and then by creation time.

Verify that no cases with a case lead are included in the results.

---

## Indicator records

The following examples filter and group indicators.

### Example: filtering by multiple indicator types

Retrieves indicators of more than one type.

**Prompt:**
> *Give me all indicators of type URL or IP.*

**Expected outcome:** Lists all indicators with a *Type* of **URL** or **IP**.

Verify that only URL and IP indicators are returned and no other indicator types are included.

---

### Example: filtering by reputation

Retrieves indicators whose reputation matches any of the specified values.

**Prompt:**
> *Filter out all the indicators having reputation either Suspicious or Malicious.*

**Expected outcome:** Lists all indicators with a *Reputation* of **Suspicious** or **Malicious**.

Verify that only indicators with the specified reputations are returned.

---

### Example: grouping recent malicious indicators by type

Retrieves recent malicious indicators, grouped by type, with their reputation and last-seen time.

**Prompt:**
> *Show me all indicators marked malicious that were created in the last 7 days, grouped by indicator type, with reputation and last-seen time.*

**Expected outcome:** Lists indicators with a *Reputation* of **Malicious** created in the last 7 days, grouped by *Type*, with the reputation and last-seen time of each.

Verify that only malicious indicators from the last 7 days are returned.

---

### Example: finding indicators with no linked records

Retrieves suspicious or malicious indicators that are not linked to any alert or case.

**Prompt:**
> *List indicators marked suspicious or malicious that have no associated alerts or cases, sorted by reputation and most recent activity.*

**Expected outcome:** Lists indicators with a *Reputation* of **Suspicious** or **Malicious** that have no linked alerts or cases, sorted by reputation and then by most recent activity.

Verify that none of the returned indicators are linked to an alert or a case.

---

## Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
|-----------------------------------------|-------------------------------------------|---------------------|---------------------------|
