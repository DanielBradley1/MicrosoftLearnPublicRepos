<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-19 -->

# Develop Copilot Studio agents with the CLI \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Important

- The CLI is preview software. Obtain the package and review the terms of the preview before installing it.
- These features are subject to [supplemental terms of use](https://www.microsoft.com/business-applications/legal/supp-powerplatform-preview/), and are available before an official release so that customers can get early access and provide feedback.
- Preview features aren't meant for production use and might have restricted functionality.

By using `Microsoft.Agents.Hosting.Cli`, which installs as `msagent`, you can work with Copilot Studio agent definitions as local files. Create a definition or bring an existing cloud agent into your workspace. Edit and review changes by using your development tools, and deploy them to Copilot Studio environments. Use it when you want source control, team code review, repeatable deployment, and evaluations alongside the Copilot Studio authoring experience. Editing happens locally; running agents and evaluations still uses cloud services.

## When to use the CLI

Use this CLI when you need to:

- Review agent instructions, tools, knowledge, and workflows as file differences in Git.
- Collaborate as a team across local and cloud workflows.
- Deploy approved source to named development, test, and production targets.
- Keep portable regression cases and service-side evaluation evidence with your release process.

Continue in the Copilot Studio portal when visual authoring alone meets your needs or your organization doesn't approve local definition authoring. The CLI doesn't replace Copilot Studio licensing or runtime, environment administration, connector authorization, configuration or release governance. It isn't an offline agent runtime.

You can use GitHub Copilot or another AI coding assistant to work with the CLI through natural-language requests. You don't need prior experience with the terminal, an editor, or Copilot Studio to get started this way. If you're already comfortable with the terminal or Copilot Studio, you can build on that experience to work directly with the CLI or combine it with AI assistance. Familiarity with YAML and JSON helps when editing files directly, and source control makes it easier to collaborate and track changes. Whether you work directly or through an AI assistant, you still need the appropriate licensing, environment access, capacity, and organizational approvals. Coding agents also have their own billing requirements. See [Copilot Studio requirements](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-licensing-subscriptions) and [Power Platform environments](https://learn.microsoft.com/en-us/power-platform/admin/environments-overview).

The CLI lets you edit agent definitions locally and deploy them to Copilot Studio. Deploying changes updates the cloud draft; publishing makes those changes available to users.

## Install the CLI

Windows and macOS support the CLI. The following examples use PowerShell and Windows-style project paths. On macOS, use paths that work for your machine.

To use the `dotnet tool install` and `dotnet tool update` commands, install the [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0). The SDK includes both runtimes required to run the CLI: .NET 10 and ASP.NET Core 10.

You can get the CLI as the [Microsoft.Agents.Hosting.Cli NuGet package](https://www.nuget.org/packages/Microsoft.Agents.Hosting.Cli). Install the preview package as a global .NET tool:

```powershell
dotnet tool install --global Microsoft.Agents.Hosting.Cli --prerelease
```

If you already installed the CLI, update it instead:

```powershell
dotnet tool update --global Microsoft.Agents.Hosting.Cli --prerelease
```

Verify the installation:

```powershell
msagent --version
```

## Agent development lifecycle

Follow these steps to create or open an agent, make changes locally, and deploy and test it in Copilot Studio.

| Order | Step | Description |
| --- | --- | --- |
| 1 | [Install the Copilot Studio CLI](#install-the-cli). | Installs the CLI and makes the `msagent` command available. |
| 2 | [Sign in and select an environment](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/authenticate?view=o365-worldwide). | Authenticates the CLI with your work or school account and selects a Power Platform environment. |
| 3 | [Create an agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide) or [open an existing agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/open-existing-agent?view=o365-worldwide). | Creates local definition files for a new agent or brings an existing definition onto your machine. |
| 4 | [Edit your agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/edit-agent?view=o365-worldwide). | Updates instructions and behavior by using your preferred tools or an AI coding assistant. Optionally, [save changes in source control](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/source-control?view=o365-worldwide). |
| 5 | [Prepare connections \(optional\)](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide#when-to-bind-connections). | Creates or reuses environment-specific connections. You can bind standalone workflow references before deployment. Agent reference binding requires an existing target cloud agent. |
| 6 | [Deploy a draft](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide#deploy-your-agent). | Uploads your local definition to Copilot Studio. Check connection bindings and workflow readiness, and then [evaluate the draft](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/evaluate?view=o365-worldwide). |
| 7 | [Publish your agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide#publish-your-agent). | Makes the reviewed changes available to intended users. |
| 8 | [Test your agent from the terminal](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide) or [in Playground](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/playground?view=o365-worldwide). | Connects to the published agent from your machine to ask questions and check its responses. |

For a cloud workflow with its own lifecycle, see [Manage a standalone workflow with the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/standalone-workflows?view=o365-worldwide).

## Test and evaluate your Copilot Studio agent

Use [evaluations](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/evaluate?view=o365-worldwide) to assess agent quality, including against a cloud draft. For interactive testing, use [terminal live queries](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide) or the [playground](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/playground?view=o365-worldwide). Both interactive testing options require a published agent that you have permission to access.

After installation, inspect the available surface with root help:

```powershell
msagent --help
```

Success at this stage means you can identify your starting state, intended development environment, and approvals needed for cloud operations. Next, [sign in and choose an environment](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/authenticate?view=o365-worldwide).

If installation, sign-in, deployment, or testing doesn't work as expected, see [Diagnose CLI problems and resume safely](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/troubleshoot?view=o365-worldwide).

Note

Cloud conversations, generation, evaluations, and connector actions can consume Copilot Credits, incur other service charges, and change real data. Running them from a local terminal doesn't make them a dry run. Use safe data, restricted action targets, and an approved budget.

## Get support

The Copilot Studio CLI project uses [GitHub issues](https://github.com/microsoft/AgentHosting.Cli/issues) to track bugs and feature requests. Search existing issues before filing a new one to avoid duplicates. To report a new bug or request a feature, [open an issue in the CLI repository](https://github.com/microsoft/AgentHosting.Cli/issues/new/choose).
