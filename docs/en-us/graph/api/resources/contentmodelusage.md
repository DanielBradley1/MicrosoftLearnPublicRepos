<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentmodelusage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-12 -->

# contentModelUsage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains information about where, by whom, and when a [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) is applied, including information about the model itself, such as the model version.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user, device, or application that first applied the [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) to the library. |
| createdDateTime | DateTimeOffset | Date and time of the [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) is first applied. |
| driveId | String | The ID of the drive where the [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) is applied. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user, device, or application that last applied the [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) to the library. |
| lastModifiedDateTime | DateTimeOffset | Date and time of the [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta) is last applied. |
| modelId | String | The ID of the [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta). |
| modelVersion | String | The version of the current applied [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentModelUsage",
  "modelId": "String",
  "driveId": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "modelVersion": "String"
}
```
