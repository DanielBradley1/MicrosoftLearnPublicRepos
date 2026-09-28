<!-- Source: https://learn.microsoft.com/en-us/graph/api/daynote-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create dayNote

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [day note](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-beta) in the schedule.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

## HTTP request

```http
POST /teams/{teamsId}/schedule/dayNotes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| dayNoteDate | Date | The date of the day note. |
| sharedDayNote | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | The draft version of this **dayNote** that is viewable by managers. |
| draftDayNote | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | The shared version of this **dayNote** that is viewable by both employees and managers. |

## Response

If successful, this method returns a `200 OK` response code and a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/teams/{teamsId}/schedule/dayNotes
Content-Type: application/json

{
    "dayNoteDate": "2023-10-08",
    "sharedDayNote": {
        "contentType": "text",
        "content": "shared note 08"
    }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.etag": "\"0404d9d2-0000-0700-0000-65412d480000\"",
    "id": "NOTE_f87ade4c-1107-47b6-b977-0f31c065b209",
    "dayNoteDate": "2023-10-08",
    "sharedDayNote": {
        "contentType": "text",
        "content": "shared note 08"
    },
    "draftDayNote": null
}
```
