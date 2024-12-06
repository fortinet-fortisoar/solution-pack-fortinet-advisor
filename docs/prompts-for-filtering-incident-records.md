| [Home](../README.md) |
|----------------------|

# Filtering incidents through prompts

This guide contains prompts for efficiently filtering incidents using the FortiAI Assistant. Each prompt focuses on specific filtering criteria to streamline threat investigation and response. Prompts in this section allow users to retrieve incidents based on various criteria that provide a targeted view of incidents under investigation or requiring immediate attention.

### Example: Retrieve Incidents with ID Greater Than 400

This example demonstrates how to filter incidents based on their ID, allowing users to focus on incidents with an ID value exceeding a specific threshold.

* **Prompt**:  
   > _"Filter out all the incidents with ID greater than 400."_

* **Expected Outcome**:  
   Displays only incidents with an ID greater than 400.

![Incidents with ID greater than 400 filtered](./res/filter-incidents-id-greater-400.png)

### Review Results

Verify that the results include only incidents with an ID greater than 400, ensuring no incidents with a lower ID are included.

### Other examples

Similarly, you can use the following prompts to filter incident records.

1. Give me incidents led by me.
 
2. Give me incidents created in the last 7 days.
 
3. Give me incidents tagged as super, and not led by <user-1>.
 
4. Fetch incidents of type phishing which are in containment phase.

# Next Steps

| [Installation](./setup.md#installation) | [Configuration](./setup.md#configuration) | [Usage](./usage.md) | [Contents](./contents.md) |
| --------------------------------------- | ----------------------------------------- | ------------------- | ------------------------- |
