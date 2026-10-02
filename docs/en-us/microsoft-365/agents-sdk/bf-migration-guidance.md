<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-guidance -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Azure Bot Framework SDK to Agents SDK migration guidance

The Microsoft 365 Agents SDK enables developers to create and customize agents using the AI stack of their choice. Developers can create a custom engine agent \(CEA\) and deploy it to Microsoft Copilot. To get started quickly with scaffolding and templates, use the Microsoft 365 Agents Toolkit for Visual Studio and Visual Studio Code. Developers can add their chosen models and orchestrator from Azure Foundry and Semantic Kernel, OpenAI Agents, LangChain, or even a custom built orchestrator. Developers can even choose to bring multiple agents built with different technologies, and surface the agents through Microsoft Copilot.

By using the Microsoft 365 Agents SDK, you can build an agent quickly and surface it on any channel, including Microsoft Copilot and Microsoft Teams.

The Agents SDK is designed to be unopinionated about the AI you use. You can implement agentic patterns without being locked into a tech stack.

The Agents SDK takes advantage of specific client channel behavior, such as Microsoft Copilot, Teams, and other non-Microsoft channels. It allows you to tailor your agent to client channels, including specific events or actions.

## Unsupported and deprecated packages

The Microsoft 365 Agents SDK is the evolution of the Azure Bot Framework SDK. The Azure Bot Framework was previously the way for a developer to build bots with a primary focus on conversational AI around topics, dialogs, and messages. The industry norm is now to use generative AI functionality, grounded on knowledge located across the enterprise. Companies need to be able to orchestrate actions, and answer questions, from within a conversational experience. The Microsoft 365 Agents SDK provides capabilities for modern agent development, bringing together the creation of conversational agents with conversation management and orchestration. Agents built with the SDK can connect to numerous AI services and clients, including agents created with non-Microsoft software or technology.

This article provides guidance and awareness if you're considering, or in the process of, migrating from the Azure Bot Framework to the Agents SDK. With this information, you can stay informed and make more informed decisions.

The functionalities in the following table aren't supported in Agents SDK. Bots requiring these functionalities can't migrate without implementing alternatives:

| Functionality | Reason |
| --- | --- |
| Adaptive Dialogs | The Adaptive Dialog System \(implemented in C# in the Bot Framework\) is no longer directly relevant. Microsoft doesn't plan to move this system into the Agents SDK. |
| AdaptiveExpressions | This functionality includes `Microsoft.Bot.AdaptiveExpressions.Core`. However, these packages are still available for use from the .NET BotBuilder packages. These packages don't take dependencies on SDK packages, and you can use them if you wish with Agents SDK. The AdaptiveExpressions functionality, however, isn't actively supported. |
| Application Insights | Legacy telemetry and monitoring approaches are replaced with modern observability solutions that better integrate with cloud-native agent architectures. |
| ASP.NET WebAPI | ASP.NET WebAPI and similar older technologies are no longer needed. This change impacts only C#, where only the current generation of ASP.NET Core \(ironically called "ASP.NET Core Web API"\) is supported. |
| Bot Framework Composer Artifacts | Artifacts from Composer \(adaptive dialogs, adaptive expressions, and so on, implemented in C# in the Bot Framework\) are no longer required and aren't being brought forward. |
| BotFrameworkAdapter | Replaced by `CloudAdapter` in Bot Framework, and removed from the Agents SDK. |
| CLI | All commands in the [Bot Framework CLI](https://github.com/microsoft/botframework-cli) \("bf"\) are deprecated and replaced with modern tooling in the Agents SDK. |
| Deprecated Activities | Older activities are deprecated, such as payments activities, as they don't align with modern agent interaction patterns. |
| Generators | The legacy generators for each of the languages \(Yeoman, and so on\), aren't being brought forward because the Microsoft 365 Agents Toolkit replaces them. |
| Inspection | Legacy debugging and inspection tools are replaced with modern development and debugging experiences provided by the Agents SDK tooling. |
| Language Generation | LG tooling, template tooling, and related parsers aren't needed. General purpose language models replace these tools. |
| Language Understanding | This functionality includes `Microsoft.Bot.Builder.Parsers.LU`. Modern LLM-based natural language processing capabilities supersede these legacy language understanding tools. |
| Previous Generation AI Tooling | Tools such as LUIS, Orchestrator, and QnA Maker are no longer needed. The online services for these tools are already disabled. Existing bots that depend on these services need to migrate to different tooling. |
| QueueStorage | Message queuing functionality was replaced with more efficient and scalable cloud-native messaging patterns optimized for agent workloads. |
| Streaming Connections | Real-time streaming capabilities were redesigned to work with modern conversational AI patterns and aren't compatible with the legacy streaming implementation. |
| TemplateManager | Legacy template management systems are no longer needed as modern LLMs can generate dynamic responses without predefined templates. |

## Language specific guides

- [.NET migration guide](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-dotnet)
- [NodeJS migration guide](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-nodejs)
- [Python migration guide](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-python)
