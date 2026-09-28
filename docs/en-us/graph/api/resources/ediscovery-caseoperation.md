<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# caseOperation resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

An abstract entity that represents a long-running eDiscovery process. It contains a common set of properties that are shared among inheriting entities. Entities that derive from **caseOperation** include:

- [caseExportOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseexportoperation?view=graph-rest-beta)
- [tagOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tagoperation?view=graph-rest-beta)
- [estimateStatisticsOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-estimatestatisticsoperation?view=graph-rest-beta)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.ediscovery.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseaction-values) | The type of action the operation represents. The possible values are: `addToReviewSet`,`applyTags`,`contentExport`,`convertToPdf`,`estimateStatistics`, `purgeData` |
| completedDateTime | DateTimeOffset | The date and time the operation was completed. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user that created the operation. |
| createdDateTime | DateTimeOffset | The date and time the operation was created. |
| id | String | The ID for the operation. Read-only. |
| percentProgress | Int32 | The progress of the operation. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-beta) | Contains success and failure-specific result information. |
| status | [microsoft.graph.ediscovery.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseoperationstatus-values) | The status of the case operation. The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`. |

### caseAction values

| Member | Description |
| :--- | --- |
| addToReviewSet | The operation represents adding data to a review set from an eDiscovery collection. |
| applyTags | The operation represents bulk tagging documents in a review set for the specified review set query. |
| contentExport | The operation represents a content export from a review set. |
| convertToPdf | The operation represents converting documents to PDFs with redactions. |
| estimateStatistics | The operation represents searching against Microsoft 365 services such as Exchange, SharePoint, and OneDrive for business. |
| purgeData | The operation represents purging content from the source workloads. |

### caseOperationStatus values

| Member | Description |
| :--- | --- |
| notStarted | The operation has not yet started. |
| submissionFailed | Submission of the operation failed. |
| running | The operation is currently running. |
| succeeded | The operation was successfully completed without any errors. |
| partiallySucceeded | The operation completed, but there were errors - See [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-beta) for error details. |
| failed | The operation failed - See result info for error details. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.caseOperation",
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
  }
}
```
