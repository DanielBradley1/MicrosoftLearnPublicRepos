<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-github-copilot?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Quickstart: Build a Microsoft Copilot Managed Runtime app with GitHub Copilot \(preview\)

\[This article is prerelease documentation and is subject to change.\]

This quickstart shows you how to go from a natural-language prompt to a deployed Copilot Managed Runtime app by using the [GitHub Copilot CLI](https://docs.github.com/copilot/github-copilot-in-the-cli/about-github-copilot-in-the-cli) with the Copilot Managed Runtime plugin. The Copilot agent plans the app, runs the Microsoft Copilot Managed Runtime CLI \(`@microsoft/managed-apps-cli`\) commands, drives the Git workflow, and asks you to confirm at each step, all from your terminal of choice.

## Prerequisites

- [Node.js](https://nodejs.org/) \(LTS version\) and [Git](https://git-scm.com/downloads) installed, with a terminal of your choice.
- GitHub Copilot enabled for your account or tenant. To set up Copilot, see [Get started with GitHub Copilot](https://docs.github.com/copilot/getting-started-with-github-copilot).
- The [GitHub Copilot CLI](https://docs.github.com/copilot/github-copilot-in-the-cli/installing-github-copilot-in-the-cli) installed and authenticated. This quickstart uses the standalone `copilot` CLI, which supports plugins via `/plugin` slash commands.

  Tip

  The Copilot Managed Runtime plugin also works with [Claude Code](https://www.anthropic.com/claude-code) and other coding agents through [Open Plugins](https://open-plugins.com/). This quickstart uses GitHub Copilot for the step-by-step walkthrough, but the same plugin, prompts, and CLI commands apply; start a session with `claude` instead of `copilot` and continue with the rest of the steps as written.

You don't need to install the Copilot Managed Runtime CLI separately; the plugin checks and installs dependencies for you the first time you run a skill.

## Process

The following table describes the process to follow.

| Order | Step | Description |
| --- | --- | --- |
| 1 | [Install the Copilot Managed Runtime plugin](#install-the-copilot-managed-runtime-plugin) | Starts the Copilot CLI, adds the Copilot Managed Runtime plugin marketplace, and installs the Copilot Managed Runtime plugin. |
| 2 | [Invoke the create-app skill](#invoke-the-create-app-skill) | Starts the create-app skill so Copilot can guide the rest of the workflow. |
| 3 | [Describe the app in natural language](#describe-the-app-in-natural-language) | Provides the app requirements so the agent can validate prerequisites and generate a plan. |
| 4 | [Approve the plan and watch the agent build](#approve-the-plan-and-watch-the-agent-build) | Reviews the proposed steps and lets the agent scaffold the app, set up the environment, and run locally. |
| 5 | [Push and preview](#push-and-preview) | Confirms the push so the agent commits the work and opens the hosted preview build. |
| 6 | [Deploy to live](#deploy-to-live) | Promotes the app from preview to the live experience. |
| 7 | [Share the app](#share-the-app) | Shares the deployed app with another user. |

## Install the Copilot Managed Runtime plugin

Start the Copilot CLI in any terminal:

```bash
copilot
```

In the Copilot session, add the Copilot Managed Runtime plugin marketplace and install the plugin:

```text
/plugin marketplace add microsoft/Managed-Apps
```

```text
/plugin install microsoft-managed-apps@Managed-Apps
```

The plugin adds apps skills to Copilot: create app, add connector, push and preview, deploy, and share. It also orchestrates `ms` CLI commands on your behalf.

Close the terminal window after installation, then re-open Copilot CLI with:

```bash
copilot
```

## Invoke the create-app skill

In your new Copilot session, run the create-app skill:

```text
/microsoft-managed-apps:create-app
```

Copilot acknowledges the skill and prompts you to describe the app you want.

## Describe the app in natural language

Type a natural-language description of the app. For example:

> *Create an app to visualize my organization's hierarchy as represented in Microsoft Entra. Show the hierarchy as a display tree where the leader of the company is at the top, with their direct reports below. Add a layer for each level of employees. The tree initially shows the top two layers. When a person is selected, the app refreshes to show who reports to them.*
> 
> *For each user, include a "view profile" button. When clicked, show full name, title, work location, email, and phone number.*

Before doing anything else, the agent:

- Validates needed prerequisites by checking dependencies, installing anything missing, and confirming you're authenticated against the right tenant.
- **Plans the app.** It identifies the needed data sources, the UI, and the interactions, then presents the plan for your approval. Copilot doesn't jump straight to code. Review each step the agent proposes before approving. You stay in control of which actions run.

## Approve the plan and watch the agent build

When you approve the plan, the agent runs the Copilot Managed Runtime CLI to:

- Create the app record and provision a platform-managed Git repository, giving you source control out of the box with no extra setup.
- Set up a developer environment. Every developer \(and every coding agent\) lands in a secure, policy-managed sandbox with a Microsoft-configured baseline. Administrators can validate and customize the baseline as needed.
- Scaffold the project files, install dependencies, and start the local dev server.
- Open the app in your browser so you can verify it locally.

## Push and preview

The agent asks whether you're ready to push and preview. Confirm, and the agent runs `git add`, `git commit`, and `git push` under the hood. The platform-managed repo uses standard Git intentionally; coding agents already understand Git workflows, and the platform builds from real commits in a real repository.

Your browser opens to the preview URL which triggers a platform build. When the build completes and you press **Refresh**, the preview loads the app running under the same enterprise governance \(Microsoft Entra ID, Conditional Access, and DLP\) that applies in production.

## Deploy to live

When the preview looks right, ask the agent to deploy:

```text
deploy app
```

The agent runs [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy) and returns the live URL. Your app is now running for users as an app, governed by Entra ID, Conditional Access, and DLP, with telemetry and operational health flowing into the admin center.

## Share the app

Ask the agent to share with a coworker, in natural language:

```text
share the app with someone@contoso.com
```

The agent invokes the share skill and confirms when the share completes.

Congratulations! You built, deployed, and shared an app end-to-end by using GitHub Copilot. You and your users can now view and play the app at [https://managedapps.cloud.microsoft/](https://managedapps.cloud.microsoft/).

## What just happened?

You didn't scaffold a project, wire up data, or run infrastructure commands. You described what you wanted. The Copilot agent ran the Copilot Managed Runtime CLI; the Copilot Managed Runtime platform provided identity, data governance, build and deploy infrastructure, audit trail, operational telemetry, and secure sharing. That's the value the platform delivers around your code, so you can stay focused on describing the app you want to build.
