<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-typespec -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Create declarative agents by using Microsoft 365 Agents Toolkit and TypeSpec

A [declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent) provides a goal-directed conversational experience powered by Microsoft 365 Copilot. You define its purpose, instructions, knowledge, and actions. This guide shows how to build a declarative agent by using [TypeSpec](https://typespec.io/) and [Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/overview-agents-toolkit?context=/microsoft-365/copilot/extensibility/context).

Note

The agent that you build in this tutorial targets licensed Microsoft 365 Copilot users. You can also build agents for Microsoft 365 Copilot Chat users, with limited capabilities. For details, see [Microsoft 365 Copilot developer licenses](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#microsoft-365-copilot-developer-licenses).

Tip

[Work IQ Dev Tools](https://aka.ms/wiqd/docs) \(preview\) and [Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/overview-agents-toolkit?context=/microsoft-365/copilot/extensibility/context) provide related pro-code workflows. To choose based on your capability, package route, and target experience, see [Choose development tools for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools).

Note

Declarative agents based on Microsoft 365 Copilot are now supported in Word and PowerPoint.

## Prerequisites

- A Microsoft 365 tenant where you can upload custom apps. **Provision** fails if custom app upload isn't enabled. To enable custom app upload, see [Microsoft 365 Agents Toolkit requirements](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#microsoft-365-agents-toolkit-requirements). For development environment and licensing options, see [Copilot development environment](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#copilot-development-environment).

To complete the steps described in this article, you need the following resources:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Microsoft 365 Agents Toolkit Visual Studio Code extension](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/install-teams-toolkit?tabs=vscode&context=/microsoft-365/copilot/extensibility/context)

Note

The screenshots and user-interface references in this article use a release version of [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit). Prerelease versions might differ from the user interface shown.

Familiarize yourself with the following standards and guidelines for declarative agents for Microsoft 365 Copilot:

- Standards for compliance, performance, security, and user experience described in [Teams Store validation guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines).

## Create a declarative agent

Start by creating a basic declarative agent.

1. Open Visual Studio Code.
2. Select **Microsoft 365 Agents Toolkit > Create a New Agent/App**.

   ![A screenshot of the Create a New App button in the Microsoft 365 Agents Toolkit sidebar](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/create-new-app.png)
3. Select **Declarative Agent**.

   ![A screenshot of the New Project options with Agent selected](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/select-copilot-agent.png)
4. Select **Start with TypeSpec for Microsoft 365 Copilot** to create a basic declarative agent.
5. Select **Default folder** to store your project root folder in the default location.
6. Enter `My Agent` as the **Application Name** and press **Enter**.
7. In the new Visual Studio Code window that opens, select **Microsoft 365 Agents Toolkit**. In the **Lifecycle** pane, select **Provision**.

   ![A screenshot of the Provision option in the Lifecycle pane of the Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/provision-agent.png)

### Test the agent

1. Go to the Copilot application at [https://m365.cloud.microsoft/chat](https://m365.cloud.microsoft/chat).
2. Next to the **New Chat** button, select the conversation drawer icon.
3. Select the declarative agent **My Agent**.

   ![A screenshot of the declarative agent in Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/select-agent.png)
4. Enter a question for your declarative agent to see it in action.

## Add instructions

Instructions change how an agent behaves.

1. Open the `main.tsp` file and replace the `@instructions` decorator with the following code.

   ```typescript
   @instructions("""
     You are an expert at creating poems.
     Every time a user asks a question, you **must** turn the answer into a poem. The poem **must** not use the quote markdown and use regular text.
   """)
   ```


   The contents of this decorator are inserted in the `instructions` property in the agent's manifest during provisioning. For more information, see [Declarative agent manifest object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#declarative-agent-manifest-object).

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent uses your updated instructions after you reload the page.

![A screenshot of an answer from a declarative agent based on updated instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/updated-instructions.png)

## Add conversation starters

Conversation starters are hints that Copilot displays to users to show how they can get started using the declarative agent.

1. Open the `main.tsp` file and replace the commented `@conversationStarter` decorator with the following content:

   ```typescript
   @conversationStarter(#{
     title: "Getting started",
     text: "How can I get started with Agents Toolkit?"
   })

   @conversationStarter(#{
     title: "Getting Help",
     text: "How can I get help with Agents Toolkit?"
   })
   ```


   For more information, see [Conversation starters object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#conversation-starters-object).

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The updated conversation starters are available in your declarative agent after you refresh the page.

![A screenshot showing the conversation starters from the declarative agent in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/conversation-starters.png)

## Add web content

The [web search capability](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#web-and-scoped-web-search) enables agents to use the search index in Bing to respond to user prompts.

1. Open the `main.tsp` file and add the `WebSearch` capability in the `MyAgent` namespace with the following content.

   ```typescript
   namespace MyAgent {
     op webSearch is AgentCapabilities.WebSearch<Sites = [
       {
         url: "https://learn.microsoft.com",
       },
     ]>;
   }
   ```


   For more information, see [Web search object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#web-search-object).


   Note


   If you don't specify the `Sites` array, the agent can access all web content.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent can access web content to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains web content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/web-content.png)

## Add OneDrive and SharePoint content

The [SharePoint capability](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#sharepoint-and-onedrive) enables the agent to use OneDrive and SharePoint content as knowledge.

1. Open the `main.tsp` file and add the `OneDriveAndSharePoint` capability in the `MyAgent` namespace with the following value, replacing `https://contoso.sharepoint.com/sites/ProductSupport` with a SharePoint site URL in your Microsoft 365 organization.

   ```typescript
   namespace MyAgent {
     // Omitted for brevity
     op od_sp is AgentCapabilities.OneDriveAndSharePoint<ItemsByUrl = [
       {
         url: "https://contoso.sharepoint.com/sites/ProductSupport"
       }
     ]>;
     // Omitted for brevity
   }
   ```


   For more information, see [OneDrive and SharePoint object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#onedrive-and-sharepoint-object).


   Note


   - URLs should be full path to SharePoint items \(site, document library, folder, or file\). You can use the "Copy direct link" option in SharePoint to get the full path or files and folders. Right-click on the file or folder and select **Details**. Navigate to **Path** and select the copy icon.
   - If you don't specify the `ItemsByUrl` array \(or the alternative `ItemsBySharePointIds` array\), the agent can access all OneDrive and SharePoint content in your Microsoft 365 organization that the signed-in user can access.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to OneDrive and SharePoint content to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains SharePoint and OneDrive content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/sharepoint-onedrive-content.png)

## Add Teams messages

The [Teams messages capability](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#teams-messages) enables the agent to use Teams channels, team, and meeting chat as knowledge.

1. Open the `main.tsp` file and add the `TeamsMessages` capability in the `MyAgent` namespace with the following value, replacing `https://teams.microsoft.com/l/team/...` with a Teams channel or team URL from your organization.

   ```typescript
   namespace MyAgent {
     // Omitted for brevity
     op teamsMessages is AgentCapabilities.TeamsMessages<TeamsMessagesByUrl = [
       {
         url: "https://teams.microsoft.com/l/team/...",
       }
     ]>;
     // Omitted for brevity
   }
   ```


   For more information, see [Microsoft Teams messages object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#microsoft-teams-messages-object).


   Note


   - The URL in the `url` property must be a well-formed link to a Teams chat, team, or meeting chat.
   - If you don't specify the `TeamsMessagesByUrl` array, the agent can access all Teams channels, teams, meetings, 1:1 chat, and group chats in your Microsoft 365 organization that the authenticated user can access.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent can access Teams data to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains Teams content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/teams-content.png)

## Add people knowledge

The [people capability](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#people) enables you to scope your agent to answer questions about individuals in an organization.

1. Open the `main.tsp` file and add the `People` capability in the `MyAgent` namespace with the following content.

   ```typescript
   namespace MyAgent {
     // Omitted for brevity
     op people is AgentCapabilities.People;
     // Omitted for brevity
   }
   ```


   For more information, see [People object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#people-object).

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to people knowledge after you reload the page.

![A screenshot showing a response from the declarative agent that contains people knowledge](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/people-content.png)

## Add email knowledge

The [email capability](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#email) enables you to scope your agent to use email from the user's mailbox or a shared mailbox as a knowledge source.

1. Open the `main.tsp` file and add the `Email` capability in the `MyAgent` namespace with the following content.

   ```typescript
   namespace MyAgent {
     // Omitted for brevity
     op email is AgentCapabilities.Email<Folders = [
       {
         folder_id: "Inbox",
       }
     ]>;
     // Omitted for brevity
   }
   ```


   For more information, see [Email object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#email-object).


   Note


   - This example accesses the user of the agent's mailbox. To access a shared mailbox instead, add the optional `shared_mailbox` property set to the email address of the shared mailbox.
   - The `Folders` array limits the mailbox access to specific folders. To access the entire mailbox, omit the `folders` array.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has access to email knowledge after you reload the page.

![A screenshot showing a response from the declarative agent that contains email knowledge](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/email-content.png)

## Add image generator

The [image generator capability](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/image-generator) enables agents to generate images based on user prompts.

1. Open the `main.tsp` file and add the `GraphicArt` capability in the `MyAgent` namespace with the following content.

   ```typescript
   namespace MyAgent {
     // Omitted for brevity
     op graphicArt is AgentCapabilities.GraphicArt;
     // Omitted for brevity
   }
   ```


   For more information, see [Graphic art object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#graphic-art-object).

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent can generate images after you reload the page.

![A screenshot showing a response from the declarative agent that contains generated graphic art](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/graphic-art-content.png)

## Add code interpreter

The [code interpreter capability](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/code-interpreter) is an advanced tool designed to solve complex tasks through Python code.

1. Open the `main.tsp` file and add the `CodeInterpreter` capability in the `MyAgent` namespace with the following content.

   ```typescript
   namespace MyAgent {
     // Omitted for brevity
     op codeInterpreter is AgentCapabilities.CodeInterpreter;
     // Omitted for brevity
   }
   ```


   For more information, see [Code interpreter object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#code-interpreter-object).

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent has the code interpreter capability after you reload the page.

![A screenshot showing a response from the declarative agent that contains a generated graph](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/code-interpreter-graph-content.png)

![A screenshot showing the Python code used to generate the requested graph](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/code-interpreter-python-content.png)

## Add Copilot connectors content

Add items ingested by a Copilot connector to the available knowledge for the agent.

1. Open the `main.tsp` file and add the `GraphConnectors` capability in the `MyAgent` namespace with the following value, replacing `policieslocal` with a valid Copilot connector ID in your Microsoft 365 organization. For more information on finding Copilot connector IDs, see [Retrieve capability IDs for the declarative agent manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-capabilities-ids#copilot-connectors).

   ```typescript
   namespace MyAgent {
     // Omitted for brevity
     op copilotConnectors is AgentCapabilities.GraphConnectors<Connections = [
       {
         connectionId: "policieslocal",
       }
     ]>;
     // Omitted for brevity
   }
   ```


   For more information, see [Copilot connectors object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#copilot-connectors-object).


   Note


   If you don't specify the `Connections` array, the agent gets content from all Copilot connectors in your Microsoft 365 organization that the signed-in user can access.

2. Select **Provision** in the **Lifecycle** pane of Agents Toolkit.

The declarative agent can access Copilot connectors content to generate its answers after you reload the page.

![A screenshot showing a response from the declarative agent that contains Copilot connector content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/graph-connector-content.png)

## Completed

You completed the declarative agent guide for Microsoft 365 Copilot. Now that you're familiar with using TypeSpec to build a declarative agent, you can learn more in the following articles.

- Learn how to [write effective instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions) for your agent.
- Test your agent with developer mode to verify if and how the Copilot orchestrator selects your knowledge sources for use in response to given prompts. For more information, see [Test and debug agents in Microsoft 365 Agents Toolkit by using developer mode](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/debugging-agents-vscode).
- Get answers to [frequently asked questions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/transparency-faq-declarative-agent).
- Learn about other ways to build declarative agents: no-code in [Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder), or low-code in [Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extensions?context=/microsoft-365/copilot/extensibility/context).

## Next steps

[Build an action with TypeSpec](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-api-plugins-typespec)
