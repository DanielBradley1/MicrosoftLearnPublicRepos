<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/agent-handoff -->
<!-- Sitemap-Last-Modified: 2026-07-09 -->

# Agent Handoff for Employee Self-Service agent

Agent handoff allows the Employee Self-Service agent to delegate user queries to other specialized agents within the system. When a user prompt falls outside the Employee Self-Service agent's primary scope, but can be better handled by another agent in Microsoft Copilot, agent handoff transfers the conversation to the appropriate agent.

These agents can include a line of business \(LOB\) agent published by the tenant from Microsoft Copilot, Copilot Studio, or Azure Foundry, or a third-party agent available in the Microsoft Copilot agent store, like Workday, Now Assist, or SAP Joule.

To enhance this, Employee Self-Service agent now supports contextual handoff, which passes both the conversation history and the user's original prompt to the target agent. This forwarding avoids a disconnected experience where users would have to repeat their query, providing a smooth transition and maintaining continuity.

This functionality invokes the appropriate specialized agent. This design ensures employees receive the most accurate and context-aware responses all inside Employee Self-Service. Employees don't need to know which agent to talk to or navigate to other agents to get their queries answered. Agent handoff creates a unified and context-aware conversational experience that improves employee satisfaction.

Note

Handoff requires that the target agent is configured and available in the customer's environment.

## Creating custom handoff topics with the sample template

You can create your own handoff topics for specialized scenarios by using the sample handoff template provided. A sample template topic named **Agenthandoff-scenarioname** is found in the Employee Self-Service solution.

1. **Clone the topic**: Make a copy of the **Agenthandoff-scenarioname** topic and give it a descriptive name that reflects its purpose.
2. **Update the topic description**: In the cloned topic, edit the trigger node. In the **Describe what the topic does** section, provide a clear and comprehensive description of the user intents that should trigger this handoff. For better intent matching, add a set of valid example phrases. This description and examples are used by the model to route user queries correctly.
3. **Locate the ID of the target agent for handoff**: Go to the **Agents** section on the Microsoft 365 page, search for the agent you want to hand off to, then select the three-dot menu \(**...**\) next to it and select **Share**. This action copies the agent's shareable link to your clipboard. The link has this format: `https://m365.cloud.microsoft/chat/?titleId=<GPT_ID>`. The value of the `titleId` parameter, shown as `<GPT_ID>`,is the GPT ID required for handoff configuration.
4. **Set the handoff agent ID**: In the topic's flow, find the **SetVariable** node that sets the **Topic.HandoffAgentId**. Replace the placeholder value with the GPT ID from the previous step.
5. **Customize the user message** \(optional\): You can modify the message shown to the user before the handoff occurs. This message is defined in the **Question** node and informs the user that they're being transferred to a specialist.

By following these steps, you can build and deploy custom routing logic to any agent in your ecosystem.

Note

Agent handoff must be tested in Copilot Chat. The "Test" view in Copilot Studio doesn't support handoff.

## Handoff Accelerators

The Employee Self-Service agent solution comes with a set of preconfigured handoff topics that are designed to work with common enterprise systems. These topics serve as ready-to-use templates for routing queries to the correct specialized agent.

The available out-of-the-box handoff topics include:

| Table name | Description | Package |
| --- | --- | --- |
| Workday employee handoff scenarios | Routes queries about a user's own information, such as job function, contact details, education, leave balance, and providing feedback. | Workday |
| Workday manager handoff scenarios | Routes queries related to a manager's direct reports, including service anniversaries, job functions, cost center, team goals, and employee transfers. | Workday |
| ServiceNow ITSM employee handoff scenarios | Routes common IT-related tasks, such as requesting equipment or software, managing approvals, reporting asset issues, and reporting lost or damaged assets. | ServiceNow IT |

By default, all these topics are **disabled**. You must manually configure and enable them to activate the handoff functionality.

## Handoff in action

Check out [this video](https://www.youtube.com/watch?v=UzAOD6DreA0&list=PLR9nK3mnD-OUov7JnGBoy_u3TwSrIT1Ln&index=2) to see an example of the Employee Self-Service agent handoff.
