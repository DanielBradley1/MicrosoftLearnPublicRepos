<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Agent Developer Kit commands for declarative agents

Every command in this article is a slash command you enter into the GitHub Copilot Chat pane in Visual Studio Code. Run these commands in the `ess-maker-skills` workspace.

If you forget a command, Copilot Chat lists the available ones when you enter `/` in the chat input. Run `/menu` for the same list with short descriptions.

## Before you start

The required setup depends on the command. Agent operations that need a selected target require the matching workspace setup. Some evaluation-set authoring and review tasks can work locally before an agent is configured. Read the command-specific instructions before assuming that setup, deployment, or a separate push is required.

`/setup` is not listed in `/menu` because it is a setup entry point. Type `/setup` directly when you need to select or prepare an agent workspace. It can replace the local workspace contents, so preserve local work before starting over.

## Commands at a glance

The commands are grouped here by the task you're doing rather than alphabetically.

### Set up and brand the agent

| Command | What it does | When to use it |
| --- | --- | --- |
| `/setup` | Connects to your Power Platform environment, establishes an editable Dev agent, and creates the local workspace. | Use it for first-time setup. It also switches environments, adds another agent, or installs another product. |
| `/landing-page` | Configures supported landing-page sections for the selected agent. | Use it to change supported landing-page content. Agent name and icon are read-only in this command. |

### Author and change content

| Command | What it does | When to use it |
| --- | --- | --- |
| `/create` | Creates a topic, workflow, or evaluation test set locally. | Use it to add a scenario the agent should handle. |
| `/update` | Updates an existing topic, workflow, or evaluation test set locally. | Use it to change trigger phrases, messages, or the flow of an existing scenario. |
| `/review` | Reviews authored topics or evaluation test sets and reports findings. | Use the review that matches the content. Topic review is advisory and does not deploy changes. |
| `/delete` | Deletes a topic, workflow, or evaluation test set. | See [Command availability for declarative agents](#command-availability-for-declarative-agents) before you use this command. |

### Check and evaluate quality

| Command | What it does | When to use it |
| --- | --- | --- |
| `/scan` | Scans your agent files for compile errors and helps you fix them. | Use it after any change. |
| `/evaluate` | Creates, updates, tags, reviews, runs, views results for, or deletes evaluation test sets. | Use it to build a baseline test set, or to confirm quality after a major change. |
| `/run` | Runs an evaluation test set, or views the results of an earlier run. | Use it to execute a test set you already authored. |
| `/test` | Drives a deployed topic and diagnoses faults in its runtime behavior. | Use it when a topic runs but doesn't behave the way you intended. See [Command availability for declarative agents](#command-availability-for-declarative-agents). |
| `/flightcheck` | Runs the readiness checks that apply to the selected agent family and scope. | Use it before a supported deployment, or when you triage an issue. |

### Connect external systems

| Command | What it does | When to use it |
| --- | --- | --- |
| `/connect` | Lists the available integrations and configures the one you choose. | Use it to add a new integration or fix a broken one. |
| `/connect-workday` | Starts the Workday setup flow for a supported Employee Self-Service HR agent. | Use it when that agent needs the supported Workday integration. Follow the administrator handoffs in [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent). |

### Maintain and deploy

| Command | What it does | When to use it |
| --- | --- | --- |
| `/push` | Pushes supported changes after showing a dry run. General topic and workflow deployment is not available for native declarative agents. | Use the evaluation-specific deployment flow for evaluation sets; do not use `/push` to publish native topics or workflows. |
| `/backup-template-configs` | Backs up hybrid Workday reference-data template configurations. | Use it before you make a change that affects Workday reference data. |
| `/restore-template-configs` | Restores hybrid Workday reference-data template configurations from a backup. | Use it to roll back a Workday reference-data change. |
| `/troubleshoot` | Diagnoses connectivity and authentication errors. | See [Command availability for declarative agents](#command-availability-for-declarative-agents) before you use this command. |
| `/menu` | Shows the maker menu. It does not list `/setup` or `/analytics`. | Use it when you forget a command name. |
| `/analytics` | Provides a link to the selected agent's Copilot Studio analytics. | Use it to view the analytics for that agent; it is not an ADK analytics dashboard. |

## Command availability for declarative agents

Some commands aren't fully available yet when your workspace targets a declarative agent. In every case the command tells you so and stops without changing anything.

| Command | Availability | What you see |
| --- | --- | --- |
| `/delete` | Not available | The command reports that deleting components from a declarative agent isn't available in this release, and confirms that no local or remote files were changed. |
| `/troubleshoot` | Not available | The command reports that integration troubleshooting requires the matching product extension guidance, which isn't available in this release. |
| `/test` | Partly available | Drive a topic and check its replies as usual. Server-side diagnostics aren't available, so the command can't localize a fault inside a component. Workflow testing isn't available, and the command stops if you choose a workflow. |

Command behavior depends on the agent family and the operation. In particular, native declarative agents have local-only topic and workflow authoring, a separate evaluation deployment path, and different FlightCheck checks.

Note

These limitations apply to the current release of the Agent Developer Kit for declarative agents.

## Common command sequences

### Add a new topic

```text
/create        <- describe the scenario
/scan          <- catch any compile errors
/review        <- optional advisory check after authoring
```

### Connect an external system

```text
/connect             <- or /connect-workday to start Workday setup directly
/flightcheck         <- check applicable readiness results
```

### Build and run an evaluation test set

```text
/evaluate      <- author and tag the test set
/run           <- run it, then view results
```

The kit reports when results are ready.

### Check a supported deployment

```text
/scan          <- catch local errors
/flightcheck   <- full readiness check
```

### Configure the landing page

```text
/landing-page  <- supported landing-page sections employees see first
```

## FlightCheck readiness check

`/flightcheck` selects checks based on the configured agent family and the scope you choose. A native no-Dataverse declarative agent uses agent identity, authored content, connection readiness, capacity, local-file, and publishing checks. A hybrid or Custom Engine Agent workspace can also run checks for Dataverse, solutions, integrations, and other legacy configuration.

Use the checkpoint ID and remediation details in the generated report. The report identifies manual checks and the next-step role where available. Native checks are read-only. The legacy full runtime-reachability probe can create and then remove a temporary flow, and requires consent before it runs.

To run FlightCheck without the full kit, see [FlightCheck-only mode](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/flightcheck-standalone). Use the checkpoint-specific remediation in the generated report.

## How commands respond

The kit's commands are conversational. When a command needs more information, it asks. You don't need to remember every option:

- "Which agent do you want to work on?" - reply with the name or number
- "What should the trigger phrases be?" - reply in plain English
- "Are you sure you want to delete this?" - reply `yes` or `no`

If your answer is vague, the command asks for more detail instead of guessing.

Commands confirm before making supported remote changes. For command paths that support `/push`, the kit shows the changes and asks you to confirm before sending them to Copilot Studio.

Commands that work on more than one kind of component ask which one you mean. Type `/create`, `/update`, `/delete`, or `/test` with no other text, and the command asks whether you mean a topic, a workflow, or an evaluation test set.

## Where commands look for instructions

The kit's commands rely on the Copilot Chat model picking up context from your workspace. If a command gives a confusing response:

- Make sure your workspace root is `ess-maker-skills` and not the full repo.
- Select a recommended model in Copilot Chat. For specific failure modes, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).

## Related content

| Concept | See |
| --- | --- |
| Employee Self-Service agent components \(topics, workflows, variables\) | [Customize the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize) |
| Workday integration | [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent) |
| ServiceNow integration | [ServiceNow HR and IT for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it) |
| Evaluations | [Agent evaluations for the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations) |
| Publishing | [Publish the Employee Self-Service declarative agent to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-publish) |
