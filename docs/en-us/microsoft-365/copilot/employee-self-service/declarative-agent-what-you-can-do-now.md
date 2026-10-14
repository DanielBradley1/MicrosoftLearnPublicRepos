<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-what-you-can-do-now -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# What you can do now with the Agent Developer Kit for declarative agents

Setup prepared a local workspace for the selected agent. Local changes are not automatically published or available to employees. For native declarative agents, general topic and workflow changes remain local and aren't deployed by `/push`; see [Commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference) for the supported deployment paths.

Here are six ways to continue. Choose the task that fits what you're working on.

## 1. Configure what employees see first

Configure the supported landing-page sections employees see when they open the agent:

```text
/landing-page
```

For the full set of customization options, see [Customize the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize).

## 2. Author your first topic

Tell the kit what scenario you want the agent to handle, and it writes the topic for you:

```text
/create a topic that lets employees ask about their remaining paid time off this year, gets the answer from Workday, and shows the balance with a link to request more.
```

The kit asks any clarifying questions it needs, such as which Workday scenario maps to your tenant and what trigger phrases to use. It then generates the topic and any supporting configuration. Run `/scan` after it finishes.

## 3. Check for errors

After you make local changes, run a scan:

```text
/scan
```

The kit reads your agent files looking for broken variable references, missing workflow bindings, mismatched topics, and similar problems. If it finds any, it helps you fix them one at a time.

Run `/review` for advisory topic feedback. It reports findings and does not deploy changes.

## 4. Generate and run test cases

Build a baseline test set:

```text
/evaluate
```

Evaluation sets use single-response Compare Meaning cases. A set can contain 1 to 100 cases; multi-turn and mixed-method sets are not supported by this flow. Quality review evaluates the test set, not whether the deployed agent passes it.

To run a test set you already authored, or to view the results of an earlier run:

```text
/run
```

The kit reports when the results are ready. For the evaluation workflow, see [Agent evaluations for the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations).

## 5. Connect Workday or ServiceNow

The kit guides supported integration setup. Some steps require an administrator:

```text
/connect
```

The kit lists integration flows available for the selected agent. To start Workday setup directly, run `/connect-workday`. Workday setup is limited to supported Employee Self-Service HR scenarios and includes administrator handoffs. For Workday administrator handoffs, see [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent). For ServiceNow HR and IT, see [the declarative-agent guide](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it).

## 6. Run a predeployment readiness check

Before publishing a supported change, run the readiness check:

```text
/flightcheck
```

FlightCheck runs checks applicable to the selected agent family and scope. It produces a report with results and applicable remediation. The checks differ between native declarative agents and Custom Engine Agent or hybrid workspaces.

## Find the right command later

If you forget a command name, type `/` in the chat input or run `/menu`. For the full command list, see [Commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference).

`/setup` isn't listed in `/menu`, because you normally run it once. To run it again, type `/setup` directly.

## When something doesn't work

If something doesn't work, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).

Note

The `/troubleshoot` command isn't available yet for declarative agents. It reports that integration troubleshooting requires the matching product extension guidance, and stops without changing anything. Use [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started) instead, and see [Commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference) for the other commands that behave differently on declarative agents.

## Related content

The kit is one way to work on your Employee Self-Service agent. The agent itself, its components, integrations, security model, and publishing flow are documented in the broader Employee Self-Service doc set:

- [Introduction to Employee Self-Service Declarative Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview)
- [Customize the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize)
- [Publish the Employee Self-Service declarative agent to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-publish)
- [Agent evaluations for the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations)
- [ADK command availability for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference#command-availability-for-declarative-agents)
