<!-- Source: https://learn.microsoft.com/en-us/graph/api/daynote-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# Update dayNote

Namespace: microsoft.graph

Update the properties of a [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

## HTTP request

```http
PUT /teams/{teamsId}/schedule/dayNotes/{dayNoteId}
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
| dayNoteDate | Date | The date for the day note. |
| sharedDayNote | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The draft version of this **dayNote** that is viewable by managers. |
| draftDayNote | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The shared version of this **dayNote** that is viewable by both employees and managers. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
PUT /teams/d72f9b8e-4c76-4f50-bf93-51b17aab0cd9/schedule/dayNotes/NOTE_ff2194ab-0ae5-43e3-acb4-ec2654927213
Content-Type: application/json

{
  "dayNoteDate": "2025-01-09",
  "sharedDayNote": null,
  "draftDayNote": {
    "contentType": "text",
    "content": "Produce shipment arriving at 2 PM"
  }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
