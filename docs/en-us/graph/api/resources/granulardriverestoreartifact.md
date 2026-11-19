<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-10 -->

# granularDriveRestoreArtifact resource type

Namespace: microsoft.graph

Represents the granular artifact of the OneDrive that is present within a backed-up drive and can be restored.

Inherits from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-list-granulardriverestoreartifacts?view=graph-rest-1.0) | [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) collection | Get a list of the granularDriveRestoreArtifact objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| browseSessionId | String | The unique identifier of the [browseSession](https://learn.microsoft.com/en-us/graph/api/resources/browsesessionbase?view=graph-rest-1.0). Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| completionDateTime | DateTimeOffset | Date time when the artifact's restoration completes. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| destinationType | [destinationType](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0#destinationtype-values) | The restoration destination. The possible values are: `new`, `inPlace`, `unknownFutureValue`. Nullable. Use `inPlace` to restore to the original location. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| directoryObjectId | String | Id of the drive in which artifact is present. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if the restoration fails or completes with an error. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| id | String | The unique identifier for the artifact. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| restoredItemKey | String | The unique identifier for the restored artifact. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| restoredItemPath | String | The path of the restored artifact. It's the path of the folder where all the artifacts are restored within a granular restore session. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| restoredItemWebUrl | String | The web url of the restored artifact. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| restorePointDateTime | DateTimeOffset | The restore point date time to which the artifact is restored. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| startDateTime | DateTimeOffset | The start time of the restoration. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| status | artifactRestoreStatus | Status of the artifact restoration. The possible values are: `added`, `scheduling`, `scheduled`, `inProgress`, `succeeded`, `failed`, `unknownFutureValue`. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |
| webUrl | String | The original web url of the artifact being restored. Inherited from [granularRestoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreartifactbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.granularDriveRestoreArtifact",
  "id": "String (identifier)",
  "browseSessionId": "String",
  "status": "String",
  "webUrl": "String",
  "restoredItemKey": "String",
  "restoredItemPath": "String",
  "restoredItemWebUrl": "String",
  "restorePointDateTime": "String (timestamp)",
  "startDateTime": "String (timestamp)",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "completionDateTime": "String (timestamp)",
  "destinationType": "String",
  "directoryObjectId": "String"
}
```
