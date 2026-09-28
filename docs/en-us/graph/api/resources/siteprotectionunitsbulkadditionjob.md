<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-17 -->

# siteProtectionUnitsBulkAdditionJob resource type

Namespace: microsoft.graph

Represents the properties of a **siteProtectionUnitsBulkAdditionJob** associated with a [SharePoint protection policy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0). It contains a list of SharePoint site URLs, and a list of site IDs to be added to the SharePoint protection policy for backup.

Inherits from [protectionUnitsBulkJobBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitsbulkjobbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/sharepointprotectionpolicy-list-siteprotectionunitsbulkadditionjobs?view=graph-rest-1.0) | [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) collection | Get a list of [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/siteprotectionunitsbulkadditionjobs-post?view=graph-rest-1.0) | [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) | Create a new [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/siteprotectionunitsbulkadditionjobs-get?view=graph-rest-1.0) | [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0) | Read the properties and relationships of a [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who created the job. |
| createdDateTime | DateTimeOffset | The date and time that the job was created. |
| displayName | String | The name of the job. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if any site-url resolution fails. |
| id | String | The unique identifier of the job associated with the SharePoint protection policy. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified the job. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of the last modification to the job. |
| status | [protectionUnitsBulkJobStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitsbulkjobbase?view=graph-rest-1.0#protectionunitsbulkjobstatus-values) | Status of the job. The possible values are: `unknown`, `active`, `completed`, `completedWithErrors`, and `unknownFutureValue`. |
| siteWebUrls | String collection | The list of SharePoint site URLs to add to the SharePoint protection policy. |
| siteIds | String collection | The list of SharePoint site IDs to add to the SharePoint protection policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.siteProtectionUnitsBulkAdditionJob",
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
  "siteWebUrls": [
    "String"
   ],
  "siteIds": [
    "String"
   ]
}
```
