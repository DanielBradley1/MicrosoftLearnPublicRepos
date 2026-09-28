<!-- Source: https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/oauth2permissiongrants -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# oauth2PermissionGrants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Terraform files.

### Resource deployment

Choose the least privileged permission from the following table to create or update a `oauth2PermissionGrants` resource.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DelegatedPermissionGrant.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DelegatedPermissionGrant.ReadWrite.All | Directory.ReadWrite.All |

### Read existing resources only

Choose the least privileged permission from the following table to read a `oauth2PermissionGrants` resource using the `msgraph_resource` data source.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | DelegatedPermissionGrant.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | DelegatedPermissionGrant.ReadWrite.All, Directory.ReadWrite.All |

## Resource format

To create a `oauth2PermissionGrants` resource, add the following Terraform configuration to your Terraform configuration.

```terraform
resource "msgraph_resource" "symbolicname" {
  url = "oauth2PermissionGrants@beta"
  body = {
    clientId = "string"
    consentType = "string"
    id = "string"
    principalId = "string"
    resourceId = "string"
    scope = "string"
  }
}
```

## Property values

### oauth2PermissionGrants

| Name | Description | Value |
| --- | --- | --- |
| apiVersion | The resource api version | 'beta' \(ReadOnly\) |
| clientId | The object id \(not appId\) of the client service principal for the application that's authorized to act on behalf of a signed-in user when accessing an API. Required. | string |
| consentType | Indicates if authorization is granted for the client application to impersonate all users or only a specific user. AllPrincipals indicates authorization to impersonate all users. Principal indicates authorization to impersonate a specific user. Consent on behalf of all users can be granted by an administrator. Nonadmin users might be authorized to consent on behalf of themselves in some cases, for some delegated permissions. Required. | string |
| id | The unique identifier for an entity. Read-only. | string |
| principalId | The id of the user on behalf of whom the client is authorized to access the resource, when consentType is Principal. If consentType is AllPrincipals this value is null. Required when consentType is Principal. | string |
| resourceId | The id of the resource service principal to which access is authorized. This identifies the API that the client is authorized to attempt to call on behalf of a signed-in user. | string |
| scope | A space-separated list of the claim values for delegated permissions that should be included in access tokens for the resource application \(the API\). For example, openid User.Read GroupMember.Read.All. Each claim value should match the value field of one of the delegated permissions defined by the API, listed in the oauth2PermissionScopes property of the resource service principal. Must not exceed 3,850 characters in length. | string |
| type | The resource type | 'Microsoft.Graph/oauth2PermissionGrants' \(ReadOnly\) |
