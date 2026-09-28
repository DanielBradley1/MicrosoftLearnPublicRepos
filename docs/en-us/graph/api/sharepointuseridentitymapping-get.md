<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointuseridentitymapping-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# Get sharePointUserIdentityMapping

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve a specific [user identity mapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) by the source user principal name \(UPN\). This method looks up existing user mappings and verifies migration configuration.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SharePointCrossTenantMigration.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SharePointCrossTenantMigration.Read.All | Not available. |

## HTTP request

```http
GET /solutions/sharePoint/migrations/crossOrganizationUserMappings(sourceUserPrincipalName='{sourceUserPrincipalName}')
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. You can use `$select` to choose specific properties such as **targetUserIdentity**, **sourceUserIdentity**, or **userType**. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [sharePointUserIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationUserMappings(sourceUserPrincipalName='user1@contoso.com')
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#solutions/sharePoint/migrations/crossOrganizationUserMappings/$entity",
  "id": "AQAAAAEAAAB1c2VyMUBjb250b3NvLmNvbQ",
  "sourceOrganizationId": "11111111-1111-1111-1111-111111111111",
  "userType": "regularUser",
  "sourceUserIdentity": {
    "userPrincipalName": "user1@contoso.com"
  },
  "targetUserIdentity": {
    "userPrincipalName": "admin@fabrikam.onmicrosoft.com"
  },
  "targetUserMigrationData": {
    "email": "admin@fabrikam.onmicrosoft.com"
  }
}
```
