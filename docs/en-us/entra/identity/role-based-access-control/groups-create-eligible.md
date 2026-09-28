<!-- Source: https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/groups-create-eligible -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Create a role-assignable group in Microsoft Entra ID

This article describes how to create a role-assignable group using the Microsoft Entra admin center, Microsoft Graph PowerShell, or Microsoft Graph API.

With Microsoft Entra ID P1 or P2, you can create [role-assignable groups](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/groups-concept) and assign Microsoft Entra roles to these groups. You create a new role-assignable group by setting **Microsoft Entra roles can be assigned to the group** to **Yes** or by setting the `isAssignableToRole` property set to `true`. A role-assignable group can't be a part of a [dynamic membership group](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership) type. In Microsoft Entra, a single tenant can have a maximum of 500 role-assignable groups.

## Prerequisites

- Microsoft Entra ID P1 or P2 license
- [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator)
- [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) module when using PowerShell
- Admin consent when using Graph explorer for Microsoft Graph API

For more information, see [Prerequisites to use PowerShell or Graph Explorer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/prerequisites).

## Create a role-assignable group

- [Admin center](#tabpanel_1_admin-center)
- [PowerShell](#tabpanel_1_ms-powershell)
- [Graph API](#tabpanel_1_ms-graph)

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **Entra ID** > **Groups** > **All groups**.
3. Select **New group**.
4. On the **New Group** page, provide group type, name, and description.
5. Set **Microsoft Entra roles can be assigned to the group** to **Yes**.

   This option is visible to Privileged Role Administrators because this role can set this option.

   [![Screenshot of option to make group a role-assignable group.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/groups-create-eligible/eligible-switch.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/groups-create-eligible/eligible-switch.png#lightbox)
6. Select the members and owners for the group. You also have the option to assign roles to the group, but assigning a role isn't required here.
7. Select **Create**.

   You see the following message:

   Creating a group to which Microsoft Entra roles can be assigned is a setting that cannot be changed later. Are you sure you want to add this capability?

   [![Screenshot of confirm message when creating a role-assignable group.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/groups-create-eligible/group-create-message.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/groups-create-eligible/group-create-message.png#lightbox)
8. Select **Yes**.

   The group is created with any roles you might have assigned to it.

Use the [New-MgGroup](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.groups/new-mggroup?branch=main) command to create a role-assignable group.

This example shows how to create a Security role-assignable group.

```powershell
Connect-MgGraph -Scopes "Group.ReadWrite.All"
$group = New-MgGroup -DisplayName "Contoso_Helpdesk_Administrators" -Description "Helpdesk Administrator role assigned to group" -MailEnabled:$false -SecurityEnabled -MailNickName "contosohelpdeskadministrators" -IsAssignableToRole:$true
```

This example shows how to create a Microsoft 365 role-assignable group.

```powershell
Connect-MgGraph -Scopes "Group.ReadWrite.All"
$group = New-MgGroup -DisplayName "Contoso_Helpdesk_Administrators" -Description "Helpdesk Administrator role assigned to group" -MailEnabled:$true -SecurityEnabled -MailNickName "contosohelpdeskadministrators" -IsAssignableToRole:$true -GroupTypes "Unified"
```

Use the [Create group](https://learn.microsoft.com/en-us/graph/api/group-post-groups?branch=main) API to create a role-assignable group.

This example shows how to create a Security role-assignable group.

```http
POST https://graph.microsoft.com/v1.0/groups
{
    "description": "Helpdesk Administrator role assigned to group",
    "displayName": "Contoso_Helpdesk_Administrators",
    "isAssignableToRole": true,
    "mailEnabled": false,
    "mailNickname": "contosohelpdeskadministrators",
    "securityEnabled": true
}
```

Response

```http
HTTP/1.1 201 Created
```

This example shows how to create a Microsoft 365 role-assignable group.

```http
POST https://graph.microsoft.com/v1.0/groups
{
  "description": "Helpdesk Administrator role assigned to group",
  "displayName": "Contoso_Helpdesk_Administrators",
  "groupTypes": [
    "Unified"
  ],
  "isAssignableToRole": true,
  "mailEnabled": true,
  "mailNickname": "contosohelpdeskadministrators",
  "securityEnabled": true,
  "visibility" : "Private"
}
```

For this type of group, `isPublic` is always false and `isSecurityEnabled` is always true.

## Next steps

- [Assign Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal)
- [Use Microsoft Entra groups to manage role assignments](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/groups-concept)
- [Troubleshoot Microsoft Entra roles assigned to groups](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/groups-faq-troubleshooting)
