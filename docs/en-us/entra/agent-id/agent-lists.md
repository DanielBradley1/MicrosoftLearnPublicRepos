<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/agent-lists -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# View and filter agent identities in your tenant

Microsoft Entra admin center provides you with a centralized interface to view and filter your agent identities. This comes with the ability to search, filter, sort, and customize columns to find specific agent identities in your tenant.

- To view and manage your agent identity blueprint principals, see [View and manage agent identity blueprints using Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-blueprint).
- To view and manage agents registered in the Agent Registry without an identity, see [manage agent identity blueprints with no identities](https://learn.microsoft.com/en-us/entra/agent-id/manage-agents-without-identity).

## Prerequisites

To view agent identities in your Microsoft Entra tenant, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). No admin role is required for viewing.

To manage agent identities in your Microsoft Entra tenant, you need:

- Agent ID Administrator or Cloud Application Administrator role.
- You can also manage your agent identity if you're the owner of that agent identity, with or without the above roles.

## View a list of agent identities

To view agent identities in your tenant:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com)
2. Browse to **Entra ID** > **Agents** > **Agent identities**.
3. Select any agent identity you'd like to manage.

This page contains a list of all agent identities in your organization. This includes both [agent identity objects](https://learn.microsoft.com/en-us/entra/agent-id/agent-identities) and [agents using a service principal](https://learn.microsoft.com/en-us/entra/agent-id/agent-service-principals).

## Search for an agent identity

- To search for an agent identity, enter either the **name** or **object ID** of the agent identity you want to find in the search box.
- To look up an agent identity by its **Blueprint App ID**, add the **Blueprint App ID** filter. You can further refine the list using filters based on various criteria.

You can select an agent identity from this list to see information like:

- An overview of the agent identity, including:

  - The name, description, and logo for your agent identity
  - The status of that agent identity, and the ability to enable/disable a given agent identity
  - The link to the parent agent identity blueprint

- The list of owners and sponsors for that agent identity
- The agent's access via this agent identity's granted permissions and Microsoft Entra roles
- Audit logs and sign-in logs for that agent identity

## Select viewing options

To customize your view of agent identities, you can change filters or select which columns are shown for each agent identity. Not all columns are shown by default. To see all available columns and edit shown columns, select the **Choose columns** button. The table columns and their filter options are as follows:

| Column Name | Description | Sortable | Filterable | Special notes |
| --- | --- | :---: | :---: | --- |
| **Name** | Display name of the agent identity | ✓ | ✓ | Primary search field; clickable to view details of the agent identity |
| **Created On** | Date when the agent was created | ✓ | ✓ | Filter by "Last N days" |
| **Status** | Current operational state \(Active, or Disabled\) | ✓ | ✓ |  |
| **Object ID** | Unique identifier for agent identity | ✗ | ✓ |  |
| **View Access** | Direct link to agent identity's permissions | ✗ | ✗ | Navigates to the Agent's Access pane, on Permissions tab |
| **Blueprint App ID** | Unique identifier for the agent identity blueprint of this agent identity | ✗ | ✓ | Will be blank for [agents using service principals](https://learn.microsoft.com/en-us/entra/agent-id/agent-service-principals) |
| **Owners and Sponsors** | Direct link to the owners and sponsors for a given agent identity | ✗ | ✗ |  |
| **Uses agent identity** | Represents whether or not this agent has an agent identity object, or utilizes a service principal | ✗ | ✗ | If the answer is "yes," then it uses an agent identity object. If "no" this agent utilizes a service principal |

## Related content

- [Manage agent identities in your organization](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-identities-admin) - Overview of agent identity management including roles, lifecycle, and governance.
- [Manage agents in end user experience](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-identities-end-user) - Owners and sponsors can manage their agents from the My Account portal without admin roles.
- [Conditional Access for Agent ID](https://learn.microsoft.com/en-us/entra/identity/conditional-access/agent-id) - Enforce Conditional Access policies across all agent identities or specific groups.
- [View and manage agent identity blueprints in your tenant](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-blueprint)
