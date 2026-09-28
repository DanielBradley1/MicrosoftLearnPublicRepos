<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# What is the Microsoft 365 Agents SDK

The Microsoft 365 Agents SDK is a development framework for building conversational agents. Conversational agents are software that can receive messages from users, process them, and respond. Think of it as the plumbing layer between a user sending a message \(whether in Teams, a website, Slack, or elsewhere\) and whatever logic you built to respond to that message.

The SDK handles the mechanics of receiving and sending messages across different surfaces, so developers can focus on what the agent actually does rather than on low-level communication protocols.

## Supported languages

The Agents SDK supports:

- C# using the .NET 8.0 SDK
- JavaScript using Node.js version 18 and later
- Python using version 3.9 to 3.11

## Three problems the Agents SDK solves

- **Your agent needs to work in more than one place.** Users don't all communicate through the same channel. Some use Microsoft Teams, some use Microsoft 365 Copilot, some use a company website, and some use non-Microsoft tools like Slack or Facebook Messenger. Without a framework, a developer needs to write separate integration code for each of those surfaces, each with its own message format, authentication scheme, and connection protocol.

  The SDK provides a channel abstraction layer. You write your agent logic once, and the SDK translates incoming and outgoing messages to and from the format each channel expects. Adding a new channel doesn't require rewriting the agent's core behavior.
- **You don't want to be locked into one AI service.** The choice of which AI service powers an agent, whether that's Azure AI Foundry, OpenAI, Semantic Kernel, or something else entirely, changes frequently as the landscape evolves and as different use cases emerge. An agent framework that bakes in a specific AI provider forces developers to rewrite large portions of their code when that choice changes.

  The SDK is AI-agnostic by design. It provides the scaffolding for receiving messages, managing state, and routing events, but makes no assumptions about what generates the response. Developers plug in whatever AI services or orchestration libraries they prefer. The SDK doesn't get in the way of that choice.
- **Handling conversation state is hard.** Conversations aren't stateless. A user might ask a follow-up question, refer to something said two turns ago, or abandon a conversation and resume it later. Managing that context, including tracking what happened, where it's stored, and how it flows between messages, is tedious and error-prone to build from scratch.

  The SDK provides built-in state and storage management. It introduces the concept of a turn \(a single unit of work in a conversation\) and tracks state across turns without requiring developers to wire up their own persistence layer. This means less boilerplate code and fewer bugs in conversation flow logic.

## How it fits together

At its core, the SDK does three things when a message arrives:

1. Receives the message from whatever channel sent it \(Teams, web chat, Slack, and so on\) and normalizes it into a common format called an `Activity`.
2. Routes the activity to the appropriate handler in your agent code. For example, a message activity triggers one handler, a user joining a conversation triggers another.
3. Sends the response back through the same channel, translating your response back into the format that channel expects.

Developers write handlers for the activity types they care about. The SDK handles everything else, including authentication, message format translation, and channel connectivity.

## What the Agents SDK is not

The Agents SDK isn't an AI model, an orchestration engine, or a no-code builder. The Agents SDK doesn't decide what an agent says. These elements are the job of whatever AI service or business logic the developer wires into the agent. The Agents SDK is the framework that gets messages to and from that logic reliably, across channels, with conversation state intact.

## Next steps

- Learn about [Activity Protocol](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/activity-protocol)
- Learn about [AgentApplication](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-application)
- [Quickstart: Create and test a basic agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/quickstart)
