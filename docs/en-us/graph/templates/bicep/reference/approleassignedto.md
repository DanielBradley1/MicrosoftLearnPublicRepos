<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/reference/approleassignedto?view=graph-bicep-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Microsoft.Graph appRoleAssignedTo

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Bicep files.

### Resource deployment

Choose the least privileged permission from the following table to create or update a Microsoft.Graph/appRoleAssignedTo resource.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AppRoleAssignment.ReadWrite.All and Application.Read.All | AppRoleAssignment.ReadWrite.All and Directory.Read.All, Application.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AppRoleAssignment.ReadWrite.All and Application.Read.All | AppRoleAssignment.ReadWrite.All and Directory.Read.All, Application.ReadWrite.All |

### Read existing resources only

Choose the least privileged permission from the following table to read a Microsoft.Graph/appRoleAssignedTo resource using the `existing` keyword.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.Read.All | Application.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.Read.All | Application.ReadWrite.All, Application.ReadWrite.OwnedBy, Directory.Read.All, Directory.ReadWrite.All |

## Resource format

To create a Microsoft.Graph/appRoleAssignedTo resource, add the following Bicep to your template.

```bicep
resource symbolicname 'Microsoft.Graph/appRoleAssignedTo@v1.0' = {
  appRoleId: 'string'
  principalId: 'string'
  resourceDisplayName: 'string'
  resourceId: 'string'
}
```

## Property values

### appRoleAssignedTo

| Name | Description | Value |
| --- | --- | --- |
| apiVersion | The resource api version | 'v1.0' \(ReadOnly\) |
| appRoleId | The identifier \(id\) for the app role that's assigned to the principal. This app role must be exposed in the appRoles property on the resource application's service principal \(resourceId\). If the resource application hasn't declared any app roles, a default app role ID of 00000000-0000-0000-0000-000000000000 can be specified to signal that the principal is assigned to the resource app without any specific app roles. Required on create. | string \(Required\)  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| createdDateTime | The time when the app role assignment was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string \(ReadOnly\) |
| deletedDateTime | Date and time when this object was deleted. Always null when the object hasn't been deleted. | string \(ReadOnly\) |
| id | The unique identifier for an entity. Read-only. | string \(ReadOnly\) |
| principalDisplayName | The display name of the user, group, or service principal that was granted the app role assignment. Maximum length is 256 characters. Read-only. | string \(ReadOnly\) |
| principalId | The unique identifier \(id\) for the user, security group, or service principal being granted the app role. Security groups with dynamic memberships are supported. Required on create. | string \(Required\)  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| principalType | The type of the assigned principal. This can either be User, Group, or ServicePrincipal. Read-only. | string \(ReadOnly\) |
| resourceDisplayName | The display name of the resource app's service principal to which the assignment is made. Maximum length is 256 characters. | string |
| resourceId | The unique identifier \(id\) for the resource service principal for which the assignment is made. Required on create. | string \(Required\)  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| type | The resource type | 'Microsoft.Graph/appRoleAssignedTo' \(ReadOnly\) |

## Related content

- [Microsoft Graph API reference](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment)
