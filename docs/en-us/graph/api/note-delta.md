<!-- Source: https://learn.microsoft.com/en-us/graph/api/note-delta?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# note: delta

Namespace: microsoft.graph

Get a set of [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) objects that were added, updated, or deleted in the user's *Notes* folder since the last delta query. A **delta** function call for notes is similar to a GET request, except that by appropriately applying [state tokens](https://learn.microsoft.com/en-us/graph/delta-query-overview) in one or more of these calls, you can query for incremental changes in the notes.

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
GET /me/notes/delta
GET /users/{id | userPrincipalName}/notes/delta
```

## Query parameters

Tracking changes in notes incurs a round of one or more **delta** function calls. If you use any query parameter \(other than `$deltatoken` and `$skiptoken`\), you must specify it in the initial **delta** request. Microsoft Graph automatically encodes any specified parameters into the token portion of the **@odata.nextLink** or **@odata.deltaLink** URL provided in the response.

| Query parameter | Type | Description |
| :--- | :--- | :--- |
| $deltatoken | String | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the **@odata.deltaLink** URL of the previous **delta** function call, indicating the completion of that round of change tracking. Save and apply the entire **@odata.deltaLink** URL, including this token, in the first request of the next round of change tracking for that collection. |
| $skiptoken | String | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the **@odata.nextLink** URL of the previous **delta** function call, indicating further changes to be tracked. |

This method also supports the `$select`, `$filter`, `$orderby`, and `$top` OData query parameters to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) objects in the response body. The response also includes an **@odata.nextLink** URL or an **@odata.deltaLink** URL.

- If an **@odata.nextLink** URL is returned, more pages of data remain to be retrieved. The application continues making requests using the **@odata.nextLink** URL until an **@odata.deltaLink** URL is included in the response.
- If an **@odata.deltaLink** URL is returned, no more pages of data remain to be returned. Save the **@odata.deltaLink** URL for use in the next **delta** call.

## Examples

### Example 1: Initial sync request

The following example shows the initial sync request to get all notes.

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/me/notes/delta
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user-id')/notes",
  "@odata.deltaLink": "https://graph.microsoft.com/v1.0/me/notes/delta?$deltatoken=abc123def456",
  "value": [
    {
      "id": "AAMkAGI2THVSAAA=",
      "changeKey": "CQAAABYAAABE",
      "createdDateTime": "2024-01-15T10:00:00Z",
      "lastModifiedDateTime": "2024-01-20T11:00:00Z",
      "categories": [],
      "subject": "Updated Note",
      "body": {
        "contentType": "html",
        "content": "<html><body>Updated content</body></html>"
      },
      "bodyPreview": "Updated content",
      "isDeleted": false,
      "hasAttachments": false
    }
  ]
}
```

### Example 2: Subsequent delta request

The following example shows a subsequent sync request using the delta token from the previous response. New, updated, and deleted notes are returned.

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/me/notes/delta?$deltatoken=abc123def456
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user-id')/notes",
  "@odata.deltaLink": "https://graph.microsoft.com/v1.0/me/notes/delta?$deltatoken=xyz789new",
  "value": [
    {
      "id": "AAMkAGI2NEWITEM=",
      "changeKey": "CQAAABYAAABF",
      "subject": "New Note",
      "bodyPreview": "New content",
      "createdDateTime": "2024-01-21T08:00:00Z",
      "lastModifiedDateTime": "2024-01-21T08:00:00Z"
    },
    {
      "@removed": {
        "reason": "deleted"
      },
      "id": "AAMkAGI2DELETED="
    }
  ]
}
```
