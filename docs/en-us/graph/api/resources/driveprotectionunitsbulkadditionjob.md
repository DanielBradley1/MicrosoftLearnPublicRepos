<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunitsbulkadditionjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-17 -->

# driveProtectionUnitsBulkAdditionJob resource type

Namespace: microsoft.graph

Represents the properties of a **driveProtectionUnitsBulkAdditionJob** associated with a [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0). It contains a list of email addresses, drives, and, directory object IDs to be added to the OneDrive protection policy for backup.

Inherits from [protectionUnitsBulkJobBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitsbulkjobbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessprotectionpolicy-list-driveprotectionunitsbulkadditionjobs?view=graph-rest-1.0) | [driveProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunitsbulkadditionjob?view=graph-rest-1.0) collection | Get a list of [driveProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunitsbulkadditionjob?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/driveprotectionunitsbulkadditionjobs-post?view=graph-rest-1.0) | [driveProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunitsbulkadditionjob?view=graph-rest-1.0) | Create a new [driveProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunitsbulkadditionjob?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/driveprotectionunitsbulkadditionjobs-get?view=graph-rest-1.0) | [driveProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunitsbulkadditionjob?view=graph-rest-1.0) | Read the properties and relationships of a [driveProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunitsbulkadditionjob?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who created the job. |
| createdDateTime | DateTimeOffset | The date and time that the job was created. |
| directoryObjectIds | String collection | The list of OneDrive **directoryObjectIds** to add to the OneDrive protection policy. |
| displayName | String | The name of the job. |
| drives | String collection | The list of email addresses to add to the OneDrive protection policy. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if any email address resolution fails. |
| id | String | The unique identifier of the job associated with the OneDrive protection policy. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified the job. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of the last modification to the job. |
| status | [protectionUnitsBulkJobStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitsbulkjobbase?view=graph-rest-1.0#protectionunitsbulkjobstatus-values) | Status of the job. The possible values are: `unknown`, `active`, `completed`, `completedWithErrors`, and `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driveProtectionUnitsBulkAdditionJob",
  "id": "String (identifier)",
  "displayName": "String",
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "drives": [
    "String"
   ],
  "directoryObjectIds": [
    "String"
   ]
}
```
