<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-list-distributionlists?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# List distributionLists

Namespace: microsoft.graph

Get a list of the [personal distribution lists](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) in the user's mailbox.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Contacts.Read | Contacts.ReadWrite |
| Delegated \(personal Microsoft account\) | Contacts.Read | Contacts.ReadWrite |
| Application | Contacts.Read | Contacts.ReadWrite |

## HTTP request

```http
GET /me/distributionLists
GET /users/{id | userPrincipalName}/distributionLists
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$orderby`, `$top`, `$skip`, and `$count` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/me/distributionLists
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user-id')/distributionLists",
  "value": [
    {
      "@odata.type": "#microsoft.graph.distributionList",
      "id": "AAMkAGI2THVSAAA=",
      "changeKey": "CQAAABYAAABE",
      "createdDateTime": "2024-03-15T10:30:00Z",
      "lastModifiedDateTime": "2024-03-20T14:00:00Z",
      "categories": [],
      "displayName": "Project Team",
      "personId": "e527d18c-9c02-4af4-b5da-729744507c9b"
    }
  ]
}
```
