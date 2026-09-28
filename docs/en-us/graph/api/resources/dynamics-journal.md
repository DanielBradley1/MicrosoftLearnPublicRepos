<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-journal?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# journal resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a journal in Dynamics 365 Business Central.

Note

The journal resource type offers a bound action called `post` that posts the corresponding general journal batch.

> Posting the general journal batch is illustrated in the following example:  
> `POST https://graph.microsoft.com/beta/financials/companies{id}/journals{id}/post`.
> 
> The response has no content; the response code is 204.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get journal](https://learn.microsoft.com/en-us/graph/api/dynamics-journal-get?view=graph-rest-beta) | journal | Gets a journal. |
| [Create journal](https://learn.microsoft.com/en-us/graph/api/dynamics-create-journal?view=graph-rest-beta) | journal | Creates a journal. |
| [Update journal](https://learn.microsoft.com/en-us/graph/api/dynamics-journal-update?view=graph-rest-beta) | journal | Updates a journal. |
| [Delete journal](https://learn.microsoft.com/en-us/graph/api/dynamics-journal-delete?view=graph-rest-beta) | none | Deletes a journal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the journal. Non-editable. |
| code | string, maximum size 10 | The code of the journal. |
| displayName | string, maximum size 50 | The display name of the journal. |
| lastModifiedDateTime | datetime | The last datetime the journal was modified. Read-Only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "GUID",
  "code": "string",
  "displayName": "string",
  "lastModifiedDateTime": "datetime"
}
```
