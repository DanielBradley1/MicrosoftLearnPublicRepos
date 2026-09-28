<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-connected-agents-for-researcher?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# Manage connected agents in the Microsoft 365 admin center

On an agent's **Connected Agents** tab, you can view agents that provide information and answers when users interact with the primary agent. You can also add connected agents to Researcher and Sales. For other agents, you can view the connections configured by the agent developer, but you can't add or remove them.

## What are connected agents

Connected agents are other Copilot-enabled agents that a primary agent can invoke during a conversation. When a user's request falls within a connected agent's domain, the primary agent can delegate the request to that agent.

Important

If a connected agent is external to your organization, the primary agent can include information from its context in the prompt it sends to the connected agent. The primary agent determines what information is needed for the connected agent to respond accurately. Review the connected agent and your organization's data policies before making it available to users.

For connected agents to work, both the primary agent and the connected agent must be acquired for the user. You can install each agent for users from the Microsoft 365 admin center.

## Key details

- **Agents you can connect** - You can add connected agents to Researcher and Sales. For other primary agents, you can only view the connections configured by the agent developer.
- **Types of agents** - Primary agents can connect to declarative agents and agents that are available over the Agent2Agent \(A2A\) protocol.
- **Limit** - An agent can connect to up to 10 other agents.
- **Developer-configured agents** - You can't remove connected agents configured by the agent developer.
- **User access** - Both the primary agent and each connected agent must be acquired for the user.

## Connect agents to Researcher or Sales

1. In the [Microsoft 365 admin center](https://admin.microsoft.com/), go to **Agents** > **All agents**.
2. Select **Researcher** or **Sales**, and then select the **Connected Agents** tab.

   [![Screenshot showing how to connect an agent with Researcher in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/media/agents/connect-agent.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/agents/connect-agent.png?view=o365-worldwide#lightbox)
3. Select **+ Connect agents**.
4. In the **Select agent to connect** pane:

   - Use the search bar to find agents.
   - Check the box next to the agents you want to connect.

5. Select **Save** to confirm.

## Make connected agents available to users

Both the primary agent and its connected agents must be acquired for a user before the primary agent can invoke them. To review and install a connected agent:

1. On the **Connected Agents** tab, select an agent from the list. The agent's details page opens.
2. Install the agent for the users who need access.

Install the primary agent and each connected agent for the users who need them.

## Manage connected agents

- **Remove an agent** - From the **Connected Agents** list, select an agent that an admin added, and then select **Remove**. You can't remove an agent configured by the agent developer.
- **Reset to default** - Use this option to remove all admin-added connections and restore the connections configured by the agent developer.
