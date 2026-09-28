<!-- Source: https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-create -->
<!-- Sitemap-Last-Modified: 2026-06-28 -->

# Create a custom role in Microsoft Entra ID

This article describes how to create a custom role to manage access to Microsoft Entra resources using the Microsoft Entra admin center, Microsoft Graph PowerShell, or Microsoft Graph API. If you want to instead create a custom role to manage access to Azure resources, see [Create or update Azure custom roles using the Azure portal](https://learn.microsoft.com/en-us/azure/role-based-access-control/custom-roles-portal).

For the basics of custom roles, see the [custom roles overview](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-overview). The role can be assigned either at the directory-level scope or an app registration resource scope only. For information about the maximum number of custom roles that can be created in a Microsoft Entra organization, see [Microsoft Entra service limits and restrictions](https://learn.microsoft.com/en-us/entra/identity/users/directory-service-limits-restrictions).

Custom roles can only include permissions that are enabled for custom use. The available categories are [app registrations](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-available-permissions), [enterprise applications](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-enterprise-app-permissions), [consent](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-consent-permissions), [devices](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-device-permissions), [users](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-user-permissions), and [groups](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-group-permissions).

## Prerequisites

- Microsoft Entra ID P1 or P2 license
- Privileged Role Administrator
- [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) module when using PowerShell
- Admin consent when using Graph explorer for Microsoft Graph API

For more information, see [Prerequisites to use PowerShell or Graph Explorer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/prerequisites).

- [Admin center](#tabpanel_1_admin-center)
- [PowerShell](#tabpanel_1_ms-powershell)
- [Graph API](#tabpanel_1_ms-graph)

### Create a custom role

These steps describe how to create a custom role in the Microsoft Entra admin center to manage app registrations.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **Entra ID** > **Roles & admins**.
3. Select **New custom role**.

   [![Screenshot of Roles and administrators page in Microsoft Entra admin center.](https://learn.microsoft.com/en-us/entra/media/common/entra-roles-admins.png)](https://learn.microsoft.com/en-us/entra/media/common/entra-roles-admins.png#lightbox)
4. On the **Basics** tab, provide a name and description for the role.

   You can clone the baseline permissions from a custom role but you can't clone a built-in role.

   [![Screenshot of Basics tab to provide a name and description for a custom role.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/custom-create/basics-tab.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/custom-create/basics-tab.png#lightbox)
5. On the **Permissions** tab, select the permissions necessary to manage basic properties and credential properties of app registrations. For a detailed description of each permission, see [Application registration subtypes and permissions in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-available-permissions).

   1. First, enter "credentials" in the search bar and select the `microsoft.directory/applications/credentials/update` permission.

      [![Screenshot of Permissions tab to select the permissions for a custom role.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/custom-create/permissions-tab.png)](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/custom-create/permissions-tab.png#lightbox)
   2. Next, enter "basic" in the search bar, select the `microsoft.directory/applications/basic/update` permission, and then click **Next**.

6. On the **Review + create** tab, review the permissions and select **Create**.

   Your custom role will show up in the list of available roles to assign.

### Sign in

Use the [Connect-MgGraph](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.authentication/connect-mggraph) command to sign in to your tenant.

```PowerShell
Connect-MgGraph -Scopes "RoleManagement.ReadWrite.Directory"
```

### Create a custom role

Create a new role using the following PowerShell script:

```PowerShell
# Basic role information
$displayName = "Application Support Administrator"
$description = "Can manage basic aspects of application registrations."
$templateId = (New-Guid).Guid
      
# Set of permissions to grant
$rolePermissions = @{
    "allowedResourceActions" = @(
        "microsoft.directory/applications/basic/update",
        "microsoft.directory/applications/credentials/update"
    )
}
      
# Create new custom admin role
$customAdmin = New-MgRoleManagementDirectoryRoleDefinition -RolePermissions $rolePermissions `
    -DisplayName $displayName -Description $description -TemplateId $templateId -IsEnabled:$true
```

### Update a custom role

```powershell
# Update role definition
# This works for any writable property on role definition. You can replace display name with other
# valid properties.
Update-MgRoleManagementDirectoryRoleDefinition -UnifiedRoleDefinitionId c4e39bd9-1100-46d3-8c65-fb160da0071f `
   -DisplayName "Updated DisplayName"
```

### Delete a custom role

```powershell
# Delete role definition
Remove-MgRoleManagementDirectoryRoleDefinition -UnifiedRoleDefinitionId c4e39bd9-1100-46d3-8c65-fb160da0071f
```

### Create a custom role

Follow these steps:

1. Use the [Create unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roledefinitions) API to create a custom role.

   ```HTTP
   POST https://graph.microsoft.com/v1.0/roleManagement/directory/roleDefinitions
   ```


   Body


   ```HTTP
   {
       "description": "Can manage basic aspects of application registrations.",
       "displayName": "Application Support Administrator",
       "isEnabled": true,
       "templateId": "<GUID>",
       "rolePermissions": [
           {
               "allowedResourceActions": [
                   "microsoft.directory/applications/basic/update",
                   "microsoft.directory/applications/credentials/update"
               ]
           }
       ]
   }
   ```


   Note


   The `"templateId": "GUID"` is an optional parameter that's sent in the body depending on the requirement. If you have a requirement to create multiple different custom roles with common parameters, it's best to create a template and define a `templateId` value. You can generate a `templateId` value beforehand by using the PowerShell cmdlet `(New-Guid).Guid`.

2. Use the [Create unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignments) API to assign the custom role.

   ```http
   POST https://graph.microsoft.com/v1.0/roleManagement/directory/roleAssignments
   ```


   Body


   ```http
   {
   "principalId":"<GUID OF USER>",
   "roleDefinitionId":"<GUID OF ROLE DEFINITION>",
   "directoryScopeId":"/<GUID OF APPLICATION REGISTRATION>"
   }
   ```

## Related content

- [Assign Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal)
- [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference)
- [Comparison of default guest and member user permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions?context=azure/active-directory/roles/context/ugr-context)
