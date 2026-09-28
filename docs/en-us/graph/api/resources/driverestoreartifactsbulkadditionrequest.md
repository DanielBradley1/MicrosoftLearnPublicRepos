<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-23 -->

# driveRestoreArtifactsBulkAdditionRequest resource type

Namespace: microsoft.graph

Represents the properties of a **driveRestoreArtifactsBulkAdditionRequest** associated with a [OneDrive for work or school restore session](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0). It contains a list of drives that are added to the corresponding OneDrive for work or school restore session in a bulk operation.

Inherits from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-list-driverestoreartifactsbulkadditionrequests?view=graph-rest-1.0) | [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) collection | Get a list of the [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) objects associated with a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessrestoresession-post-driverestoreartifactsbulkadditionrequests?view=graph-rest-1.0) | [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) | Create a [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object associated with a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/driverestoreartifactsbulkadditionrequest-get?view=graph-rest-1.0) | [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) | Get a [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object by its **id**, associated with a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/driverestoreartifactsbulkadditionrequest-delete?view=graph-rest-1.0) | None | Delete a [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object associated with a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who created the bulk request. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The time when the bulk request was created. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| destinationType | destinationType | Indicates the restoration destination. The possible values are: `new`, `inPlace`, `unknownFutureValue`. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| directoryObjectIds | String collection | The list of directory object IDs that are added to the corresponding OneDrive for work or school restore session in a bulk operation. |
| displayName | String | Name of the addition request. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| drives | String collection | The list of email addresses that are added to the corresponding OneDrive for work or school restore session in a bulk operation. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Error details are populated for resource resolution failures. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| id | String | The unique identifier of the bulk request associated with the restore session. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified this entity. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | Timestamp when this entity was last modified. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| protectionTimePeriod | [timePeriod](https://learn.microsoft.com/en-us/graph/api/resources/timeperiod?view=graph-rest-1.0) | The start and end date time of the protection period. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| protectionUnitIds | String collection | Indicates which protection units to restore. This property isn't implemented yet. Future value; don't use. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| restorePointPreference | restorePointPreference | Indicates which restore point to return. The possible values are: `oldest`, `latest`, `unknownFutureValue`. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| status | [restoreArtifactsBulkRequestStatus](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0#restoreartifactsbulkrequeststatus-values) | The status of the long-running operation. The possible values are: `unknown`, `active`, `completed`, `completedWithErrors`, `unknownFutureValue`. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |
| tags | restorePointTags | The type of the restore point. The possible values are: `none`, `fastRestore`, `unknownFutureValue`. Inherited from [restoreArtifactsBulkRequestBase](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactsbulkrequestbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driveRestoreArtifactsBulkAdditionRequest",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "destinationType": "String",
  "directoryObjectIds": ["String"],
  "displayName": "String",
  "drives": ["String"],
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
