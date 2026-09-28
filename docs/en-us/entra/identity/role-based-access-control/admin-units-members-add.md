<!-- Source: https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-members-add -->
<!-- Sitemap-Last-Modified: 2026-03-04 -->

# Add users, groups, or devices to an administrative unit

In Microsoft Entra ID, you can add users, groups, or devices to an administrative unit to limit the scope of role permissions. Adding a group to an administrative unit brings the group itself into the management scope of the administrative unit, but **not** the members of the group. For additional details on what scoped administrators can do, see [Administrative units in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units).

This article describes how to add users, groups, or devices to administrative units manually. For information about how to add users or devices to administrative units dynamically using rules, see [Manage users or devices for an administrative unit with rules for dynamic membership groups](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-members-dynamic).

## Prerequisites

- Microsoft Entra ID P1 or P2 license for each administrative unit administrator
- Microsoft Entra ID Free licenses for administrative unit members
- To add existing users, groups, or devices:

  - Privileged Role Administrator

- To create new groups:

  - Groups Administrator \(scoped to the administrative unit or entire directory\)

- [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) module when using PowerShell
- Admin consent when using Graph Explorer for Microsoft Graph API

For more information, see [Prerequisites to use PowerShell or Graph Explorer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/prerequisites).

- [Admin center](#tabpanel_1_admin-center)
- [PowerShell](#tabpanel_1_ms-powershell)
- [Graph API](#tabpanel_1_ms-graph)

You can add users, groups, or devices to administrative units using the Microsoft Entra admin center. You can also add users in a bulk operation or create a new group in an administrative unit.

### Add a single user, group, or device to administrative units

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **Entra ID**.
3. Browse to one of the following:

   - **Users** > **All users**
   - **Groups** > **All groups**
   - **Devices** > **All devices**

4. Select the user, group, or device you want to add to administrative units.
5. Select **Administrative units**.
6. Select **Assign to administrative unit**.
7. In the **Select** pane, select the administrative units and then select **Select**.

   [![Screenshot of the Administrative units page for adding a user to an administrative unit.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/assign-users-individually.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/assign-users-individually.png#lightbox)

### Add users, groups, or devices to a single administrative unit

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **Entra ID** > **Roles & admins** > **Admin units**.
3. Select the administrative unit you want to add users, groups, or devices to.
4. Select one of the following:

   - **Users**
   - **Groups**
   - **Devices**

5. Select **Add member**, **Add**, or **Add device**.
6. In the **Select** pane, select the users, groups, or devices you want to add to the administrative unit and then select **Select**.

   [![Screenshot of adding multiple devices to an administrative unit.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/admin-unit-members-add.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/admin-unit-members-add.png#lightbox)

### Add users to an administrative unit in a bulk operation

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **Entra ID** > **Roles & admins** > **Admin units**.
3. Select the administrative unit you want to add users to.
4. Select **Users** > **Bulk operations** > **Bulk add members**.

   [![Screenshot of the Users page for assigning users to an administrative unit as a bulk operation.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/bulk-assign-to-admin-unit.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/bulk-assign-to-admin-unit.png#lightbox)
5. In the **Bulk add members** pane, download the comma-separated values \(CSV\) template.
6. Edit the downloaded CSV template with the list of users you want to add.

   Add one user principal name \(UPN\) in each row. Don't remove the first two rows of the template.
7. Save your changes and upload the CSV file.

   [![Screenshot of an edited CSV file for adding users to an administrative unit in bulk.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/bulk-user-entries.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/bulk-user-entries.png#lightbox)
8. Select **Submit**.

### Create a new group in an administrative unit

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Groups Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#groups-administrator).
2. Browse to **Entra ID** > **Roles & admins** > **Admin units**.
3. Select the administrative unit you want to create a new group in.
4. Select **Groups**.
5. Select **New group** and complete the steps to create a new group.

   [![Screenshot of the Administrative units page for creating a new group in an administrative unit.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/admin-unit-create-group.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-members-add/admin-unit-create-group.png#lightbox)

Use the [New-MgDirectoryAdministrativeUnitMemberByRef](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/new-mgdirectoryadministrativeunitmemberbyref) command to add user, groups, or devices to an administrative unit or create a new group in an administrative unit.

### Add users to an administrative unit

```powershell
$adminUnitObj = Get-MgDirectoryAdministrativeUnit -Filter "DisplayName eq '{admin-unit-id}'"
$userObj = Get-MgUser -Filter "UserPrincipalName eq '{user-principal-name}'"
$odataId = "https://graph.microsoft.com/v1.0/users/" + $userObj.Id
New-MgDirectoryAdministrativeUnitMemberByRef -AdministrativeUnitId $adminUnitObj.Id -OdataId $odataId
```

### Add groups to an administrative unit

```powershell
$adminUnitObj = Get-MgDirectoryAdministrativeUnit -Filter "DisplayName eq '{admin-unit-id}'"
$groupObj = Get-MgGroup -Filter "DisplayName eq 'group-name'"
$odataId = "https://graph.microsoft.com/v1.0/groups/" + $groupObj.Id
New-MgDirectoryAdministrativeUnitMemberByRef -AdministrativeUnitId $adminUnitObj.Id -OdataId $odataId
```

### Add devices to an administrative unit

```powershell
$adminUnitObj = Get-MgDirectoryAdministrativeUnit -Filter "DisplayName eq '{admin-unit-id}'"
$odataId = "https://graph.microsoft.com/v1.0/devices/{device-id}"
New-MgDirectoryAdministrativeUnitMemberByRef -AdministrativeUnitId $adminUnitObj.Id -OdataId $odataId
```

### Create a new group in an administrative unit

```powershell
$adminUnitObj = Get-MgDirectoryAdministrativeUnit -Filter "DisplayName eq '{admin-unit-id}'"
$params = @{
    "@odata.type" = "#microsoft.graph.group"
    description = "{group-description}"
    displayName = "{group-name}"
    groupTypes = @(
        "Unified"
    )
    mailEnabled = $false
    mailNickname = "{group-name}"
    securityEnabled = $true
}
New-MgDirectoryAdministrativeUnitMember -AdministrativeUnitId $adminUnitObj.Id -BodyParameter $params
```

Use the [Add a member](https://learn.microsoft.com/en-us/graph/api/administrativeunit-post-members) API to add users, groups, or devices to an administrative unit or create a new group in an administrative unit.

### Add users to an administrative unit

Request

```http
POST https://graph.microsoft.com/v1.0/directory/administrativeUnits/{admin-unit-id}/members/$ref
```

Body

```http
{
    "@odata.id":"https://graph.microsoft.com/v1.0/users/{user-id}"
}
```

Example

```http
{
    "@odata.id":"https://graph.microsoft.com/v1.0/users/john@example.com"
}
```

### Add groups to an administrative unit

Request

```http
POST https://graph.microsoft.com/v1.0/directory/administrativeUnits/{admin-unit-id}/members/$ref
```

Body

```http
{
    "@odata.id":"https://graph.microsoft.com/v1.0/groups/{group-id}"
}
```

Example

```http
{
    "@odata.id":"https://graph.microsoft.com/v1.0/groups/871d21ab-6b4e-4d56-b257-ba27827628f3"
}
```

### Add devices to an administrative unit

Request

```http
POST https://graph.microsoft.com/v1.0/directory/administrativeUnits/{admin-unit-id}/members/$ref
```

Body

```http
{
    "@odata.id":"https://graph.microsoft.com/v1.0/devices/{device-id}"
}
```

### Create a new group in an administrative unit

To create a new group directly in an administrative unit, use the following request. To add an existing group instead, see **Add groups to an administrative unit** earlier in this article.

Request

```http
POST https://graph.microsoft.com/v1.0/directory/administrativeUnits/{admin-unit-id}/members
```

Body

```http
{
    "@odata.type": "#Microsoft.Graph.Group",
    "description": "{Example group description}",
    "displayName": "{Example group name}",
    "groupTypes": [
        "Unified"
    ],
    "mailEnabled": true,
    "mailNickname": "{examplegroup}",
    "securityEnabled": false
}
```

## Next steps

- [Administrative units in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units)
- [Assign Microsoft Entra roles with administrative unit scope](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal)
- [Manage users or devices for an administrative unit with rules for dynamic membership groups](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-members-dynamic)
- [Remove users, groups, or devices from an administrative unit](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-members-remove)
