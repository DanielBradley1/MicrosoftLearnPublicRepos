<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/reference/oauth2permissiongrants?view=graph-bicep-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Microsoft.Graph oauth2PermissionGrants

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Bicep files.

### Resource deployment

Choose the least privileged permission from the following table to create or update a Microsoft.Graph/oauth2PermissionGrants resource.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DelegatedPermissionGrant.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DelegatedPermissionGrant.ReadWrite.All | Directory.ReadWrite.All |

### Read existing resources only

Choose the least privileged permission from the following table to read a Microsoft.Graph/oauth2PermissionGrants resource using the `existing` keyword.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | DelegatedPermissionGrant.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | DelegatedPermissionGrant.ReadWrite.All, Directory.ReadWrite.All |

## Resource format

To create a Microsoft.Graph/oauth2PermissionGrants resource, add the following Bicep to your template.

```bicep
resource symbolicname 'Microsoft.Graph/oauth2PermissionGrants@v1.0' = {
  clientId: 'string'
  consentType: 'string'
  principalId: 'string'
  resourceId: 'string'
  scope: 'string'
}
```

## Property values

### oauth2PermissionGrants

| Name | Description | Value |
| --- | --- | --- |
| apiVersion | The resource api version | 'v1.0' \(ReadOnly\) |
| clientId | The object id \(not appId\) of the client service principal for the application that's authorized to act on behalf of a signed-in user when accessing an API. Required. | string \(Required\) |
| consentType | Indicates if authorization is granted for the client application to impersonate all users or only a specific user. AllPrincipals indicates authorization to impersonate all users. Principal indicates authorization to impersonate a specific user. Consent on behalf of all users can be granted by an administrator. Nonadmin users might be authorized to consent on behalf of themselves in some cases, for some delegated permissions. Required. | string \(Required\) |
| id | The unique identifier for an entity. Read-only. | string \(ReadOnly\) |
| principalId | The id of the user on behalf of whom the client is authorized to access the resource, when consentType is Principal. If consentType is AllPrincipals this value is null. Required when consentType is Principal. | string |
| resourceId | The id of the resource service principal to which access is authorized. This identifies the API that the client is authorized to attempt to call on behalf of a signed-in user. | string \(Required\) |
| scope | A space-separated list of the claim values for delegated permissions that should be included in access tokens for the resource application \(the API\). For example, openid User.Read GroupMember.Read.All. Each claim value should match the value field of one of the delegated permissions defined by the API, listed in the oauth2PermissionScopes property of the resource service principal. Must not exceed 3,850 characters in length. | string |
| type | The resource type | 'Microsoft.Graph/oauth2PermissionGrants' \(ReadOnly\) |

## Related content

- [Microsoft Graph API reference](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant)
