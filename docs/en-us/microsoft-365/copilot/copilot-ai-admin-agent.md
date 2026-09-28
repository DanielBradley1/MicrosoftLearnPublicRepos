<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-admin-agent -->
<!-- Sitemap-Last-Modified: 2026-07-10 -->

# Use Microsoft 365 Admin agent

The Microsoft 365 Admin agent is an assistive, agentic experience that helps IT administrators operate Microsoft 365, Microsoft Copilot, and agents at AI scale. Built on the [Agent 365 Platform SDK](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/) and connected to multiple [Model Context Protocol \(MCP\)](https://learn.microsoft.com/en-us/agent-framework/agents/tools/hosted-mcp-tools?pivots=programming-language-csharp) servers, the Microsoft 365 Admin agent shifts administrative work from manual configuration to intent-driven, observable, and governed operations.

The Microsoft 365 Admin agent helps admins perform tasks across different Microsoft 365 services via a single unified surface in Microsoft Copilot Chat, using natural language interactions, contextual guidance, and proactive suggestions to discover, configure, troubleshoot, and manage Microsoft 365 services.

## Prequisites

All Microsoft 365 admins can use the Microsoft 365 Admin agent. No action is required to use the Microsoft 365 Admin agent. The agent is pre-installed in Microosft 365 Copilot Chat for all Microsoft 365 administrators.

- Admins don't need an additional Microsoft Copilot or Agent 365 license to use the Microsoft 365 Admin agent.
- Existing role-based access control \(RBAC\) assignments in Microsoft Entra ID govern the actions admins can take through the agent.
- Role-based permissions for each admin type, such as AI Administrator, Global Administrator, Teams Administrator, and SharePoint Administrator, govern actions like approving agent requests, assigning ownership, and changing tenant settings.

Note

Because the agent honors your existing Microsoft Entra role assignments, the actions you can perform reflect the permissions associated with your admin role. If a capability appears unavailable, verify that your role grants the required permission for that workload.

## Use the Microsoft 365 Admin agent

Admins can start a task in one experience and complete it in another without losing context. Access the Microsoft 365 Admin agent within the Microsoft 365 admin center or Microsoft Copilot Chat. For example, you can start a task by asking the Microsoft 365 Admin agent in Microsoft Copilot Chat, "Who are the unlicensed users in my org?" and then continue the chat in the Microsoft 365 admin center by prompting, "Assign Adele Vance a Microsoft 365 E7 license" without losing the initial prompt and context.

### Microsoft 365 admin center

To use Microsoft 365 Admin agent in the Microsoft 365 admin center, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/).
2. Select the **Copilot** button at the top of the window to launch Copilot in a Microsoft 365 admin center. The Microsoft 365 Admin agent is already pre-selected in the agent picker.
3. Enter an administrative question or instruction in natural language. For example, "List all global admins in my organization." For more examples, see [Example prompts](#example-prompts).

### Microsoft Copilot Chat

To use the first-party Microsoft 365 Admin agent in a Copilot chat, follow these steps:

1. Sign in to [Microsoft Copilot Chat](https://m365.cloud.microsoft/) as a user with an administrator role.
2. In the navigation panel, select **Agents**.
3. Select **Microsoft 365 Admin** agent.
4. Enter an administrative question or instruction in natural language. For example, "List all global admins in my organization." For more examples, see [Example prompts](#example-prompts).

Important

- Any write or execute action proposed by the Microsoft 365 Admin agent requires explicit admin confirmation before it is performed. The agent never makes changes to your tenant on its own. For more information, see [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy).
- Although all admins can use the admin agent, responses and actions depend on the signed-in user's permissions. Admins can only see data and take actions that their assigned roles allow.

## Example prompts

The following sections describe common admin scenarios and provide example prompts for the Microsoft 365 Admin agent.

Note

This article lists only generally available capabilities for Microsoft 365 Admin agent. New scenarios appear in this article as they become available.

### Manage users, licenses, and groups

Use the Microsoft 365 Admin agent to view and manage users, licenses, and groups in your organization.

#### Users

- "List all global admins in my organization."
- "Show me users in Germany with an E5 license assigned."
- "How many users are using Copilot?"

#### Assign licenses

- "How many Copilot licenses do I have?"
- "List all users with a Copilot license."
- "List all pending license requests."
- "Assign Copilot license to user name."

#### Manage groups

- "Which groups have no assigned owner?"
- "Are there any groups with names starting with Test?"

### Copilot management

Use the Microsoft 365 Admin agent to assess Copilot readiness, check and change Copilot settings, and get license assignment recommendations.

#### Copilot readiness

- "Is my org ready for Copilot?"
- "What should I prioritize to get ready for Copilot?"
- "What's the status of data security tasks for Copilot readiness?"

#### Copilot state and settings

- "Can unlicensed users in my tenant access Copilot Chat?"
- "Allow users without a Copilot license to access Copilot Chat for my tenant."
- "Enable automatic file access so Copilot can use users' open files in chats."
- "Are users allowed to generate images with Copilot in my tenant?"
- "Turn off image generation for Copilot for all users."
- "Switch the Copilot AI disclaimer to bold without a custom link."
- "Disable Copilot screen sharing for all users."
- "Disable camera sharing with Copilot to tighten privacy controls."
- "Pin Copilot across Microsoft 365 Apps."
- "What AI providers are available in my org?"
- "Enable Anthropic as a Microsoft AI subprocessor."

### Agent management

Use the Microsoft 365 Admin agent to discover, manage, and monitor agents in your organization.

#### Discover agents in the registry

- "List all agents in my organization."
- "Search for agents with 'Sales' in their display name."
- "Show me all Microsoft agents."
- "List agents from external partners."
- "List all agents built with Copilot Studio."
- "Show me agents created with SharePoint."
- "Show me all blocked agents."
- "Show me agents that don't have an owner."
- "Which agents are available to everyone?"
- "Which agents work in Microsoft Teams?"

#### View agent details and insights

- "Get details for the Analyst agent."
- "Get full details for Microsoft 365 Admin agent, including usage analytics."
- "How many active users does the Researcher agent have?"
- "Give me an overview of the agents in my organization."
- "How many agents don't have an owner?"
- "What is the breakdown of agents by publisher?"

#### Manage agents

- "Block the Asana agent."
- "Deploy the Viva Goals agent to everyone."
- "Deploy the Microsoft 365 Admin agent to Allie Bellew."
- "Remove the Box agent from all users."
- "Assign Justin Wayne as the owner of *agent name*."

#### Manage agent access and sharing

- "Who has access to AI agents in my tenant?"
- "Enable everyone in the organization to access agents."
- "Disable agent access for everyone."
- "Who can share agents?"
- "Enable everyone in the org to share agents."

### Change management

Stay informed about changes affecting your organization.

- "Recap my organization."
- "Recap important information from Microsoft 365 admin centers."
- "What's new in message center?"
- "Summarize all my messages related to Copilot."
- "What are the latest changes for Microsoft Teams?"
- "Show me service health status."
- "Is Microsoft Teams down?"
- "My users are having email delivery problems. Are there any service problems right now?"

### Help and support

Get self-help guidance and view support tickets.

- "How do I set up a domain?"
- "How do I assign a license to a user?"
- "Show me my recent support tickets and their statuses."
- "Show me support tickets related to Copilot."
- "Get help from FastTrack."

### Teams administration

Troubleshoot Microsoft Teams chat policy issues, analyze call and meeting quality, and search Teams configuration data.

- "Why can't internal users delete messages in Teams chat?"
- "Why can't guest users edit messages in Teams chat?"
- "Analyze the call quality of *user* for their meeting with Meeting ID *id*. Were there any quality issues?"
- "List the recent calls and meeting quality information for *user* in the last 7 days."
- "List the most common quality issues in meetings for the last 7 days."
- "Get me all the users and their enterprise voice values."
- "Get me all the phone numbers that aren't assigned yet."
- "Get me the account type for user: *user*."

### Identity, migration, and other admin scenarios

- "What is my tenant ID?"
- "What services are currently active in our organization?"
- "Who is the security compliance contact in my tenant?"
- "I need help with migrating my data from another provider."
- "Show me users enabled for Self-service password reset."
- "Let users reset their own passwords."
- "Get MFA status."
- "Get directory sync status."
- "Which authentication methods do I have on?"
- "Turn on passwordless authentication for my users."

## Frequently asked questions

### How do I block the Microsoft 365 Admin agent?

Administrators who want to restrict use of the Microsoft 365 Admin agent can do so through standard agent governance controls in the Microsoft 365 admin center. From the agent management experience, you can:

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/) as a Global Administrator or AI Administrator.
2. Select to **Agents** > **Registry**.
3. Locate **Microsoft 365 Admin** in the registry.
4. Use the available agent actions to **Block** the agent or to **scope deployment** to specific users or groups instead of the entire organization.

Important

Blocking the Microsoft 365 admin agent restricts administrators in your tenant from invoking it through Microsoft Copilot Chat and admin surfaces. Other admin functionality in the Microsoft 365 admin center is unaffected.

### What data and tools does the Microsoft 365 admin agent use?

The Microsoft 365 Admin agent uses native MCP tools that invoke Microsoft Graph APIs and other Microsoft administrative services to read tenant data and perform actions. Only the Microsoft 365 Admin agent can access native MCP tools. These tools follow the same data handling, compliance, and audit requirements as the underlying admin experiences.

### Are actions taken by the Microsoft 365 Admin agent audited?

Yes, the underlying workload's audit logs, such as Microsoft 365 admin center audit logs, Microsoft Entra audit logs, and Microsoft Teams admin logs, record administrative actions performed through the Microsoft 365 Admin agent, just as if you took the action directly in an admin center.

## Related articles

- [Agent management in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-365-overview)
- [Agent management roles and permissions](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-roles-perms)
- [Overview of Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/overview)
- [License options for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing)
- [Get started with agents in the Microsoft Copilot app](https://support.microsoft.com/microsoft-365-copilot/get-started-with-agents-in-the-microsoft-365-copilot-app)
