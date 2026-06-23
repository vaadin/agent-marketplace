# Vaadin Agent Marketplace

This repository publishes Vaadin's agent plugin marketplace for Claude Code and
Codex.

The marketplace contains one plugin:

- `vaadin-skills` - Vaadin 25 development skills and MCP tools for Java/Flow,
  layouts, components, forms, testing, data access, and reactive state
  management.

The plugin implementation lives in
[`vaadin/agent-skills`](https://github.com/vaadin/agent-skills). This repository
only contains the marketplace metadata that lets Claude Code and Codex discover
and install that plugin.

## Claude Code

### Install

In Claude Code, add the Vaadin marketplace:

```shell
/plugin marketplace add vaadin/agent-marketplace
```

Then install the plugin:

```shell
/plugin install vaadin-skills@vaadin-marketplace
```

You can also browse and install it from `/plugin` by opening the marketplace
browser and selecting `vaadin-skills`.

### Use

The skills and MCP tools activate automatically when you ask Claude Code for
help with Vaadin development. Example prompts:

- "Create a responsive master-detail view in Vaadin Flow"
- "Add Binder validation to this form"
- "Write UI unit tests for this view"
- "Look up the current Vaadin documentation for Grid lazy loading"

### Update

Refresh the marketplace catalog:

```shell
/plugin marketplace update vaadin-marketplace
```

Then update or reinstall `vaadin-skills` from the plugin manager if a newer
version is available.

## Codex

### Install

Add the Vaadin marketplace:

```shell
codex plugin marketplace add vaadin/agent-marketplace --ref main
```

Then install the plugin:

```shell
codex plugin add vaadin-skills@vaadin-marketplace
```

To inspect the available plugin before installing:

```shell
codex plugin list --marketplace vaadin-marketplace --available
```

### Use

Start Codex in a Vaadin project and ask for help with Vaadin development. Codex
will load the relevant Vaadin skills and MCP tools from the installed plugin
when the task matches their descriptions.

Example prompts:

- "Modernize this Vaadin layout for Flow 25"
- "Create a Lit wrapper for this Web Component"
- "Debug this Binder validation issue"
- "Use Vaadin docs to check the recommended Grid API"

### Update

Refresh Git-backed marketplace snapshots:

```shell
codex plugin marketplace upgrade
```

Then reinstall or update `vaadin-skills` if needed.

## Local Marketplace Testing

From a local checkout of this repository, add the marketplace by path:

```shell
claude plugin marketplace add .
codex plugin marketplace add .
```

Install the plugin from the local marketplace:

```shell
claude plugin install vaadin-skills@vaadin-marketplace
codex plugin add vaadin-skills@vaadin-marketplace
```

## Metadata

- Claude Code marketplace metadata:
  [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json)
- Codex marketplace metadata:
  [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json)

Update plugin instructions, skills, MCP definitions, and plugin manifests in
[`vaadin/agent-skills`](https://github.com/vaadin/agent-skills). Update this
repository only when the marketplace catalog itself changes.
