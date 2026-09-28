<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# restoreSessionBase resource type

Namespace: microsoft.graph

Represents a restore session for a [protection unit](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) that's protected by a [protection policy](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0). Restore session APIs are used by global admins, SharePoint Online admins, and Exchange Online admins to perform restore-related tasks on artifacts that are protected as part of protection policy.

Restoring to both a new location and the same URL in a single restore session is not supported.

Note

Restore sessions that are older than one year and in a terminal state are removed.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-restoresessions?view=graph-rest-1.0) | [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) collection | Get a list of [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/restoresessionbase-get?view=graph-rest-1.0) | [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) | Read the properties and relationships of a [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/restoresessionbase-delete?view=graph-rest-1.0) | None | Delete a [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) object. |
| [Activate](https://learn.microsoft.com/en-us/graph/api/restoresessionbase-activate?view=graph-rest-1.0) | [restoreSessionBase](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0) | Activate a draft restore session. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the restore session. |
| completedDateTime | DateTimeOffset | The time of completion of the restore session. |
| createdBy | identitySet | The identity of person who created the restore session. |
| createdDateTime | DateTimeOffset | The time of creation of the restore session. |
| error | publicError | Contains error details if the restore session fails or completes with an error. |
| lastModifiedBy | identitySet | Identity of the person who last modified the restore session. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of the last modification of the restore session. |
| restoreJobType | [restoreJobType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#restorejobtype-values) | Indicates whether the restore session was created normally or by a bulk job. |
| restoreSessionArtifactCount | [restoreSessionArtifactCount](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionartifactcount?view=graph-rest-1.0) | The number of metadata artifacts that belong to this restore session. |
| status | [restoreSessionStatus](https://learn.microsoft.com/en-us/graph/api/resources/restoresessionbase?view=graph-rest-1.0#restoresessionstatus-values) | Status of the restore session. The value is an aggregated status of the restored artifacts. The possible values are: `draft`, `activating`, `active`, `completedWithError`, `completed`, `unknownFutureValue`, `failed`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `failed`. |

### restoreSessionStatus values

| Member | Description |
| :--- | :--- |
| draft | All artifacts are added. |
| activating | All artifacts are scheduled. |
| active | All or any restore artifacts are scheduled or in progress. |
| completedWithError | Some artifacts failed to restore, and some succeeded. |
| completed | All restore artifacts successfully restored. |
| failed | All restore artifacts failed to restore. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restoreSessionBase",
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
