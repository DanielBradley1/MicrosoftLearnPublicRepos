<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-customize-behavior -->
<!-- Sitemap-Last-Modified: 2026-05-11 -->

# Add instructions and conversation starters to a declarative agent created with Microsoft 365 Agents Toolkit

You can customize the behavior of your declarative agent in the agent's manifest.

- [Instructions](#add-instructions-to-the-agent) ensure that the agent understands its role and tasks and how to interact with users.
- [Conversation starters](#add-conversation-starters-to-the-agent) are hints that are displayed to the user to demonstrate how they can get started using the declarative agent.

Important

This guide assumes you have completed the [Create declarative agents using Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents) tutorial.

## Add instructions to the agent

Start by adding instructions to the agent to phrase its responses as poems.

1. Open the `appPackage/instructions.txt` file and replace its contents with the following text.

   ```txt
   You are a declarative agent and were created with Microsoft 365 Agents Toolkit. You are an expert at creating poems.

   Every time a user asks a question, you **must** turn the answer into a poem. The poem **must** not use the quote markdown and use regular text.
   ```

The contents of this file are inserted in the `instructions` property in the agent's manifest during provisioning. For more information, see [Declarative agent manifest object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#declarative-agent-manifest-object).

1. Select **Provision** in the **Lifecycle** pane of the Agents Toolkit.

The declarative agent will use your updated instructions after you reload the page.

![A screenshot of an answer from a declarative agent based on updated instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/updated-instructions.png)

For more information about writing instructions, see [Write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Add conversation starters to the agent

Next, add some conversation starters to the agent.

1. Open the `appPackage/declarativeAgent.json` file and add the `conversation_starters` array with the following content:

   ```json
   "conversation_starters": [
     {
       "title": "Getting Started",
       "text": "How can I get started with Agents Toolkit?"
     },
     {
       "title": "Getting Help",
       "text": "How can I get help with Agents Toolkit?"
     }
   ]
   ```

For more information, see [Conversation starters object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#conversation-starters-object).

1. Select **Provision** in the **Lifecycle** pane of the Agents Toolkit.

The updated conversation starters will be available in your declarative agent after you refresh the page.

![A screenshot showing the conversation starters from the declarative agent in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/build-da/ttk/conversation-starters.png)

## Next step

[Add knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-knowledge)
