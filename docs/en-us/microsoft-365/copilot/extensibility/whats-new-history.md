<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/whats-new-history -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# What's new history for Microsoft 365 Copilot extensibility

Find historical information about additions and updates to Microsoft 365 Copilot extensibility options.

For the current what's new information, see [What's new in Microsoft 365 Copilot extensibility](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/whats-new).

## December 2025

### Teams meeting AI insights APIs now generally available

The Teams meeting AI insights APIs are now generally available in Microsoft Graph v1.0. These APIs enable you to retrieve AI-generated insights from Teams meetings, including action items, meeting notes, and mentions. For more information, see [List aiInsights](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/onlinemeeting-list-aiinsights) and [Get callAiInsight](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/callaiinsight-get).

## November 2025

### People knowledge source in Copilot Studio lite experience

The People knowledge source is now available in the Copilot Studio lite experience, allowing agents to answer questions about individuals in your organization. For more information, see [People data](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#people-data) and [Add knowledge sources to your declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#people).

### Agent Builder in Microsoft 365 Copilot is available in GCCM

The Agent Builder feature in Microsoft 365 Copilot is now available in Microsoft 365 Government Community Cloud Moderate \(GCCM\) environments.

### Embedded file content file size limit increased to 512 MB

You can now upload files up to 512 MB in size when you embed file content as knowledge in Agent Builder in Microsoft 365 Copilot. For more information, see [File types and size limits](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#file-types-and-size-limits).

## October 2025

### New admin controls for agent sharing

Tenant administrators can now govern who is allowed to share agents created in Microsoft 365 Copilot. These controls help organizations maintain compliance and prevent oversharing of agents. For more information, see [Share an agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-share-manage-agents#share-an-agent).

### Copy an agent to Copilot Studio

You can copy your declarative agent from Microsoft 365 Copilot to Copilot Studio by using the **Copy to full experience** feature. This unlocks advanced lifecycle management, analytics, governance controls, and deeper enterprise integration options.

For details, see [Copy an agent from Agent Builder to Copilot Studio](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copy-agent-to-copilot-studio).

### Use the Search API \(preview\) to perform semantic search

The Microsoft 365 Copilot Search API \(preview\) enables developers to perform semantic search across OneDrive content by using natural language queries with contextual understanding and intelligent results. For more information, see [Overview of the Search API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/overview).

### Users with usage billing have access to additional knowledge sources in Microsoft 365 Copilot

Users who are configured with usage billing in the Microsoft 365 admin center now have access to embedded file content, SharePoint data, and Microsoft 365 Copilot connectors custom knowledge sources when they use Microsoft 365 Copilot to create agents.

### Microsoft 365 Copilot Chat API \(preview\)

The Microsoft 365 Copilot Chat API \(preview\) enables you to programmatically engage in multi-turn conversations with Microsoft 365 Copilot, grounded in enterprise search and web search. For more information, see [Overview of the Microsoft 365 Copilot Chat API \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/overview).

## August 2025

### Use Teams meetings as a knowledge source in Microsoft 365 Copilot

Teams meetings are now available as a knowledge source when you use Microsoft 365 Copilot to create agents. For more information, see [Add knowledge sources to your declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources).

## July 2025

### Scope Copilot connector data sources

You can now scope Copilot connectors to specific data attributes when you use Microsoft 365 Copilot to create your agent. For more information, see [Scope Copilot connector data sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#scope-copilot-connector-data-sources).

### Declarative agent manifest version 1.5

A new version of the declarative agent manifest schema is available. [Declarative agent manifest schema version 1.5](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.5) adds the following:

- Added the [meetings](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.5#meetings-object) capability to the list of `capabilities`, which allows agents to search meetings in the organization.

### Disclaimers in declarative agents

Added the `disclaimers` property to the [Declarative agent manifest object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.4#declarative-agent-manifest-object) in schema version 1.4.

### Embedded file content file size limit increased to 100 MB

You can now upload files up to 100 MB when you embed file content as knowledge in Microsoft 365 Copilot. For more information, see [File types and size limits](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#file-types-and-size-limits).

### Increased SharePoint file limit for agents

You can now specify up to 100 SharePoint files as knowledge when you use Microsoft 365 Copilot, up from a limit of 20 files. For more information, see [SharePoint content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#sharepoint-and-onedrive-content).

### Build Microsoft 365 Copilot connectors for people data \(preview\)

Build connectors to ingest people data from your source systems into Microsoft Graph for Microsoft 365 Copilot. For more information, see [Build Microsoft 365 Copilot connectors for people data \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-connectors-with-people-data).

### Agents supported in Microsoft 365 Government clouds

Limited support for declarative agents is available for [Microsoft 365 Government](https://www.microsoft.com/microsoft-365/government) tenants. Support is now available for Government Community Cloud \(GCC\) tenants.

### Asynchronous and proactive messages in custom engine agents

You can implement asynchronous and proactive message flows in your custom engine agents. For more information, see [Implement asynchronous and proactive messaging in custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/custom-engine-agent-asynchronous-flow).

### Convert declarative agents to custom engine agents

You can convert your declarative agent to a custom engine agent to take advantage of advanced functionality and workflows. For more information, see [Convert your declarative agent to a custom engine agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/convert-declarative-agent).

### Prioritize declarative agent knowledge sources

You can configure your agent to prioritize the knowledge sources that you provide rather than general knowledge in its responses. For more information, for Microsoft 365 Copilot, see [Prioritize your knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#prioritize-your-knowledge-sources-over-general-knowledge); for Microsoft 365 Agents Toolkit, see [Special instructions object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.4#special-instructions-object).

### Custom engine agents generally available

Custom engine agents for Microsoft 365 Copilot are now generally available \(GA\). For more information, see [Custom engine agent overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-custom-engine-agent).

## June 2025

### Maximum number of conversation starters for declarative agents

You can now add up to 12 conversation starters to your declarative agent when you use the [Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents) to create your agent.

### Embedded file content as knowledge

Use the file upload feature in Microsoft 365 Copilot to upload files from your device or the cloud to use as knowledge for your agent. For more information, see [Embedded file content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#embedded-file-content).

### Use the Retrieval API \(preview\) to retrieve data

The Microsoft 365 Copilot Retrieval API \(preview\) allows you to retrieve relevant content from SharePoint and Copilot connectors. For more information, see [Overview of the Retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/overview).

### Microsoft 365 Copilot API client libraries

Use the Copilot API libraries to work with Microsoft 365 Copilot APIs. For more information, see [Microsoft 365 Copilot APIs \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/sdks/api-libraries).

### Outlook email and Teams chats knowledge in Microsoft 365 Copilot

Add Outlook email and Teams group, channel, and meeting chats as knowledge when you use Microsoft 365 Copilot to build your agent. For more information, see [Add knowledge sources in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge).

## May 2025

### Microsoft 365 Agents Toolkit

Use the [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) to [build declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents) and [build Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-your-first-connector).

### Microsoft 365 Copilot APIs

The Microsoft 365 Copilot APIs provide a comprehensive set of capabilities that enable you to build AI-powered applications grounded in enterprise data. For more information, see [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview).

### API plugin manifest version 2.3

A new version of the API plugin manifest schema is available. [Plugin manifest schema 2.4 for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-manifest-2.4) adds support for [Model Context Protocol \(MCP\) servers](https://modelcontextprotocol.io/), enhanced response semantics with file references, and improved confirmation handling.

### Declarative agent manifest version 1.4

A new version of the declarative agent manifest schema is available. [Declarative agent manifest schema version 1.4](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.4) adds the following features.

- Added the `behavior_overrides` property to the [Declarative agent manifest object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.4#declarative-agent-manifest-object).
- Added the `part_type` and `part_id` properties to the [Items by SharePoint IDs object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.4#items-by-sharepoint-ids-object).
- Added the [Scenario models](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.4#scenario-models-object) capability.

## April 2025

### Email as knowledge

Email is now available as a knowledge source for agents built with the [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit). For more information, see [Email knowledge](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#email).

### Copilot Studio agent templates

Use templates in [Copilot Studio](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder) to streamline your agent development process. For more information, see [Agent templates overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-templates-overview).

### Document interaction for declarative agents in Word

Declarative agents in the Copilot experience in Word can [interact with the open document](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-document-interaction). Users can provide the current selection to the agent and can insert images provided by the agent into the document.

## March 2025

### Declarative agent manifest version 1.3

A new version of the declarative agent manifest schema is available. [Declarative agent manifest schema version 1.3](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.3) adds support for the following capabilities:

- Dataverse knowledge
- [Teams messages as knowledge](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#teams-messages)
- [People knowledge](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#people)

## February 2025

### Copilot Studio available in Copilot Chat

Microsoft 365 Copilot Chat users can now access Copilot Studio to build agents in the Microsoft 365 Copilot app and the Copilot app in Teams.

### Add websites as knowledge in Copilot Studio

You can add specific public websites as agent knowledge sources to make your agent context-aware. For details, see [Web content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#public-websites).

### Custom engine agents available in Copilot app \(preview\)

Users with Microsoft 365 Copilot licenses or users in tenants with metering enabled can now access custom engine agents in the Microsoft 365 Copilot app \(preview\), in addition to Teams.

## January 2025

### Links are no longer redacted in Copilot responses

Copilot responses no longer redact links to organizational and web resources. Links that don't explicitly match grounding data or resources defined in the agent manifest continue to be redacted.

### Build agents for Microsoft 365 Copilot Chat

You can now build agents for Microsoft 365 users who don't have a Microsoft 365 Copilot license, grounded on the web and with limited capabilities. For more information, see [Microsoft 365 Copilot developer licenses](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#microsoft-365-copilot-developer-licenses).

## December 2024

### Add code interpreter to your declarative agent

Add the code interpreter capability to your declarative agent by using the Copilot Studio agent builder or Agents Toolkit. To learn more, see [Add capabilities to your declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/code-interpreter).

## November 2024

### Add image generator to your declarative agent

Add the image generator capability to your declarative agent by using the Copilot Studio agent builder or Agents Toolkit.. To learn more, see [Add capabilities to your declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/image-generator).

### Declarative agent manifest version 1.2

A new version of the declarative agent manifest schema has been released. Version 1.2 adds support for scoped web search and the new code interpreter and image generator capabilities. To learn more, see [Declarative agent schema 1.2 for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.2).

### API plugin manifest version 2.2

A new version of the API plugin manifest schema has been released. Version 2.2 adds support for data handling attestation. To learn more, see [Plugin manifest schema 2.2 for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-manifest-2.2).

## October 2024

### Use the Copilot Studio agent builder to build declarative agents

Use the Copilot Studio agent builder to create and customize agents for your specific scenarios. With the agent builder, you can use natural language to describe your agent, or you can build it manually via a rich authoring experience. To learn more, see [Overview of Copilot Studio agent builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder).

## September 2024

### Build your own agent

You can build your own agents to focus on your specific use cases. Provide custom instructions to tailor responses, ground agents in your organization's data, and add more skills with actions.

You can build agents in two ways:

- [Build declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent) by using the Microsoft 365 Copilot orchestrator and foundation models. You can use Visual Studio Code or the Copilot Studio agent builder.
- [Build custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-custom-engine-agent) with your custom orchestrator and foundation models by using Azure AI Foundry and Visual Studio Code.
