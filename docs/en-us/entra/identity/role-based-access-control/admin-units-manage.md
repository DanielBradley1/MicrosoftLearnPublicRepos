<!-- Source: https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-manage -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# Create or delete administrative units

Administrative units let you subdivide your organization into any unit that you want, and then assign specific administrators that can manage only the members of that unit. For example, you could use administrative units to delegate permissions to administrators of each school at a large university, so they could control access, manage users, and set policies only in the School of Engineering.

This article describes how to create or delete administrative units to restrict the scope of role permissions in Microsoft Entra ID.

## Prerequisites

- Microsoft Entra ID P1 or P2 license for each administrative unit administrator
- Microsoft Entra ID Free licenses for administrative unit members
- Privileged Role Administrator role
- [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) module when using PowerShell
- Admin consent when using Graph Explorer for Microsoft Graph API

For more information, see [Prerequisites to use PowerShell or Graph Explorer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/prerequisites).

## Create an administrative unit

You can create a new administrative unit by using either the Microsoft Entra admin center, Microsoft Entra PowerShell, or Microsoft Graph.

- [Admin center](#tabpanel_1_admin-center)
- [PowerShell](#tabpanel_1_ms-powershell)
- [Graph API](#tabpanel_1_ms-graph)

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **Entra ID** > **Roles & admins** > **Admin units**.

   [![Screenshot of the Administrative units page.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-manage/nav-to-admin-units.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-manage/nav-to-admin-units.png#lightbox)
3. Select **Add**.
4. In the **Name** box, enter the name of the administrative unit. Optionally, add a description of the administrative unit.
5. If you don't want tenant-level administrators to be able to access this administrative unit, set the **Restricted management administrative unit** toggle to **Yes**. For more information, see [Restricted management administrative units](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-restricted-management).

   [![Screenshot showing the Add administrative unit page and the Name box for entering the name of the administrative unit.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-manage/add-new-admin-unit.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-manage/add-new-admin-unit.png#lightbox)
6. Optionally, on the **Assign roles** tab, select a role and then select the users to assign the role to with this administrative unit scope.

   [![Screenshot showing the Add assignments pane to add role assignments with this administrative unit scope.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-manage/assign-roles-admin-unit.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-manage/assign-roles-admin-unit.png#lightbox)
7. On the **Review + create** tab, review the administrative unit and any role assignments.
8. Select the **Create** button.

Use the [Connect-MgGraph](https://learn.microsoft.com/en-us/powershell/microsoftgraph/authentication-commands#using-connect-mggraph) command to sign in to your tenant and consent to the required permissions.

```powershell
Connect-MgGraph -Scopes "AdministrativeUnit.ReadWrite.All"
```

Use the [New-MgDirectoryAdministrativeUnit](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/new-mgdirectoryadministrativeunit) command to create a new administrative unit.

```powershell
$params = @{
    DisplayName = "Seattle District Technical Schools"
    Description = "Seattle district technical schools administration"
    Visibility = "HiddenMembership"
}
$adminUnitObj = New-MgDirectoryAdministrativeUnit -BodyParameter $params
```

Use the [New-MgDirectoryAdministrativeUnit](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/new-mgdirectoryadministrativeunit) command to create a new restricted management administrative unit. Set the `IsMemberManagementRestricted` property to `$true`.

```powershell
$params = @{
    DisplayName = "Contoso Executive Division"
    Description = "Contoso Executive Division administration"
    Visibility = "HiddenMembership"
    IsMemberManagementRestricted = $true
}
$restrictedAU = New-MgDirectoryAdministrativeUnit -BodyParameter $params
```

Use the [Create administrativeUnit](https://learn.microsoft.com/en-us/graph/api/directory-post-administrativeunits) API to create a new administrative unit.

Request

```http
POST https://graph.microsoft.com/v1.0/directory/administrativeUnits
```

Body

```http
{
  "displayName": "North America Operations",
  "description": "North America Operations administration"
}
```

Use the [Create administrativeUnit](https://learn.microsoft.com/en-us/graph/api/directory-post-administrativeunits) API to create a new restricted management administrative unit. Set the `isMemberManagementRestricted` property to `true`.

Request

```http
POST https://graph.microsoft.com/v1.0/directory/administrativeUnits
```

Body

```http
{ 
  "displayName": "Contoso Executive Division",
  "description": "This administrative unit contains executive accounts of Contoso Corp.", 
  "isMemberManagementRestricted": true
}
```

## Delete an administrative unit

In Microsoft Entra ID, you can delete an administrative unit that you no longer need as a unit of scope for administrative roles. Before you delete the administrative unit, you should remove any role assignments with that administrative unit scope.

- [Admin center](#tabpanel_2_admin-center)
- [PowerShell](#tabpanel_2_ms-powershell)
- [Graph API](#tabpanel_2_ms-graph)

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **Entra ID** > **Roles & admins** > **Admin units**.
3. Select the administrative unit you want to delete.
4. Select **Roles and administrators**, and then open a role to view the role assignments.
5. Remove all the role assignments with the administrative unit scope.
6. Browse to **Entra ID** > **Roles & admins** > **Admin units**.
7. Add a check mark next to the administrative unit you want to delete.
8. Select **Delete**.

   [![Screenshot of the administrative unit Delete button and confirmation window.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-manage/select-admin-unit-to-delete.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/admin-units-manage/select-admin-unit-to-delete.png#lightbox)
9. To confirm that you want to delete the administrative unit, select **Yes**.

Use the [Remove-MgDirectoryAdministrativeUnit](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/remove-mgdirectoryadministrativeunit) command to delete an administrative unit.

```powershell
$adminUnitObj = Get-MgDirectoryAdministrativeUnit -Filter "DisplayName eq 'Seattle District Technical Schools'"
Remove-MgDirectoryAdministrativeUnit -AdministrativeUnitId $adminUnitObj.Id
```

Use the [Delete administrativeUnit](https://learn.microsoft.com/en-us/graph/api/administrativeunit-delete) API to delete an administrative unit.

```http
DELETE https://graph.microsoft.com/v1.0/directory/administrativeUnits/{admin-unit-id}
```

## Next steps

- [Add users, groups, or devices to an administrative unit](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-members-add)
- [Assign Microsoft Entra roles with administrative unit scope](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal)
- [Microsoft Entra administrative units: Troubleshooting and FAQ](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-faq-troubleshoot)
