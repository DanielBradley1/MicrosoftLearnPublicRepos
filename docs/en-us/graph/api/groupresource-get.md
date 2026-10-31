<!-- Source: https://learn.microsoft.com/en-us/graph/api/groupresource-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-29 -->

# Get groupResource

Namespace: microsoft.graph

Read the properties and relationships of a [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrivilegedAccess.Read.AzureADGroup | PrivilegedAccess.ReadWrite.AzureADGroup |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrivilegedAccess.Read.AzureADGroup | PrivilegedAccess.ReadWrite.AzureADGroup |

Note

In delegated scenarios that use work or school accounts, any Microsoft Entra ID member user can call this API if the required permissions are granted.

## HTTP request

```http
GET /identityGovernance/privilegedAccess/group/resources/{groupId}
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/group/resources/a13fc7b0-a4ff-45fc-82c4-1d31a807426a
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/group/resources/$entity",
  "id": "a13fc7b0-a4ff-45fc-82c4-1d31a807426a"
}
```
