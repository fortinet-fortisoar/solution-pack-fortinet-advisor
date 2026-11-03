| [Home](../README.md) |
|----------------------|

# Using the AI Agent Traceability

**AI Agent Traceability** shows every step of the agent run that produced a result. Use it to see how a conclusion was reached, which agent and model handled each step, and where a run slowed down or failed.

Traceability is available from FortiAI v6.1.0 and later, on FortiSOAR v8.0.1 and later.

## Opening the traceability view

The traceability view opens from an investigation result, using the trace identifier recorded for that run.

1. Open the alert whose investigation you want to review.
2. Click the **AI Investigation** tab.
3. In **AI Investigation Details**, open **AI Agent Traceability**.

The view loads the run associated with that result. If a run is still in progress, refresh the view to load the steps completed so far.

> [!Note]
> Users require Read permission on AI Agents and Usage permission on Widgets to open the traceability view.

## Reading the run summary

The summary line reports the shape of the whole run, so you can judge its size before you open individual steps.

| Item              | Description                                              |
|-------------------|----------------------------------------------------------|
| **Total steps**   | The number of steps the run executed.                    |
| **Total run time**| The elapsed time for the run, from first step to last.   |

## Reading the step list

Steps are listed in execution order as an expandable list. A step that called other agents or tools expands to show the steps beneath it, so a long run can be read at the top level first and opened only where it matters.

Select a step to view the following detail.

| Item           | Description                                                                 |
|----------------|-------------------------------------------------------------------------------|
| **Status**     | The outcome of the step.                                                      |
| **Duration**   | The time the step took to complete.                                           |
| **Input**      | The input the step received.                                                  |
| **Output**     | The result the step produced.                                                 |
| **Model**      | The language model used for the step.                                         |
| **Provider**   | The provider of that model.                                                   |
| **Token usage**| The tokens consumed by the step.                                              |
| **MCP server** | The MCP server the step used, where the step called a tool.                   |

> [!Tip]
> Token usage per step shows which part of a run is most expensive. Use it when you tune an agent configuration or choose a reasoning level.

## Finding a step

Long runs produce long step lists. Use the search field to filter the list to steps matching the text you enter, then select a result to open it.

## Refreshing the run

The view shows the run as it stood when it loaded. Refresh the view to load the current state of a run that is still executing.

---

## Next Steps

| [Usage](./usage.md) | [AI Configurations](./ai-configurations.md) | [Troubleshooting](./troubleshooting.md) | [Contents](./contents.md) |
|---------------------|---------------------------------------------|-----------------------------------------|---------------------------|