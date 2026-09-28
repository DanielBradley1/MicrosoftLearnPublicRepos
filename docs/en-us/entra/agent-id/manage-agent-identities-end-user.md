<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-identities-end-user -->
<!-- Sitemap-Last-Modified: 2026-09-03 -->

# Manage Agents in end user experience

The Manage Agents feature in Microsoft Entra lets you view and control, [agent identities you own or sponsor](https://learn.microsoft.com/en-us/entra/agent-id/agent-owners-sponsors-managers). [Agents identities](https://learn.microsoft.com/en-us/entra/agent-id/what-are-agent-identities) are special identities, such as bots or automated processes, that act on behalf of users or teams. With the manage agents feature, you can easily see which agents you’re responsible for, review their details, and take action to enable, disable, or request access for them.

Note

This article is for agent identity owners and sponsors. The **Manage agents** menu only appears for users who own or sponsor at least one agent identity. For tenant-wide management by administrators, see [Manage agent identities in your organization](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-identities-admin).

## Manage agents as an agent identity owner or sponsor

1. Sign in to the [My Account end user portal](https://myaccount.microsoft.com/) as either an owner or sponsor of at least one agent identity.
2. If you haven’t opted in to the new homepage yet, select **Use new version** in the banner.

   Note

   If you’re already using the new homepage, the banner still appears with the message "You’re using the new version of the account homepage" and a **Use previous version** button.
3. In the left menu, select **Manage agents**.

   Note

   This menu item will only appear if you're an owner or sponsor of at least one agent identity.
4. Choose either the **Agents you sponsor** or **Agents you own** tab to view your agents.  ![Screenshot of the managed agents page in the My Account portal.](https://learn.microsoft.com/en-us/entra/agent-id/media/manage-agent/manage-agents-list.png)
5. Select an agent to view details about it.  ![Screenshot of the manage agent view.](https://learn.microsoft.com/en-us/entra/agent-id/media/manage-agent/manage-agent-view.png)

## Enable or disable an agent

1. To disable an agent, select it from the list and choose **Disable agent**. This blocks users from being able to access it and prevents it from being issued tokens. This has the same effect as disabling the agent from the admin center.
2. To re-enable, select the agent that is disabled and choose **Enable agent**. This allows users to access it, and allows it to be issued tokens. Note that sponsors can't re-enable agents. They will need an owner or admin's help if one of their agents needs to be re-enabled.

## Request an access package on behalf of an agent identity

As the owner or sponsor of an agent identity, you can request an access package for that agent identity by doing the following steps:

1. Sign in to the My Access portal at [https://myaccess.microsoft.com](https://myaccess.microsoft.com).
2. On the My Access Portal page, select **Access packages**.
3. On the Access packages page, locate the access package you want to request for an agent identity to have, and select **Request**.
4. On the Request pane under **Request details**, select **Requesting for Sponsored agent** or **Requesting for Owned agent**.
5. Select the agent identity and then select **Continue**.

## Next steps

- [Manage agent identities in your organization](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-identities-admin) - Full agent management overview including roles, security, and governance.
- [View and filter agent identities in your tenant](https://learn.microsoft.com/en-us/entra/agent-id/agent-lists) - For organization-wide agent viewing, filtering, and search.
- If an agent needs other access packages, [Request an access package on behalf of an agent identity](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-request-behalf#request-an-access-package-on-behalf-of-an-agent-identity)
- [Governing Agent Identities](https://learn.microsoft.com/en-us/entra/id-governance/agent-id-governance-overview) - Understand sponsor responsibilities and access package governance.
