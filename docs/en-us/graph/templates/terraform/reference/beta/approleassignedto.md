<!-- Source: https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/approleassignedto -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# appRoleAssignedTo

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Terraform files.

### Resource deployment

Choose the least privileged permission from the following table to create or update a `appRoleAssignedTo` resource.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AppRoleAssignment.ReadWrite.All and Application.Read.All | AppRoleAssignment.ReadWrite.All and Directory.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AppRoleAssignment.ReadWrite.All and Application.Read.All | AppRoleAssignment.ReadWrite.All and Directory.Read.All |

### Read existing resources only

Choose the least privileged permission from the following table to read a `appRoleAssignedTo` resource using the `msgraph_resource` data source.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.Read.All | Application.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.Read.All | Application.ReadWrite.All, Application.ReadWrite.OwnedBy, Directory.Read.All, Directory.ReadWrite.All |

## Resource format

To create a `appRoleAssignedTo` resource, add the following Terraform configuration to your Terraform configuration.

```terraform
resource "msgraph_resource" "symbolicname" {
  url = "appRoleAssignedTo@beta"
  body = {
    appRoleId = "string"
    createdDateTime = "string"
    deletedDateTime = "string"
    id = "string"
    principalDisplayName = "string"
    principalId = "string"
    principalType = "string"
    resourceDisplayName = "string"
    resourceId = "string"
  }
}
```

## Property values

### appRoleAssignedTo

| Name | Description | Value |
| --- | --- | --- |
| apiVersion | The resource api version | 'beta' \(ReadOnly\) |
| appRoleId | The identifier \(id\) for the app role that's assigned to the principal. This app role must be exposed in the appRoles property on the resource application's service principal \(resourceId\). If the resource application hasn't declared any app roles, a default app role ID of 00000000-0000-0000-0000-000000000000 can be specified to signal that the principal is assigned to the resource app without any specific app roles. Required on create. | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| createdDateTime | The time when the app role assignment was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string |
| deletedDateTime | Date and time when this object was deleted. Always null when the object hasn't been deleted. | string |
| id | The unique identifier for an entity. Read-only. | string |
| principalDisplayName | The display name of the user, group, or service principal that was granted the app role assignment. Maximum length is 256 characters. Read-only. | string |
| principalId | The unique identifier \(id\) for the user, security group, or service principal being granted the app role. Security groups with dynamic memberships are supported. Required on create. | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| principalType | The type of the assigned principal. This can either be User, Group, or ServicePrincipal. Read-only. | string |
| resourceDisplayName | The display name of the resource app's service principal to which the assignment is made. Maximum length is 256 characters. | string |
| resourceId | The unique identifier \(id\) for the resource service principal for which the assignment is made. Required on create. | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| type | The resource type | 'Microsoft.Graph/appRoleAssignedTo' \(ReadOnly\) |
