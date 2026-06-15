| [Home](../README.md) |
|---|

# Filtering Indicators Through Prompts

This reference contains prompts for filtering indicator records in FortiSOAR using the AI Assistant bot. Use these prompts to retrieve indicators based on criteria such as type, reputation, or status.

> [!NOTE]
> Filtering operations apply to a single module at a time. Prompts that combine filter criteria across multiple modules are not supported.

---

## Example: Retrieve Indicators of Type URL

Retrieves all indicators whose **Type** is **URL**.

**Prompt:**
> *Give me all indicators of type URL.*

**Expected outcome:** Lists all indicators with a *Type* of **URL**.

Verify that only URL-type indicators are returned and no other indicator types are included.

---

## Additional Prompts

The following prompts can also be used to filter indicator records:

1. *Give me all indicators of type URL or IP.*
2. *Give me all blocked indicators.*
3. *Fetch all the indicators with Good reputation.*
4. *Filter out all the indicators having reputation either Suspicious or Malicious.*

---

## Next Steps

| [Installation](setup.md#installation) | [Configuration](setup.md#configuration) | [Usage](usage.md) | [Contents](contents.md) |
|---|---|---|---|
