<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/create-new-toolkit-project-vsc -->
<!-- Sitemap-Last-Modified: 2026-07-24 -->

# Create JavaScript agents in Visual Studio Code with the Microsoft 365 Agents Toolkit

In this article, you learn how to create a new Agents SDK JavaScript project in Visual Studio, using the Microsoft 365 Agents Toolkit.

## Prerequisites

- [Install the Agents Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) extension for Visual Studio Code.
- You need an Azure OpenAI model from the Microsoft Foundry portal. You need the following data about the model:

  - **Name**
  - **Target URI**
  - **Key**


  [Learn how to add and configure models to Azure AI Foundry Models](https://learn.microsoft.com/en-us/azure/ai-foundry/model-inference/how-to/create-model-deployments)

## Create a new project

The Agents Toolkit provides a project template to help you get started with building an agent. You can start from a template in the toolkit or from samples in the Agents SDK.

Note

The procedure that follows currently works for JavaScript and TypeScript only. Support is planned for Python.

1. In Visual Studio Code, open the Microsoft 365 Agents Toolkit extension side panel by selecting the Microsoft 365 Agents icon on the sidebar.
2. To build a new agent project, select **Create a New Agent/App**. You can start from a template in the toolkit or from samples in the Agents SDK. This guide covers starting with the Agents Toolkit.

![Starting page of Agents Toolkit extension](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-start-page.png)

1. To start with building an agent with the Agents SDK, select **Custom Engine Agent**:

![Select agent type to create](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-custom-engine-agent.png)

## Create a new agent

With custom engine agent selected as an option, you're guided down a series of prompts to add in your own AI services.

You have two templates to select from:

- **Basic Custom Engine Agent**
- **Weather Agent**.

The basic custom engine agent is an agent without anything prebuilt. You need to add an AI orchestrator, like Semantic Kernel or LangChain, and your knowledge, for the agent to be useful.

![Select template](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-select-template.png)

1. In this example, select **Weather Agent** to create an agent that uses LangChain, and Azure AI Foundry, depending on your chosen language.

You are prompted to select an LLM service.

1. Select **Azure OpenAI** for your model.

   ![Select Azure OpenAI for LLM](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-select-azureopenai.png)

   You're prompted for your **Key**, **Target URI**, and the **Name** of your Azure OpenAI model from the Microsoft Foundry portal. You can find these pieces of information under **My assets** and **Models and endpoints** in the Foundry portal.
2. Enter the model details, starting with the Azure OpenAI service key.

   ![Enter Azure OpenAI key to authenticate](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-enter-azureopnai-key.png)
3. Select **JavaScript** or **TypeScript**, select the **Default folder**, and enter an **Application Name** to store your project root folder in the default location.

   Your new project opens.

   ![View of files for newly created project](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-view-new-project.png)
4. Confirm you're signed in using the extension by selecting the Microsoft 365 logo on the toolbar in Visual Studio Code. Ensure you're signed in to the tenant you want to connect to.

   ![View accounts and sign in](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-account-signin.png)

## Debug and test your agent in Agents Playground

You can debug and test your code with the new Microsoft 365 Agent Playground available in the toolkit. The playground helps you debug your code easily and without having to go through a full deployment cycle.

1. Select **Debug in Microsoft 365 Agents Playground**.

   When you select the playground, wait a short time while it prepares your local machine with the required components. The preparation takes a few minutes.

   ![Select debug in Microsoft 365 Agents Playground](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-debug-m365-agents-playground.png)
2. While you wait for the deployment, check your folder for the code and review it to familiarize yourself.

   ![Looking at the generated template code](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-review-code.png)
3. Once the playground for debug and testing finishes loading, a browser opens and you're ready to interact with your agent using the playground. If you follow the guide and use the prebuilt template with LangChain and Azure AI Foundry, you can ask "What is the weather in {your location} tomorrow?" The agent responds with an adaptive card with the weather, using your chosen AI Service.

   ![Debug app in Teams App Test Tool](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-teams-app-test-tool.png)

   ![Teams App Test Tool with adaptive card in chat](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-teams-app-test-tool-adaptive-card.png)

## Debug and test your agent in Microsoft Copilot

When you finish testing locally in the Agents Playground, you can deploy to Azure Bot Service and configure for the Microsoft Copilot channel. Ensure you're logged into a tenant that has access to Microsoft Copilot.

1. Change the debug target to Copilot, so that you can debug using Microsoft Copilot. Select **F5** on the keyboard or **Debug** to test. It takes a few minutes of preparation to make the agent available to Microsoft 365. Behind the scenes, the toolkit creates an app registration and Azure Bot Service record in Azure Bot Service, and deploys your project to your tenant along with a manifest.

   ![Select to debug in Copilot \(Edge\)](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-select-debug-m365-copilot-edge.png)
2. Once your project is deployed, you should see Microsoft Copilot load and be able to ask questions, add breakpoints, and debug, as required, directly in Microsoft Copilot:

   ![Test and debug in Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/toolkit-project-vsc/vsc-toolkit-test-debug-m365-copilot.png)

## Summary

You have now successfully:

- Started a new Microsoft 365 Agents project and agent using the Agents Toolkit
- Tested the agent locally using the Microsoft 365 Agents Playground
- Deployed the agent for debugging directly in the Microsoft 365 Channel
