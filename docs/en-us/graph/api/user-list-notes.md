<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-list-notes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# List notes

Namespace: microsoft.graph

Get a list of the [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) objects in the user's *Notes* folder.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ShortNotes.Read | ShortNotes.ReadWrite |
| Delegated \(personal Microsoft account\) | ShortNotes.Read | ShortNotes.ReadWrite |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/notes
GET /users/{id | userPrincipalName}/notes
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$orderby`, `$top`, `$skip`, and `$count` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The following properties support `$filter`:

- **subject**: `eq`, `ne`, `startsWith`
- **createdDateTime**: `eq`, `ne`, `ge`, `le`, `gt`, `lt`
- **lastModifiedDateTime**: `eq`, `ne`, `ge`, `le`, `gt`, `lt`
- **hasAttachments**: `eq`

The following properties support `$orderby`: **createdDateTime**, **lastModifiedDateTime**, and **subject**.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/me/notes?$select=id,subject,bodyPreview,lastModifiedDateTime&$orderby=lastModifiedDateTime desc&$top=20
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user-id')/notes(id,subject,bodyPreview,lastModifiedDateTime)",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/me/notes?$select=id,subject,bodyPreview,lastModifiedDateTime&$orderby=lastModifiedDateTime+desc&$top=20&$skiptoken=abc123",
  "value": [
    {
      "id": "AAMkAGI2THVSAAA=",
      "subject": "Team Standup - Jan 20",
      "bodyPreview": "Completed tasks: Feature A, Feature B. In progress: Feature C",
      "lastModifiedDateTime": "2024-01-20T09:15:00Z"
    },
    {
      "id": "AAMkAGI2THVSAAB=",
      "subject": "Shopping List",
      "bodyPreview": "Milk, Eggs, Bread, Coffee",
      "lastModifiedDateTime": "2024-01-19T18:30:00Z"
    }
  ]
}
```
