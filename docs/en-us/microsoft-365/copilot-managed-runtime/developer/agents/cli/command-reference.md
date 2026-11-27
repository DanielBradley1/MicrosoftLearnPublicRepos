<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/command-reference?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# msagent CLI command reference \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Use the `msagent` CLI to work with Copilot Studio agents from your terminal. This article summarizes the core commands. For the options available on a command, add `--help`.

## Command syntax

```text
msagent <command> [options]
```

For example, show the available commands or get help with deployment:

```powershell
msagent --help
msagent agent deploy --help
```

## Authentication and environments

| Command | What it does |
| --- | --- |
| `msagent auth login` | Signs you in. |
| `msagent auth status` | Shows your saved sign-in information. |
| `msagent auth switch` | Switches accounts. |
| `msagent env list` | Lists available Power Platform environments. |
| `msagent env select <environment-id>` | Selects an environment. |

Start by signing in and choosing your environment:

```powershell
msagent auth login
msagent env list
msagent env select '<environment-id>'
```

Replace `<environment-id>` with the ID of the environment you want to use.

## Agents and deployments

| Command | What it does |
| --- | --- |
| `msagent agent create` | Creates an agent project. |
| `msagent agent init` | Registers an existing agent definition with the CLI. |
| `msagent agent list` | Lists agents. |
| `msagent agent show` | Shows local project or agent configuration. |
| `msagent agent pull` | Downloads changes from Copilot Studio. |
| `msagent agent deploy` | Deploys your agent definition to a configured target. |
| `msagent agent delete` | Deletes an agent resource. Use command help to check the target and options. |
| `msagent deployment` | Provides commands for deployment records and connection configuration. |

To create a Copilot Studio agent project:

```powershell
msagent agent create --agent-type MCSAgent `
  --agent-name 'Contoso Agent' `
  --description 'Contoso helper' `
  --initial-prompt 'Help users with Contoso questions.'
```

For deployment steps, see [Deploy and promote an agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide). For connection setup, see [Working with connections and the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide).

## Common options

| Option | What it does |
| --- | --- |
| `--help` | Shows command help and available options. |
| `--version` | Shows the CLI version. |
| `--json` | Returns structured JSON output. |
| `--no-color` | Turns off colored output. |
| `--non-interactive` | Stops supported operations from opening an interactive sign-in flow. It doesn't sign you in automatically. |

For example, list environments as JSON:

```powershell
msagent env list --json
```

## Telemetry

| Command | What it does |
| --- | --- |
| `msagent telemetry status` | Shows the current telemetry setting. |
| `msagent telemetry disable` | Turns off usage telemetry. |
| `msagent telemetry enable` | Turns on usage telemetry. |
