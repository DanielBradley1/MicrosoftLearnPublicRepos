<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/commands-reference -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Agent Developer Kit commands reference

Every command in this article is a slash command you enter into the GitHub Copilot Chat pane in Visual Studio Code. Run these commands in the `ess-maker-skills` workspace after you complete [Run your first command](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-3-run-setup).

If you forget a command, Copilot chat lists the available ones when you enter `/` in the chat input. You can also run `/menu` for the same list with short descriptions.

## Commands at a glance

| Command | What it does | When to use it |
| --- | --- | --- |
| `/setup` | Connects to your Power Platform environment, finds your Employee Self-Service agent, and saves a local copy. | Use it for first-time setup. It also switches environments or adds a second agent later. |
| `/connect` | Connects an external system, either Workday or ServiceNow, end-to-end. | Use it to add a new integration or fix a broken one. |
| `/create` | Builds a new topic or workflow from a plain English description. | Use it to add a new scenario that the agent can handle. |
| `/update` | Modifies an existing topic or workflow. | Use it to change trigger phrases, messages, or the flow of an existing scenario. |
| `/delete` | Removes a topic or workflow, with safety checks for downstream references. | Use it when a scenario is no longer needed. |
| `/scan` | Checks your agent files for errors and walks you through fixes. | Use it after any change and before you push. |
| `/evaluate` | Generates test cases in the CSV format that the Copilot Studio evaluator expects. | Use it to build a baseline test set, or to confirm quality after a major change. |
| `/push` | Sends your local changes to Copilot Studio. | Use it when you're ready to apply local edits to the live agent. |
| `/flightcheck` | Runs a predeployment readiness check across licenses, environment, integrations, and agent files. | Use it before you publish, or when you triage a customer issue. |
| `/troubleshoot` | Provides interactive triage for common problems. | Use it when something doesn't work and you want guided help. |
| `/menu` | Shows the list of available commands. | Use it when you forget a command name. |

## Common command sequences

### Add a new topic from scratch

```text
/create        <- describe the scenario
/scan          <- catch any compile errors
/push          <- send the change to Copilot Studio
```

### Wire up an integration

```text
/connect servicenow      <- or /connect workday
/flightcheck             <- confirm the integration is healthy
```

### Get ready to publish

```text
/scan          <- catch local errors
/flightcheck   <- comprehensive readiness check across 40+ verifications
/push          <- send any final changes
```

### Generate test cases for the evaluator

```text
/evaluate      <- pick which dimensions to generate
```

Upload the resulting CSV files to the [Copilot Studio evaluator](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/evaluations-run-tests) in your agent's analytics view.

## FlightCheck readiness check

`/flightcheck` runs a comprehensive predeployment readiness check across more than 40 verifications. Run it before you publish to end users, or when you triage a customer issue and want a single report that checks the most common causes.

The check covers:

- **Licenses** - confirms the required licenses and entitlements are in place.
- **Environment** - validates the Power Platform environment and its configuration.
- **Identity** - checks the sign-in account and the permissions it carries.
- **Integrations** - verifies that connected systems, such as Workday and ServiceNow, are wired up and reachable.
- **Agent files** - scans your local topics and workflows for errors.
- **Publishing** - confirms the agent is ready to publish.

FlightCheck produces an HTML report you can share with stakeholders. When it finds an issue it can resolve, it offers to fix the issue for you.

```text
/flightcheck
```

For the conceptual background on what FlightCheck validates, see [Publish the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish).

## How commands respond

The kit's commands are conversational. When a command needs more information, it asks. You don't need to remember every option:

- "Which agent do you want to work on?" - reply with the name or number
- "What should the trigger phrases be?" - reply in plain English
- "Are you sure you want to delete this?" - reply `yes` or `no`

If your answer is vague, the command asks for more detail instead of guessing.

## Where commands look for instructions

The kit's commands rely on the Copilot Chat model picking up context from your workspace. If a command gives a confusing response:

- Make sure your workspace root is `ess-maker-skills` and not the full repo \(see [Step 1](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-1-clone-the-kit)\).
- Make sure you select a [recommended model](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-2-install-github-copilot#pick-a-recommended-model).
- Rerun the command. Models occasionally fail to respond.

For specific failure modes, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).

## Where to learn more about each command

The Copilot Studio doc set covers the broader concepts that the commands operate on. When you want the conceptual background:

| Concept | See |
| --- | --- |
| Employee Self-Service agent components \(topics, workflows, variables\) | [Customize the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/customize) |
| Workday integration | [Simplified Workday integration](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-simplified-setup) or [Workday integration](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday) |
| ServiceNow integration | [ServiceNow HRSD and ITSM integration](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/servicenow-hrsd-itsm) |
| Evaluations | [Evaluations for the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/evaluations) |
| Publishing | [Publish the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish) |

## Next steps

- Try `/create` from [What you can do now](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/what-you-can-do-now)
- If a command doesn't behave as expected, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started)
