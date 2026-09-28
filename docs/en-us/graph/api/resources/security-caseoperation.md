<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# caseOperation resource type

Namespace: microsoft.graph.security

An abstract entity that represents a long-running eDiscovery process. It contains a common set of properties that are shared among inheriting entities. Entities that derive from **caseOperation** include:

- [ediscoveryIndexOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryindexoperation?view=graph-rest-1.0)
- [ediscoveryHoldOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdoperation?view=graph-rest-1.0)
- [ediscoveryPurgeDataOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverypurgedataoperation?view=graph-rest-1.0)
- [ediscoveryEstimateOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryestimateoperation?view=graph-rest-1.0)
- [ediscoveryAddToReviewSetOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryaddtoreviewsetoperation?view=graph-rest-1.0)
- [ediscoveryTagOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverytagoperation?view=graph-rest-1.0)
- [ediscoveryExportOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryexportoperation?view=graph-rest-1.0)
- [ediscoverySearchExportOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0)
- [ediscoveryHoldPolicySyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicysyncoperation?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-operations?view=graph-rest-1.0) | [microsoft.graph.security.caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0) collection | Get a list of the [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-caseoperation-get?view=graph-rest-1.0) | [microsoft.graph.security.caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0) | Read the properties and relationships of a [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.security.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseaction-values) | The type of action the operation represents. The possible values are: `contentExport`, `applyTags`, `convertToPdf`, `index`, `estimateStatistics`, `addToReviewSet`, `holdUpdate`, `unknownFutureValue`, `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. |
| completedDateTime | DateTimeOffset | The date and time the operation was completed. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user that created the operation. |
| createdDateTime | DateTimeOffset | The date and time the operation was created. |
| id | String | The ID for the operation. Read-only. |
| percentProgress | Int32 | The progress of the operation. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | Contains success and failure-specific result information. |
| status | [microsoft.graph.security.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseoperationstatus-values) | The status of the case operation. The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`, `unknownFutureValue`. |

### caseAction values

| Member | Description |
| :--- | --- |
| contentExport | The operation represents a content export from a review set. |
| applyTags | The operation represents bulk tagging documents in a review set for the specified review set query. |
| convertToPdf | The operation represents converting documents to PDFs with redactions. |
| index | The operation represents indexing data sources of custodians and noncustodial data sources to make them searchable. |
| estimateStatistics | The operation represents searching against Microsoft 365 services such as Exchange, SharePoint, and OneDrive for Business. |
| addToReviewSet | The operation represents adding data to a review set from an eDiscovery collection. |
| holdUpdate | The operation represents updating legal hold \(apply/remove\) for custodians and noncustodial data sources. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| purgeData | The operation represents purging content from the source workloads. |
| exportReport | The operation exports an item report from an estimated search. |
| exportResult | The operation exports item results from an estimated search. |
| holdPolicySync | The operation represents the addition or update of a legal hold policy. |

### caseOperationStatus values

| Member | Description |
| :--- | --- |
| notStarted | The operation hasn't yet started. |
| submissionFailed | Submission of the operation failed. |
| running | The operation is currently running. |
| succeeded | The operation was successfully completed without any errors. |
| partiallySucceeded | The operation completed, but there were errors. For error details, see [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0). |
| failed | The operation failed. For error details, see [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseOperation",
  "action": "String",  
  "completedDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "percentProgress": "Int32",
  "resultInfo": {
    "@odata.type": "microsoft.graph.resultInfo"
  },
  "status": "String"
}
```
