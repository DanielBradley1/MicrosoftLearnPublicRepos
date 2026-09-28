<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Tutorial: Create declarative agents by using Microsoft 365 Agents Toolkit

A declarative agent is a customized version of Microsoft 365 Copilot that you can use to create personalized experiences by declaring specific instructions, actions, and knowledge. This guide provides information about how to build a declarative agent by using [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit).

The agent that you build in this tutorial targets licensed Microsoft 365 Copilot users. You can also build agents for Microsoft 365 Copilot Chat users, with limited capabilities. For details, see [Microsoft 365 Copilot developer licenses](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#microsoft-365-copilot-developer-licenses).

Note

[Microsoft 365 Government tenants](https://www.microsoft.com/microsoft-365/government) don't support publishing agents through the Microsoft 365 Agents Toolkit.

![Screenshot shows the answer from the declarative agent in Microsoft 365 Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/agent-answer.png)

For overview information, see [Declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent). To compare agent types, see [Agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agents-overview).

Note

Declarative agents based on Microsoft 365 Copilot are now supported in Word and PowerPoint.

## Prerequisites

Before you start, make sure that Microsoft 365 Copilot is available for your organization.

The following options are available for your development environment:

- A sandbox Microsoft 365 organization with Copilot \(available in limited preview through [TAP membership](https://developer.microsoft.com/microsoft-365/tap)\).
- An [eligible Microsoft 365 or Office 365 production environment](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#organizations-with-microsoft-365-copilot-licenses) with a Microsoft 365 Copilot license.

The following resources are required to complete the steps described in this article:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Microsoft 365 Agents Toolkit Visual Studio Code extension](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/install-teams-toolkit?tabs=vscode#install-a-prerelease-version)

Note

The screenshots and references to user interface of the [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) in this document were generated using the latest **Release** version, 6.0. Pre-Release versions of Agents Toolkit may differ from the user interface in this document.

You should be familiar with the following standards and guidelines for declarative agents for Microsoft 365 Copilot:

- Standards for compliance, performance, security, and user experience described in [Microsoft Teams Store validation guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#teams-apps-extensible-as-plugin-for-microsoft-copilot-for-microsoft-365).

## Create and provision a declarative agent with Microsoft 365 Agents Toolkit

Start by creating a basic declarative agent.

Tip

**Work IQ Dev Tools \(preview\)** — As an alternative to the Visual Studio Code steps in this tutorial, [get started with Work IQ Dev Tools](https://aka.ms/wiqd/docs) for a simpler, faster command-line workflow. The Microsoft 365 Agents Toolkit steps that follow might be a better fit for your workflow.

1. Open Visual Studio Code.
2. Select **Microsoft 365 Agents Toolkit > Create a New Agent/App**.

   ![A screenshot of the Create a New Agent/App button in the Agents Toolkit sidebar](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/create-new-app.png)
3. Select **Declarative Agent**.

   ![A screenshot of the New Project options with Agent selected](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/select-copilot-agent.png)
4. Select **No Action** to create a basic declarative agent.
5. Select **Default folder** to store your project root folder in the default location.
6. Enter `My Agent` as the **Application Name** and press **Enter**.
7. In the new Visual Studio Code window that opens, select **Microsoft 365 Agents Toolkit**, then select **Provision** in the **Lifecycle** pane.

   ![A screenshot of the Provision option in the Lifecycle pane of Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/provision-agent.png)

## Test the agent

1. Go to the Copilot application at [https://m365.cloud.microsoft/chat](https://m365.cloud.microsoft/chat).
2. Next to the **New Chat** button, select the conversation drawer icon.
3. Select the declarative agent **My Agent**.

   ![A screenshot of the declarative agent in Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/select-agent.png)
4. Enter a question for your declarative agent and make sure it replies with "Thanks for using Microsoft 365 Agents Toolkit to create your declarative agent!"

   ![A screenshot of an answer from the declarative agent in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/agent-answer.png)

## Next step

[Customize behavior with instructions and conversation starters](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-customize-behavior)
