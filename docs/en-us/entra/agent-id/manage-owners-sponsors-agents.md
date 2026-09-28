<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/manage-owners-sponsors-agents -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# Add and manage owners and sponsors for agent identities and blueprints

Owners and sponsors play distinct governance roles for agent identity blueprints and agent identities in Microsoft Entra ID. Owners are technical administrators who can manage the configuration and operations of an agent. Sponsors are business owners who are accountable for the agent's purpose, lifecycle decisions, and access reviews.

This article walks you through adding and removing owners and sponsors using the Microsoft Entra admin center. For more information about the roles and responsibilities of owners and sponsors, see [owners, sponsors, and managers](https://learn.microsoft.com/en-us/entra/agent-id/agent-owners-sponsors-managers).

## Prerequisites

To manage owners and sponsors, you must:

- Have the [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator) role.
- Be an existing owner of the agent identity blueprint or agent identity you want to manage.

## Add an owner or sponsor to an agent blueprint

When managing agent identity blueprint owners and sponsors, you can assign them to either the agent identity blueprint or the agent blueprint principal using the respective tabs.

Note

When you use a dynamic membership group as a sponsor, it can take up to 24 hours after a membership rule change or a user property change before the authorization check on sponsorship succeeds. Plan accordingly when assigning dynamic groups as sponsors for agent identities or blueprints.

[![Screenshot of the owners and sponsors page for a blueprint showing the list of owners and sponsors with their roles.](https://learn.microsoft.com/en-us/entra/agent-id/media/manage-owners-sponsors-agents/blueprint-owners-sponsors.png)](https://learn.microsoft.com/en-us/entra/agent-id/media/manage-owners-sponsors-agents/blueprint-owners-sponsors.png#lightbox)

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as an [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator) or owner of the agent identity blueprint.
2. Browse to **Entra ID** > **Agents** > **Agent blueprints**.
3. Select the blueprint you want to manage.
4. Under **Access** select **Owners and sponsors**.
5. Select either the **Agent blueprint** or **Agent blueprint principal** tab, depending on which you want to manage.
6. Select **Add** > **Add owner** or **Add sponsor**, depending on which you want to add.
7. Search for and select the users and groups \(for sponsors only\) you want to add.
8. Select **Add**.

## Add an owner or sponsor to an agent identity

The process for adding owners and sponsors to individual agent identities is similar to blueprints.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as an [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator) or owner of the agent identity.
2. Browse to **Entra ID** > **Agents** > **Agent identities**.
3. Select the agent identity you want to manage.
4. Under **Access** select **Owners and sponsors**.
5. Select **Add** > **Add owner** or **Add sponsor** depending on which you want to add.
6. Search for and select the users and groups \(for sponsors only\) you want to add.
7. Select **Add**.

## Remove an owner or sponsor

### Remove from blueprints

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as an [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator) or owner of the agent identity blueprint.
2. Browse to **Entra ID** > **Agents** > **Agent blueprints**.
3. Select the blueprint you want to manage.
4. Select **Owners and sponsors** from the left menu.
5. Select either the **Agent blueprint** or **Agent blueprint principal** tab, depending on which you want to manage.
6. Select the checkbox next to the owner or sponsor you want to remove.
7. Select **Remove**.

### Remove from agent identities

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as an [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator) or owner of the agent identity.
2. Browse to **Entra ID** > **Agents** > **Agent identities**.
3. Select the agent identity you want to manage.
4. Under **Access** select **Owners and sponsors**.
5. Select the checkbox next to the owner or sponsor you want to remove.
6. Select **Remove**.

## Related content

- [Owners, sponsors, and managers](https://learn.microsoft.com/en-us/entra/agent-id/agent-owners-sponsors-managers)
- [View and manage agent identity blueprints](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-blueprint)
- [Create an agent identity blueprint](https://learn.microsoft.com/en-us/entra/agent-id/create-blueprint)
