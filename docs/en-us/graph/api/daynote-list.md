<!-- Source: https://learn.microsoft.com/en-us/graph/api/daynote-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-14 -->

# List dayNote

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the properties and relationships of all [day notes](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-beta) in a team.

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
GET /teams/{teamsId}/schedule/dayNotes
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The following example shows how to use the `$filter` parameter.

```http
GET /teams/{teamsId}/schedule/dayNotes?$filter=dayNoteDate eq 2023-11-3
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a list of [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/teams/{teamsId}/schedule/dayNotes
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [ 
      {
        "@odata.etag": "\"0404d9d2-0000-0700-0000-65412d480000\"",
        "id": "NOTE_f87ade4c-1107-47b6-b977-0f31c065b209",
        "dayNoteDate": "2023-10-08",
        "sharedDayNote": {
            "contentType": "text",
            "content": "shared note 08"
        },
        "draftDayNote": {
            "contentType": "text",
            "content": "draft note 08"
        }
     },
      {
        "@odata.etag": "\"0404d9d2-0000-0700-0000-65412d480009\"",
        "id": "NOTE_g87ade4c-1107-47b6-b977-0f31c065b209",
        "dayNoteDate": "2023-10-09",
        "sharedDayNote": {
            "contentType": "text",
            "content": "shared note 09"
        },
        "draftDayNote": null
     }
  ]
}
```
