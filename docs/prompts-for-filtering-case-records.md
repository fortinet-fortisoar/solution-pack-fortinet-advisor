| [Home](../README.md) |
|---|

# Filtering Cases Through Prompts

This reference contains prompts for filtering case records in FortiSOAR using the AI Assistant bot. Use these prompts to retrieve cases based on criteria such as ID, status, type, date range, or assigned user.

> [!NOTE]
> Filtering operations apply to a single module at a time. Prompts that combine filter criteria across multiple modules (for example, cases and alerts simultaneously) are not supported.

---

## Example: Retrieve Cases with ID Greater Than 400

Retrieves cases whose **ID** is greater than a specified value.

**Prompt:**
> *Filter out all the cases with ID greater than 400.*

**Expected outcome:** Displays only cases with an ID value greater than 400.

Verify that no cases with an ID of 400 or lower are included in the results.

---

## Additional Prompts

The following prompts can also be used to filter case records:

1. *Give me cases led by me.*
2. *Give me cases created in the last 7 days.*
3. *Give me cases tagged as `super`, and not led by `[user name]`.*
4. *Fetch cases of type phishing which are in the containment phase.*

---

## Next Steps

| [Installation](setup.md#installation) | [Configuration](setup.md#configuration) | [Usage](usage.md) | [Contents](contents.md) |
|---|---|---|---|
