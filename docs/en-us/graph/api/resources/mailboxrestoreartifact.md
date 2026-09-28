<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# mailboxRestoreArtifact resource type

Namespace: microsoft.graph

Represents the restore point and destination details that can be used to restore a [mailbox protection unit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-1.0).

Inherits from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/exchangerestoresession-list-mailboxrestoreartifacts?view=graph-rest-1.0) | [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) collection | Get a list of the [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the restore artifact. |
| completionDateTime | DateTimeOffset | The time when the restoration of the artifact is completed. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). |
| destinationType | [destinationType](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0#destinationtype-values) | Indicates the restoration destination. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). The possible values are: `new`, `inPlace`, `unknownFutureValue`. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if the restoration of the artifact fails. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). |
| restoredFolderId | String | The new restored folder identifier for the user. |
| restoredFolderName | String | The new restored folder name. |
| restoredItemCount | Int32 | The number of items that are being restored in the folder. |
| startDateTime | DateTimeOffset | The time when the restoration of the artifact started. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). |
| status | [artifactRestoreStatus](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0#artifactrestorestatus-values) | The restoration status of the artifact. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0). The possible values are: `added`, `scheduling`, `scheduled`, `inProgress`, `succeeded`, `failed`, `unknownFutureValue`. |

### artifactRestoreStatus values

| Member | Description |
| :--- | :--- |
| added | The restore artifact was added to the restore session. |
| scheduling | The activate action was called on the restore session. |
| scheduled | The activate action call was successful on the restore session. |
| inProgress | The restore artifact was picked for restoration. |
| succeeded | The restore artifact was successfully restored. |
| failed | The restoration of the artifact failed. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### destinationType values

| Member | Description |
| :--- | :--- |
| new | Restoration occurs at a new location. For SharePoint and OneDrive, a new site is created, and content is restored in the new site. For Exchange, a restored folder is created, and the content is restored there. |
| inPlace | Restoration occurs in the same location. For SharePoint, it's on the same site, for OneDrive, on the same drive, and for Exchange, the artifact is restored in the same mailbox. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| restorePoint | [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) | Represents the date and time when an artifact is protected by a protection policy and can be restored. Inherited from [restoreArtifactBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mailboxRestoreArtifact",
  "id": "String (identifier)",
  "destinationType": "String",
  "status": "String",
  "startDateTime": "String (timestamp)",
  "completionDateTime": "String (timestamp)",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "restoredFolderId": "String",
  "restoredFolderName": "String",
  "restoredItemCount": "Int32"
}
```
