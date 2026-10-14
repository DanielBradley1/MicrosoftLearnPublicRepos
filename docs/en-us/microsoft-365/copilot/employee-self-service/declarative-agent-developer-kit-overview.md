<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Agent Developer Kit for declarative agents: overview

The Employee Self-Service Agent Developer Kit lets you customize your Employee Self-Service agent through GitHub Copilot Chat in Visual Studio Code. You describe what you need in plain English, and the kit translates that into topics, workflows, and configuration.

You don't need to be a developer, and you don't need to know how Power Platform or Copilot Studio work under the hood.

## What you need

- A computer where you can install Visual Studio Code, or a browser if you use GitHub Codespaces
- A GitHub Copilot subscription. The installer sets up the extensions, but it can't grant the subscription.
- Access to a Power Platform environment

You don't need an Employee Self-Service agent already in place. Setup can connect to an agent you have, or create one for you. First, [confirm which agent you have](#confirm-which-agent-you-have).

## Confirm which agent you have

The kit has separate code lines for different Employee Self-Service agent families:

- **Native declarative agents** use the `main` branch.
- **Custom Engine Agents and classic declarative-agent preview** use the compatible `main-ca` branch.

The default download uses `main`. Check which agent family you have before you install or update the kit. If you are not sure, confirm with the administrator who installed the agent. Setup verifies the selected agent instead of relying on its display name.

Installing the wrong code line does not change your deployed agent, but the local kit might not match it. See the [kit repository](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit) for the matching branch.

## Pick your install path

| Option | Best for | Guide |
| --- | --- | --- |
| **One-shot installer** | For native declarative agents on Windows or macOS, one command installs the toolchain, clones the kit, and opens Visual Studio Code. | [Install with the one-shot installer](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-get-started-installer) |
| **GitHub Codespaces** | Browser-only, with no local install. Choose the branch for your agent family. | [Install with GitHub Codespaces](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-get-started-codespaces) |
| **Manual install** | You want to choose the branch and control what gets installed where. | [Step 1: Clone the kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-get-started-1-clone-kit) |
| **FlightCheck only** | You're an admin who wants only the predeployment readiness check. No GitHub Copilot subscription needed. | [Run FlightCheck without installing the full kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/flightcheck-standalone) |

### Maker mode or Developer mode

The one-shot installer asks which experience you want before Visual Studio Code opens:

- **Maker** is chat-first. Developer surfaces are hidden, and a Quick Actions rail gives you big buttons for common tasks along with a short built-in tutorial.
- **Developer** is the standard Visual Studio Code layout with Copilot Chat in the side panel.

You can switch between the two at any time from the Quick Actions panel, so the choice isn't permanent.

## Set up your workspace

After you install the kit and open the `ess-maker-skills` folder, run `/setup` in Copilot Chat. Setup verifies the agent and environment, then prepares the local workspace for the selected agent family. Setup does not publish local changes to employees.

To install and deploy an Employee Self-Service declarative-agent template, follow [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent). For the Custom Engine Agent setup walkthrough, see [Run your first command](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-get-started-3-run-setup).

## What the kit can do

The available operations depend on the agent family. The kit can help you:

- Configure supported landing-page sections.
- Create or update supported topics, workflows, and evaluation test sets.
- Scan local agent files and run applicable readiness checks.
- Configure supported integrations by following their setup guidance.

For native declarative agents, general topic and workflow changes remain local; the general `/push` command does not deploy them. Evaluation test sets use a separate supported deployment flow.

## Diagnostics

- `/scan` checks local agent files for issues such as broken references and missing bindings.
- `/flightcheck` runs checks for the selected agent family and scope, then reports results and applicable remediation.
- Setup reports workspace and readiness results separately. A ready local workspace does not mean the agent has been published or made available to employees.

Changes to native declarative-agent topics and workflows stay local. Do not treat a successful scan, readiness check, or evaluation review as a deployment.

## What the kit isn't

The Agent Developer Kit is a **sample and learning toolkit**. It isn't a Microsoft product or a supported service. It complements the Copilot Studio web UI rather than replacing it, and most customers should expect to use both.

Support for the kit comes from its repository documentation and GitHub issues, which is separate from the support route for the Employee Self-Service product itself. For the support model and known limitations, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started) and the repo's [SUPPORT.md](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/blob/main/SUPPORT.md).

## Next step

Pick an install path from the table earlier in this article. The one-shot installer installs the native declarative-agent branch. For Custom Engine Agents or classic declarative-agent preview, select `main-ca` in Codespaces or use the manual install instructions. If you can't install software locally, use [GitHub Codespaces](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-get-started-codespaces).
