<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# exchangeRestoreSession resource type

Namespace: microsoft.graph

Represents restore-related tasks on artifacts that are protected by an [Exchange protection policy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0). Restore session APIs are used by Exchange Online Admins to perform restore-related tasks on artifacts that are protected as part of a mailbox protection policy.

Inherits from [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-exchangerestoresessions?view=graph-rest-1.0) | [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) | Create a new [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0). |
| [List](https://learn.microsoft.com/en-us/graph/api/exchangerestoresession-list-mailboxrestoreartifacts?view=graph-rest-1.0) | [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) collection | Get a list of the [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) objects and their properties. |
| [Update](https://learn.microsoft.com/en-us/graph/api/exchangerestoresession-update?view=graph-rest-1.0) | [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) | Update the properties of an [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the restore session created. |
| completedDateTime | DateTimeOffset | The time of creation of the restore session. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who created the restore session. |
| createdDateTime | DateTimeOffset | The time of completion of the restore session. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if the restore session fails or completes with an error. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified this restore session. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of last modification of this restore session. |
| restoreJobType | [restoreJobType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#restorejobtype-values) | Indicates whether the restore session was created normally or by a bulk job. |
| restoreSessionArtifactCount | [restoreSessionArtifactCount](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionartifactcount?view=graph-rest-1.0) | The number of metadata artifacts that belong to this restore session. |
| status | [restoreSessionStatus](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0#restoresessionstatus-values) | Status of the restore session. The value is an aggregated status of the restored artifacts. The possible values are: `draft`, `activating`, `active`, `completedWithError`, `completed`, `unknownFutureValue`, `failed`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `failed`. |

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
| mailboxRestoreArtifacts | [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) collection | A collection of restore points and destination details that can be used to restore Exchange mailboxes. |
| mailboxRestoreArtifactsBulkAdditionRequests | [mailboxRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifactsbulkadditionrequest?view=graph-rest-1.0) collection | A collection of user mailboxes and destination details that can be used to restore Exchange mailboxes. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exchangeRestoreSession",
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
