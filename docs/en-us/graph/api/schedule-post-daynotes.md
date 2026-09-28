<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-post-daynotes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# Create dayNote

Namespace: microsoft.graph

Create a new [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object.

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
| sharedDayNote | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The draft version of this **dayNote** that is viewable by managers. |
| draftDayNote | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The shared version of this **dayNote** that is viewable by both employees and managers. |

## Response

If successful, this method returns a `200 OK` response code and a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST /teams/d72f9b8e-4c76-4f50-bf93-51b17aab0cd9/schedule/dayNotes
Content-Type: application/json

{
  "dayNoteDate": "2025-01-09",
  "sharedDayNote": null,
  "draftDayNote": {
    "contentType": "text",
    "content": "Produce shipment arriving at 11 AM"
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
  "id": "NOTE_ff2194ab-0ae5-43e3-acb4-ec2654927213",
  "dayNoteDate": "2025-01-09",
  "sharedDayNote": null,
  "draftDayNote": {
    "contentType": "text",
    "content": "Produce shipment arriving at 11 AM"
  }
}
```
