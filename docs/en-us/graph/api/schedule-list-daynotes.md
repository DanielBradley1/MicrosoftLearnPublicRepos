<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-list-daynotes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# List dayNote

Namespace: microsoft.graph

Get a list of the [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) objects and their properties.

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

If successful, this method returns a `200 OK` response code and a list of [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET /teams/d72f9b8e-4c76-4f50-bf93-51b17aab0cd9/schedule/dayNotes
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
      "id": "NOTE_52191d41-ce2d-4295-a477-b75941bd8e0f",
      "dayNoteDate": "2025-01-08",
      "draftDayNote": null,
      "sharedDayNote": {
        "contentType": "text",
        "content": "Expect a lot of customers today with the holiday traffic."
      }
    },
    {
      "id": "NOTE_d011e056-5f78-4020-98b2-84ef6f71d008",
      "dayNoteDate": "2025-01-09",
      "sharedDayNote": null,
      "draftDayNote": {
        "contentType": "text",
        "content": "Produce shipment arriving at 11 AM"
      }
    }
  ]
}
```
