# Vaadin Agent Marketplace

This repository publishes Vaadin's agent plugin marketplace for Claude Code and
Codex.

The marketplace contains two plugins:

- `vaadin-skills` - Vaadin 25 development skills and MCP tools for Java/Flow,
  layouts, components, forms, testing, data access, and reactive state
  management.
- `vaadin-agent-tools` - Vaadin tools for AI agents to bootstrap, inspect, and
  validate Vaadin projects. Ships a self-contained native CLI (no Node or JVM
  required at runtime) that can scaffold a new Vaadin project from
  start.vaadin.com and includes an Aura/Lumo theme-mixing checker.
  **Experimental** - published for early testing; expect changes.

The plugin implementations live in
[`vaadin/agent-skills`](https://github.com/vaadin/agent-skills) and
[`vaadin/agent-tools`](https://github.com/vaadin/agent-tools). This repository
only contains the marketplace metadata that lets Claude Code and Codex discover
and install those plugins.

## Claude Code

### Install

In Claude Code, add the Vaadin marketplace:

```shell
/plugin marketplace add vaadin/agent-marketplace
```

Then install a plugin:

```shell
/plugin install vaadin-skills@vaadin-marketplace
/plugin install vaadin-agent-tools@vaadin-marketplace
```

You can also browse and install them from `/plugin` by opening the marketplace
browser and selecting a plugin.

### Use

The skills and MCP tools activate automatically when you ask Claude Code for
help with Vaadin development. Example prompts:

- "Bootstrap a new Vaadin project"
- "Create a responsive master-detail view in Vaadin Flow"
- "Add Binder validation to this form"
- "Write UI unit tests for this view"
- "Look up the current Vaadin documentation for Grid lazy loading"
- "Check this project for Aura/Lumo theme mixing"

### Update

Refresh the marketplace catalog:

```shell
/plugin marketplace update vaadin-marketplace
```

Then update or reinstall `vaadin-skills` or `vaadin-agent-tools` from the plugin
manager if a newer version is available.

## Codex

### Install

Add the Vaadin marketplace:

```shell
codex plugin marketplace add vaadin/agent-marketplace --ref main
```

Then install a plugin:

```shell
codex plugin add vaadin-skills@vaadin-marketplace
codex plugin add vaadin-agent-tools@vaadin-marketplace
```

To inspect the available plugins before installing:

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

Then reinstall or update `vaadin-skills` or `vaadin-agent-tools` if needed.

## Local Marketplace Testing

From a local checkout of this repository, add the marketplace by path:

```shell
claude plugin marketplace add ./
codex plugin marketplace add .
```

Install a plugin from the local marketplace:

```shell
claude plugin install vaadin-skills@vaadin-marketplace
claude plugin install vaadin-agent-tools@vaadin-marketplace
codex plugin add vaadin-skills@vaadin-marketplace
codex plugin add vaadin-agent-tools@vaadin-marketplace
```

## Metadata

- Claude Code marketplace metadata:
  [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json)
- Codex marketplace metadata:
  [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json)

Update plugin instructions, skills, MCP definitions, and plugin manifests in the
plugin repositories
([`vaadin/agent-skills`](https://github.com/vaadin/agent-skills),
[`vaadin/agent-tools`](https://github.com/vaadin/agent-tools)). Update this
repository only when the marketplace catalog itself changes.
