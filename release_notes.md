# What's New

## Connector Generation

FortiAI now enables connector creation using natural language. By providing inputs such as CURL commands, API details, and configuration parameters, users can generate a fully functional connector that includes:

- Connector configuration
- Auto-generated connector code
- Sample playbooks

You can also upload attachments to assist in connector generation.

## Advanced Playbook Generation

FortiAI now produces more accurate, context-aware playbook blocks tailored to specific use cases. Whether automating standard workflows or designing complex incident response logic, it offers an efficient starting point that reduces manual effort.

Key improvements include:

- Playbook creation from simple prompts or clicks
- Accurate detection of connector step types, operation names, and available inputs
- Identification of steps that require loops for record traversal

### Improved Jinja Expression Selection

FortiAI intelligently selects appropriate Jinja expressions for each playbook step, reducing the need for manual adjustments.

Structured outputs are now supported, with JSON data displayed in a readable JSON editor.

## Configuration Wizard Enhancements

The configuration wizard has been improved to support the following:

- Creation of SOC and Playbook assistants
- Updating assistant instruction sets
- Clearer error messages for scenarios such as:
    - Insufficient permissions
    - Failure during assistant creation or update
    - Missing default connector configuration in single-user setups
    - Unspecified user configuration in multi-user environments