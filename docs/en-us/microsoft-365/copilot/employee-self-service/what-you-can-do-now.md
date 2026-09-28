<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/what-you-can-do-now -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# What you can do now with the Agent Developer Kit

Setup is complete. The kit is connected to your environment and you have a local copy of your ESS agent. Here are five things to try next. Pick the task that fits what you're working on. These options are ordered from simplest to most involved.

## 1. Author your first topic

Tell the kit what scenario you want the agent to handle and it writes the topic for you:

```text
/create a topic that lets employees ask about their remaining paid time off this year, gets the answer from Workday, and shows the balance with a link to request more.
```

The kit asks any clarifying questions it needs \(which Workday scenario maps to your tenant, what trigger phrases to use\), then generates the topic and any supporting configuration. Run `/scan` after it finishes.

For more, see [Customize the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/customize).

## 2. Check for errors

If you make changes \(in the kit or in the Copilot Studio portal\), run a quick health check:

```text
/scan
```

The kit walks your agent files looking for broken variable references, missing workflow bindings, mismatched topics, and similar problems. If it finds any, it walks you through fixes one at a time.

## 3. Generate test cases

Build a baseline test set the [Copilot Studio evaluator](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/evaluations-run-tests) can run against your agent:

```text
/evaluate
```

The kit asks which quality dimensions you want covered \(topic triggering, Responsible AI, sensitive topics, emotional intelligence, ambiguous prompts, integration data, general knowledge\). It then generates CSV files you can upload into the evaluator.

## 4. Wire up Workday or ServiceNow

If your agent doesn't yet talk to your HR or IT system, the kit walks you through end-to-end setup:

```text
/connect workday
```

```text
/connect servicenow
```

The kit verifies prerequisites, walks you through identity setup, captures the values it needs, installs the right extension pack, configures the connection, and runs a smoke test. For the underlying product concepts, see the Workday and ServiceNow articles in this doc set.

## 5. Run a predeployment readiness check

Before you publish to end users, run the full readiness check:

```text
/flightcheck
```

The kit runs 40+ verifications across licenses, environment, identity, integrations, agent files, and publishing. Output is an HTML report you can share with stakeholders. The kit also offers to fix certain issues for you.

## Find the right command later

If you forget a command name, type `/` in the chat input or run `/menu`. For the full command list with one-line descriptions, see [Commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/commands-reference).

## When something doesn't work

The most common stumbles in the first day with the kit are covered in [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started). For interactive help in the moment, run `/troubleshoot`.

## Where to learn more about your agent

The kit is one way to work on your ESS agent. The agent itself, its components, integrations, security model, and publishing flow are documented in the broader Employee Self-Service doc set:

- [Employee Self-Service overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/overview)
- [Customize the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/customize)
- [Publish the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish)
- [Evaluations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/evaluations)
- [Release notes, known issues, and limitations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/known-issues-limitations)
