<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# driveRestoreArtifact resource type

Namespace: microsoft.graph

Represents the restore point and destination details that can be used to restore a [drive protection unit](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunit?view=graph-rest-1.0).

Inherits from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-list-driverestoreartifacts?view=graph-rest-1.0) | [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) collection | Get a list of the [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the restore artifact. |
| completionDateTime | DateTimeOffset | The time when restoration of restore artifact is completed. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). |
| destinationType | [destinationType](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0#destinationtype-values) | The restoration destination. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). The possible values are: `new`, `inPlace`, `unknownFutureValue`. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if the restoration fails. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). |
| restoredSiteId | String | The new site identifier if **destinationType** is `new`, and the input site ID if the **destinationType** is `inPlace`. |
| restoredSiteName | String | The name of the restored site. |
| restoredSiteWebUrl | String | The web URL of the restored site. |
| startDateTime | DateTimeOffset | The time when the restoration started. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). |
| status | [artifactRestoreStatus](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0#artifactrestorestatus-values) | The individual restoration status of the restore artifact. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). The possible values are: `added`, `scheduling`, `scheduled`, `inProgress`, `succeeded`, `failed`, `unknownFutureValue`. |

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

### destinationType values

| Member | Description |
| :--- | :--- |
| new | Restoration will occur at a new location. For SharePoint and OneDrive, a new site will be created and content will be restored in the new site. For Exchange, a restored folder is created and content will be restored there. |
| inPlace | Restoration will occur in the same location. For SharePoint, it will be on the same site, for OneDrive, on the same drive, and for Exchange, the artifact will be restored in the same mailbox. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| restorePoint | [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) | Restore artifact refers to the onedrive unit's restore point and destination relevant details that can be used to restore it. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driveRestoreArtifact",
  "id": "String (identifier)",
  "destinationType": "String",
  "status": "String",
  "startDateTime": "String (timestamp)",
  "completionDateTime": "String (timestamp)",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "restoredSiteId": "String",
  "restoredSiteName": "String",
  "restoredSiteWebUrl": "String"
}
```
