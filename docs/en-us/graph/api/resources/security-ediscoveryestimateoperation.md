<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryestimateoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# ediscoveryEstimateOperation resource type

Namespace: microsoft.graph.security

Represents the process of estimating statistics \(items count, size, and number of locations\) of an eDiscovery search.

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.security.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseaction-values) | The type of action the operation represents. The possible values are: `contentExport`, `applyTags`, `convertToPdf`, `index`, `estimateStatistics`, `addToReviewSet`, `holdUpdate`, `unknownFutureValue`, `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| completedDateTime | DateTimeOffset | The date and time the operation was completed. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the operation was started. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| id | String | The ID for the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| indexedItemCount | Int64 | The estimated count of items for the **search** that matched the content query. |
| indexedItemsSize | Int64 | The estimated size of items for the **search** that matched the content query. |
| mailboxCount | Int32 | The number of mailboxes that had search hits. |
| percentProgress | Int32 | The progress of the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| reportFileMetadata | [microsoft.graph.security.reportFileMetadata](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreportfilemetadata?view=graph-rest-1.0) collection | Contains the properties for report file metadata, including **downloadUrl**, **fileName**, and **size**. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | Contains success and failure-specific result information. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| siteCount | Int32 | The number of mailboxes that had search hits. |
| statisticsOptions | [microsoft.graph.security.statisticsOptions](#statisticsoptions-values) | The options to generate statistics. The possible values are: `includeRefiners`, `includeQueryStats`, `includeUnindexedStats`, `advancedIndexing`, `locationsWithoutHits`, `unknownFutureValue`. |
| status | microsoft.graph.security.caseOperationStatus | The status of the case operation. The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`, `unknownFutureValue`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| unindexedItemCount | Int64 | The estimated count of unindexed items for the collection. |
| unindexedItemsSize | Int64 | The estimated size of unindexed items for the collection. |

### statisticsOptions values

| Name | Description |
| :--- | :--- |
| includeRefiners | Refine with categories to include people, sensitive information types, item types, and errors. |
| includeQueryStats | Include query keywords report to assess the relevance of your search query. |
| includeUnindexedStats | Include partially indexed items. |
| advancedIndexing | Perform advanced indexing during search to reduce false matches. |
| locationsWithoutHits | Estimate unindexed items even in locations without hits. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| search | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) | eDiscovery search. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryEstimateOperation",
  "action": "String",
  "completedDateTime": "String (timestamp)",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "indexedItemCount": "Int64",
  "indexedItemsSize": "Int64",
  "mailboxCount": "Int32",
  "percentProgress": "Int32",
  "reportFileMetadata": [{"@odata.type": "microsoft.graph.reportFileMetadata"}],
  "resultInfo": {"@odata.type": "microsoft.graph.resultInfo"},
  "siteCount": "Int32",
  "statisticsOptions": "String",
  "status": "String",
  "unindexedItemCount": "Int64",
  "unindexedItemsSize": "Int64"
}
```
