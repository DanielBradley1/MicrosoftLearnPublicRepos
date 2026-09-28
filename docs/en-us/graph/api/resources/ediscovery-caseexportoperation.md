<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseexportoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# caseExportOperation resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents the process of an eDiscovery export. The **caseExportOperation** can only be retrieved from the `Location` header in the response to a [reviewset export](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewset-export?view=graph-rest-beta).

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [getDownloadUrl](https://learn.microsoft.com/en-us/graph/api/ediscovery-caseexportoperation-getdownloadurl?view=graph-rest-beta) | String | Returns the URL for the export. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.ediscovery.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseaction-values) | The case action for this entity will always be `contentExport`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| azureBlobContainer | String | The name of the Azure storage location where the export will be stored. This only applies to exports stored in your own Azure storage location. |
| azureBlobToken | String | The SAS token for the Azure storage location. This only applies to exports stored in your own Azure storage location. |
| completedDateTime | DateTimeOffset | The date and time the export was completed. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who initiated the export operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time the export was created. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| description | String | The description provided for the export. |
| exportOptions | microsoft.graph.ediscovery.exportOptions | The options provided for the export. For more information, see [reviewSet: export](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewset-export?view=graph-rest-beta). The possible values are: `originalFiles`, `text`, `pdfReplacement`, `fileInfo`, `tags`. |
| exportStructure | microsoft.graph.ediscovery.exportFileStructure | The options provided specify the structure of the export. For more information, see [reviewSet: export](https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewset-export?view=graph-rest-beta). The possible values are: `none`, `directory`, `pst`. |
| id | String | The ID for the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| outputFolderId | String | The output folder ID. |
| outputName | String | The name provided for the export. |
| percentProgress | Int32 | The progress of the operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-beta) | Contains success and failure-specific result information. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| status | [microsoft.graph.ediscovery.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseoperationstatus-values) | The status of the case operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`. |

### exportOptions values

| Member | Description |
| :--- | :--- |
| originalFiles | Include copies of the original files - exclude this option when generating reports only. |
| text | Include raw extracted text files for each document. |
| pdfReplacement | If redacted PDF files are generated during review, these files are available for export. You can choose to export the redacted PDFs instead of the original native files by including this option. |
| fileInfo | Include the summary and load file - this should always be included. |
| tags | Include document tags that were applied during review in the load file. |

### exportFileStructure values

| Member | Description |
| :--- | :--- |
| directory | Maps to the condensed directory structure commonly used by eDiscovery tools. All files are exported to a root file called NativeFiles. |
| pst | Emails are stored in PSTs while documents from sites are stored in folders that represent the original native folder structure. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| reviewSet | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) | The review set the content is being exported from. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.caseExportOperation",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "completedDateTime": "String (timestamp)",
  "percentProgress": "Integer",
  "status": "String",
  "action": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "resultInfo": {
    "@odata.type": "microsoft.graph.resultInfo"
  },
  "outputName": "String",
  "description": "String",
  "outputFolderId": "String",
  "azureBlobContainer": "String",
  "azureBlobToken": "String",
  "exportOptions": "String",
  "exportStructure": "String"
}
```
