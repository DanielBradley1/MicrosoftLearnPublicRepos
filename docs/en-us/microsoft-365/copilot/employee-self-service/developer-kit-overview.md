<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/developer-kit-overview -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Customize your Employee Self-Service agent with the Agent Developer Kit

The Employee Self-Service Agent Developer Kit lets you customize your Employee Self-Service agent through GitHub Copilot Chat in Visual Studio Code. You describe what you need in plain English, and the kit translates that into topics, workflows, and configuration.

You don't need to be a developer. You don't need to know how Power Platform or Copilot Studio work under the hood. You do need:

- A computer where you can install Visual Studio Code
- A GitHub Copilot subscription
- Access to your organization's Power Platform environment with Employee Self-Service installed

## Pick your install path

There are a few ways to install the kit. Pick the one that fits your setup:

| Option | Best for | Guide |
| --- | --- | --- |
| **One-shot installer** \(Windows\) | Fastest path on a Windows machine where you can install software. One PowerShell command installs the toolchain, clones the kit, and opens Visual Studio Code. | [Install with the one-shot installer](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-installer) |
| **GitHub Codespaces** | Browser-only, no local install. Works on any operating system. Use this option when you can't install software on your machine, or when you want to try the kit before committing to a local install. | [Install with GitHub Codespaces](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-codespaces) |
| **Manual install** | You want control over what gets installed where, or you're on macOS or Linux and you'd rather set up locally than use Codespaces. | [Step 1: Clone the kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-1-clone-the-kit) |
| **FlightCheck only** | You're an admin who only wants the predeployment readiness check. No GitHub Copilot subscription needed. | [Run FlightCheck without installing the full kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/flightcheck-standalone) |

After any of the install paths \(other than FlightCheck-only\), continue with [Run your first command](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-3-run-setup) to connect the kit to your Power Platform environment. From there, see [What you can do now](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/what-you-can-do-now) for the next things to try.

## What the kit can do

Once set up, you can ask the kit to:

- Author a new topic from a plain-English description
- Update an existing topic's trigger phrases, messages, or flow
- Check your agent for errors before publishing
- Generate test cases for the Copilot Studio evaluator
- Wire up Workday or ServiceNow end to end
- Run a predeployment readiness check across 40+ verifications

Every change goes through a safe pipeline: save a backup, edit locally, check for errors, preview the change, push, and verify.

## What the kit isn't

The Agent Developer Kit is a **sample and learning toolkit**. It isn't a Microsoft product or a supported service. It complements the Copilot Studio web UI rather than replacing it. Most customers should expect to use both.

For the kit's support model and known limitations, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started) and the repo's [SUPPORT.md](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/blob/main/SUPPORT.md).

## Next step

Pick an install path from the table earlier in this article. For most Windows users, that's [Install with the one-shot installer](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-installer). For everyone else, [GitHub Codespaces](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-codespaces) is the simplest start.
