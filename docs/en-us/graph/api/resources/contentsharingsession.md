<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentsharingsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# contentSharingSession resource type

Namespace: microsoft.graph

Represents a content sharing session in a call.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get contentSharingSession](https://learn.microsoft.com/en-us/graph/api/contentsharingsession-get?view=graph-rest-1.0) | [contentSharingSession](https://learn.microsoft.com/en-us/graph/api/resources/contentsharingsession?view=graph-rest-1.0) | Retrieve the properties of a **contentSharingSession** object in a call. |
| [List contentSharingSessions](https://learn.microsoft.com/en-us/graph/api/call-list-contentsharingsessions?view=graph-rest-1.0) | [contentSharingSession](https://learn.microsoft.com/en-us/graph/api/resources/contentsharingsession?view=graph-rest-1.0) collection | Retrieve a list of **contentSharingSession** objects in a call. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the content sharing session. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentSharingSession",
  "id": "String (identifier)"
}
```
