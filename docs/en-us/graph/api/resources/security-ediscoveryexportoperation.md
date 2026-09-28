<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryexportoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# ediscoveryExportOperation resource type

Namespace: microsoft.graph.security

Represents the process of a Microsoft Purview eDiscovery export.

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get case operation by ID](https://learn.microsoft.com/en-us/graph/api/security-caseoperation-get?view=graph-rest-1.0) | Resource | The **exportFileMetadata** property returned by the method provides downloadUrl, fileName and size of exported content |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.security.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseaction-values) | The type of action the operation represents. The possible values are: `contentExport`, `applyTags`, `convertToPdf`, `index`, `estimateStatistics`, `addToReviewSet`, `holdUpdate`, `unknownFutureValue`, `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| completedDateTime | DateTimeOffset | The date and time the export was completed. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who initiated the export operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the export was created. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| description | String | The description provided for the export. |
| exportFileMetadata | [microsoft.graph.security.ediscoveryExportFileMetadata](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryexportfilemetadata?view=graph-rest-1.0) | Contains the properties for an export file metadata, including **downloadUrl**, **fileName**, and **size**. |
| exportOptions | [microsoft.graph.security.exportOptions](#exportoptions-values) | The options provided for the export. For more information, see [reviewSet: export](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-export?view=graph-rest-1.0). The possible values are: `originalFiles`, `text`, `pdfReplacement`, `tags`, `unknownFutureValue`, `splitSource`, `includeFolderAndPath`, `friendlyName`, `condensePaths`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `splitSource`, `includeFolderAndPath`, `friendlyName`, `condensePaths`. |
| exportStructure | [microsoft.graph.security.exportFileStructure](#exportfilestructure-values) | The options that specify the structure of the export. For more information, see [reviewSet: export](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-export?view=graph-rest-1.0). The possible values are: `none`, `directory` \(deprecated\), `pst`, `unknownFutureValue`, `msg`. Use the `Prefer: include-unknown-enum-members` request header to get the following members from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `msg`. The `directory` member is deprecated. It remains in v1.0 for backward compatibility. Going forward, use either `pst` or `msg`. |
| id | String | The ID for the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| outputName | String | The name provided for the export. |
| percentProgress | Int32 | The progress of the operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | Contains success and failure-specific result information. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| status | [microsoft.graph.security.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseoperationstatus-values) | The status of the case operation. The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`, `unknownFutureValue`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |

### exportOptions values

| Member | Description |
| :--- | --- |
| originalFiles | Include original files in native format; for example: docx, xlsx, pptx, doc, xlst, and pptm. |
| text | Include extracted text from the original files. |
| pdfReplacement | Replace original file with PDF version when available. |
| tags | Include tag information. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| splitSource | Organize data from different locations into separate folders or PSTs. |
| includeFolderAndPath | Include folder and path structure of source. |
| friendlyName | Give each item a friendly name. |
| condensePaths | Condense paths to fit within 259 characters. |

### exportFileStructure values

| Member | Description |
| :--- | --- |
| None | Default file structure. |
| directory \(deprecated\) | All files in a single folder called Native files. |
| pst | Mails are grouped in .pst format. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| msg | Mails are in .msg format. |

Tip

The `directory` member is deprecated. It remains in v1.0 for backward compatibility. Going forward, use either `pst` or `msg`.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| reviewSet | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) | Review set from where documents are exported. |
| reviewSetQuery | [microsoft.graph.security.ediscoveryReviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewsetquery?view=graph-rest-1.0) | The review set query that is used to filter the documents for export. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryExportOperation",
  "action": "String",
  "completedDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "exportFileMetadata": {
    "@odata.type": "microsoft.graph.security.ediscoveryExportFileMetadata"
  },
  "exportOptions": "String",
  "exportStructure": "String",
  "id": "String (identifier)",
  "outputName": "String",
  "percentProgress": "Int32",
  "resultInfo": {
    "@odata.type": "microsoft.graph.resultInfo"
  },
  "status": "String"
}
```
