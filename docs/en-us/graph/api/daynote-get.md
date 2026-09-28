<!-- Source: https://learn.microsoft.com/en-us/graph/api/daynote-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# Get dayNote

Namespace: microsoft.graph

Read the properties and relationships of a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.Read.All | Schedule.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.Read.All | Schedule.ReadWrite.All |

## HTTP request

```http
GET /teams/{teamsId}/schedule/dayNotes/{dayNoteId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET /teams/d72f9b8e-4c76-4f50-bf93-51b17aab0cd9/schedule/dayNotes/NOTE_52191d41-ce2d-4295-a477-b75941bd8e0f
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "NOTE_52191d41-ce2d-4295-a477-b75941bd8e0f",
  "dayNoteDate": "2025-01-08",
  "draftDayNote": null,
  "sharedDayNote": {
    "contentType": "text",
    "content": "Expect a lot of customers today with the holiday traffic."
  }
}
```
