<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# granularRestoreArtifactBase resource type

Namespace: microsoft.graph

An abstract type that represents granular restore artifacts associated with a restore session.

Base type for [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) and [granularSiteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granularsiterestoreartifact?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| browseSessionId | String | The unique identifier of the [browseSession](https://learn.microsoft.com/en-us/graph/api/resources/browsesessionbase?view=graph-rest-1.0) |
| completionDateTime | DateTimeOffset | Date time when the artifact's restoration completes. |
| id | String | The unique identifier for the artifact. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| restoredItemKey | String | The unique identifier for the restored artifact. |
| restoredItemPath | String | The path of the restored artifact. It's the path of the folder where all the artifacts are restored within a granular restore session. |
| restoredItemWebUrl | String | The web url of the restored artifact. |
| restorePointDateTime | DateTimeOffset | The restore point date time to which the artifact is restored. |
| startDateTime | DateTimeOffset | The start time of the restoration. |
| status | artifactRestoreStatus | Status of the artifact restoration. The possible values are: `added`, `scheduling`, `scheduled`, `inProgress`, `succeeded`, `failed`, `unknownFutureValue`. |
| webUrl | String | The original web url of the artifact being restored. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.granularRestoreArtifactBase",
  "id": "String (identifier)",
  "browseSessionId": "String",
  "status": "String",
  "webUrl": "String",
  "restoredItemKey": "String",
  "restoredItemPath": "String",
  "restoredItemWebUrl": "String",
  "restorePointDateTime": "String (timestamp)",
  "startDateTime": "String (timestamp)",
  "completionDateTime": "String (timestamp)"
}
```
