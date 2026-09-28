<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-11 -->

# oneDriveForBusinessRestoreSession resource type

Namespace: microsoft.graph

Represents restore-related tasks on artifacts that are protected by a [OneDrive protection policy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0). Restore session APIs are used by SharePoint Admins to perform restore-related tasks on artifacts that are protected as part of a OneDrive protection policy.

Inherits from [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-onedriveforbusinessrestoresessions?view=graph-rest-1.0) | [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) | Create a new [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0). |
| [List](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-list-driverestoreartifacts?view=graph-rest-1.0) | [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) collection | Get a list of the [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) objects and their properties. |
| [List granularDriveRestoreArtifacts](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-list-granulardriverestoreartifacts?view=graph-rest-1.0) | [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) collection | Get a list of the [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) objects and their properties. |
| [Update](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-update?view=graph-rest-1.0) | [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0) | Update the properties of a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the restore session created. |
| completedDateTime | DateTimeOffset | The time of creation of the restore session. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who created the restore session. |
| createdDateTime | DateTimeOffset | The time of completion of the restore session. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if the restore session fails or completes with an error. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified this restore session. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of the last modification of this restore session. |
| status | [restoreSessionStatus](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0#restoresessionstatus-values) | Status of the restore session. The value is an aggregated status of the restored artifacts. The possible values are: `draft`, `activating`, `active`, `completedWithError`, `completed`, `unknownFutureValue`, `failed`. You must use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `failed`. |
| restoreJobType | [restoreJobType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#restorejobtype-values) | Indicates whether the restore session was created normally or by a bulk job. |
| restoreSessionArtifactCount | [restoreSessionArtifactCount](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionartifactcount?view=graph-rest-1.0) | The number of metadata artifacts that belong to this restore session. |

### restoreSessionStatus values

| Member | Description |
| :--- | :--- |
| draft | All artifacts are added. |
| activating | All artifacts are scheduled. |
| active | All or any restore artifacts are scheduled or in progress. |
| completedWithError | Some artifacts failed to restore, and some succeeded. |
| completed | All restore artifacts successfully restored. |
| failed | All restore artifacts failed to restore. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| driveRestoreArtifacts | [driveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifact?view=graph-rest-1.0) collection | A collection of restore points and destination details that can be used to restore a OneDrive for work or school drive. |
| driveRestoreArtifactsBulkAdditionRequests | [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) collection | A collection of user mailboxes and destination details that can be used to restore a OneDrive for work or school drive. |
| granularDriveRestoreArtifacts | [granularDriveRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/granulardriverestoreartifact?view=graph-rest-1.0) collection | A collection of browse session ID and item key details that can be used to restore OneDrive for work or school files and folders. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oneDriveForBusinessRestoreSession",
  "id": "String (identifier)",
  "status": "String",
  "restoreJobType": "String",
  "restoreSessionArtifactCount": {
    "@odata.type": "microsoft.graph.restoreSessionArtifactCount"
  },
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "completedDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  }
}
```
