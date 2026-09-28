<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-23 -->

# restoreArtifactsBulkRequestBase resource type

Namespace: microsoft.graph

An abstract type that represents a bulk request associated with one of the restore sessions.

Base type for [siteRestoreArtifactsBulkAdditionRequests](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifactsbulkadditionrequest?view=graph-rest-1.0), [mailboxRestoreArtifactsBulkAdditionRequests](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifactsbulkadditionrequest?view=graph-rest-1.0), and [driveRestoreArtifactsBulkAdditionRequests](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0).

The following points apply to bulk addition requests for restoring artifacts:

- Currently, only one bulk addition job can be processed per restore session.
- The limit for the number of sites or users in a bulk request is 10,000.
- Patch operations aren't supported for bulk restore sessions.
- In a single restore session, you can't add restore artifacts using both manual and bulk addition methods simultaneously.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who created the bulk request. |
| createdDateTime | DateTimeOffset | The time when the bulk request was created. |
| destinationType | destinationType | Indicates the restoration destination. The possible values are: `new`, `inPlace`, `unknownFutureValue`. |
| displayName | String | Name of the addition request. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Error details are populated for resource resolution failures. |
| id | String | The unique identifier of the bulk request associated with the restore session. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified this entity. |
| lastModifiedDateTime | DateTimeOffset | Timestamp when this entity was last modified. |
| protectionTimePeriod | [timePeriod](https://learn.microsoft.com/en-us/graph/api/resources/timeperiod?view=graph-rest-1.0) | The start and end date and time of the protection period. |
| protectionUnitIds | String collection | Indicates which protection units to restore. This property isn't implemented yet. Future value; don't use. |
| restorePointPreference | restorePointPreference | Indicates which restore point to return. The possible values are: `oldest`, `latest`, `unknownFutureValue`. |
| status | [restoreArtifactsBulkRequestStatus](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0#restoreartifactsbulkrequeststatus-values) | Determines the status of the long-running operation. The possible values area: `unknown`, `active`, `completed`, `completedWithErrors`, `unknownFutureValue`. |
| tags | restorePointTags | The type of the restore point. The possible values are: `none`, `fastRestore`, `unknownFutureValue`. |

### restoreArtifactsBulkRequestStatus values

| Member | Description |
| :--- | :--- |
| unknown | The restore session is in an indeterminate state, possibly due to a temporary system issue or error. |
| active | The initial status upon creation of the entity is `active`. |
| completed | When all protection resources are added to the corresponding restore session, the status of the entity becomes `completed`. The state transition is from `active` to `completed`. |
| completedWithErrors | If any failures are encountered during resource resolution, the status of the entity becomes `completedWithErrors`. The state transition is from `active` to `completedWithErrors`. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restoreArtifactsBulkRequestBase",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "destinationType": "String",
  "displayName": "String",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "protectionTimePeriod": {"@odata.type": "microsoft.graph.timePeriod"},
  "protectionUnitIds": ["String"],
  "restorePointPreference": "String",
  "status": "String",
  "tags": "String"
}
```
