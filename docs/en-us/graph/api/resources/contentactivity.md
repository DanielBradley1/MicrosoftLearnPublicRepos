<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentactivity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# contentActivity resource type

Namespace: microsoft.graph

Represents audit data from content processing for Microsoft Purview to ensure compliance, track user actions, and detect unusual behavior.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/activitiescontainer-post-contentactivities?view=graph-rest-1.0) | [contentActivity](https://learn.microsoft.com/en-us/graph/api/resources/contentactivity?view=graph-rest-1.0) | Create a new contentActivity object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentMetadata | [processContentRequest](https://learn.microsoft.com/en-us/graph/api/resources/processcontentrequest?view=graph-rest-1.0) | Defines the input payload. It includes the relevant metadata about the activity, device, and integrated application. |
| id | String | Unique identifier. |
| scopeIdentifier | String | The scope identified from computed protection scopes. |
| userId | String | ID of the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentActivity",
  "id": "String (identifier)",
  "userId": "String",
  "scopeIdentifier": "String",
  "contentMetadata": {
    "@odata.type": "microsoft.graph.processContentRequest"
  }
}
```
