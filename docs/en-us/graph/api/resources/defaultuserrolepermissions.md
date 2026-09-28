<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/defaultuserrolepermissions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# defaultUserRolePermissions resource type

Contains certain customizable permissions of default user role in Microsoft Entra ID.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedToCreateApps | Boolean | Indicates whether the default user role can create applications. This setting corresponds to the *Users can register applications* setting in the [User settings menu in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/users-default-permissions?context=graph%2Fcontext#restrict-member-users-default-permissions). |
| allowedToCreateSecurityGroups | Boolean | Indicates whether the default user role can create security groups. This setting corresponds to the following menus in the Microsoft Entra admin center:  <br><br><br><li> <em>The Users can create security groups in Microsoft Entra admin centers, API or PowerShell</em> setting in the <a href="https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/groups-self-service-management" data-linktype="absolute-path">Group settings menu</a>. </li><br><br><li> <em>Users can create security groups</em> setting in the <a href="https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/users-default-permissions?context=graph%2Fcontext#restrict-member-users-default-permissions" data-linktype="absolute-path">User settings menu</a>.</li> |
| allowedToCreateTenants | Boolean | Indicates whether the default user role can create tenants. This setting corresponds to the *Restrict non-admin users from creating tenants* setting in the [User settings menu in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/users-default-permissions?context=graph%2Fcontext#restrict-member-users-default-permissions).  <br>  <br>When this setting is `false`, users assigned the [Tenant Creator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?context=graph%2Fcontext#tenant-creator) role can still create tenants. |
| permissionGrantPoliciesAssigned | String collection | Indicates if user consent to apps is allowed, and if it is, which permission to grant consent and which app consent policy \(permissionGrantPolicy\) govern the permission for users to grant consent. Value should be in the format `managePermissionGrantsForSelf.{id}`, where `{id}` is the **id** of a built-in or custom [app consent policy](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/manage-app-consent-policies). An empty list indicates user consent to apps is disabled. |
| allowedToReadBitlockerKeysForOwnedDevice | Boolean | Indicates whether the registered owners of a device can read their own BitLocker recovery keys with default user role. |
| allowedToReadOtherUsers | Boolean | Indicates whether the default user role can read other users. **DO NOT SET THIS VALUE TO `false`**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowedToCreateApps": true,
  "allowedToCreateSecurityGroups": true,
  "allowedToReadBitlockerKeysForOwnedDevice": true,
  "allowedToReadOtherUsers": true,
  "allowedToCreateTenants": true,
  "permissionGrantPoliciesAssigned": ["String"]
}
```
