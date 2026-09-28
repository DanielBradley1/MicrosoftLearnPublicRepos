<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-21 -->

# restoreArtifactBase resource type

Namespace: microsoft.graph

Represents the restore point and destination details that can be used to restore a site, drive, or mailbox [protection unit](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0).

Note

Restore artifacts that are older than one year and in a terminal state are removed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the restore artifact. |
| completionDateTime | DateTimeOffset | The time when restoration of restore artifact is completed. |
| destinationType | destinationType | Indicates the restoration destination. The possible values are: `new`, `inPlace`, `unknownFutureValue`. |
| error | publicError | Contains error details if the restore session fails or completes with an error. |
| startDateTime | DateTimeOffset | The time when restoration of restore artifact is started. |
| status | artifactRestoreStatus | The individual restoration status of the restore artifact. The possible values are: `added`, `scheduling`, `scheduled`, `inProgress`, `succeeded`, `failed`, `unknownFutureValue`. |

### artifactRestoreStatus values

| Member | Description |
| :--- | :--- |
| added | The restore artifact was added to the restore session. |
| scheduling | The activate action was called on the restore session. |
| scheduled | The activate action call was successful on the restore session. |
| inProgress | The restore artifact was picked for restoration. |
| succeeded | The restore artifact was successfully restored. |
| failed | The restoration of the artifact failed. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| restorePoint | [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) | Represents the date and time when an [artifact](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0) is protected by a [protectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) and can be restored. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restoreArtifactBase",
  "id": "String (identifier)",
  "destinationType": "String",
  "status": "String",
  "startDateTime": "String (timestamp)",
  "completionDateTime": "String (timestamp)",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  }
}
```
