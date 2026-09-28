<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryaddtoreviewsetoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-25 -->

# ediscoveryAddToReviewSetOperation resource type

Namespace: microsoft.graph.security

Represents an operation to add an [eDiscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) to an [eDiscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0).

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.security.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseaction-values) | The type of action the operation represents. The possible values are: `contentExport`, `applyTags`, `convertToPdf`, `index`, `estimateStatistics`, `addToReviewSet`, `holdUpdate`, `unknownFutureValue`, `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| additionalDataOptions | [microsoft.graph.security.additionalDataOptions](#additionaldataoptions-values) | The options to add items to the review set. The possible values are: `allVersions`, `linkedFiles`, `unknownFutureValue`, `advancedIndexing`, `listAttachments`, `htmlTranscripts`, `messageConversationExpansion`, `locationsWithoutHits`, `allItemsInFolder`, `cloudNativeHtmlConversion`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `advancedIndexing`, `listAttachments`, `htmlTranscripts`, `messageConversationExpansion`, `locationsWithoutHits`, `allItemsInFolder`, `cloudNativeHtmlConversion`. |
| cloudAttachmentVersion | microsoft.graph.security.cloudAttachmentVersion | Specifies the number of most recent versions of cloud attachments to collect. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. |
| completedDateTime | DateTimeOffset | The date and time the operation was completed. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user that created the operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the operation was created. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| documentVersion | microsoft.graph.security.documentVersion | Specifies the number of most recent versions of SharePoint documents to collect. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. |
| id | String | The ID for the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| itemsToInclude | [microsoft.graph.security.itemsToInclude](#itemstoinclude-values) | The items to include in the review set. The possible values are: `searchHits`, `partiallyIndexed`, `unknownFutureValue`. |
| percentProgress | Int32 | The progress of the operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| reportFileMetadata | [microsoft.graph.security.reportFileMetadata](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreportfilemetadata?view=graph-rest-1.0) collection | Contains the properties for report file metadata, including **downloadUrl**, **fileName**, and **size**. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | Contains success and failure-specific result information. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| status | microsoft.graph.security.caseOperationStatus | The status of the case operation. The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`, `unknownFutureValue`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |

### additionalDataOptions values

| Name | Description |
| :--- | :--- |
| allVersions | Include all versions of a SharePoint document that match the source collection query. Caution: SharePoint versions can significantly increase the volume of items. |
| linkedFiles | Include linked files shared in Outlook, Teams, or Engage messages by attaching a link to the file. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| advancedIndexing | To reduce false matches, perform advanced indexing during export. |
| listAttachments | Include list attachments. |
| htmlTranscripts | Contextual chat messages are threaded into HTML transcript. |
| messageConversationExpansion | Include conversation context around a hit. |
| locationsWithoutHits | Look for unindexed items even in locations without hits. |
| allItemsInFolder | Include all content in the folder if the folder itself matches a query. |
| cloudNativeHtmlConversion | Convert items to cloud-native HTML format during review set collection. |

### itemsToInclude values

| Member | Description |
| :--- | :--- |
| searchHits | Include indexed items that match. |
| partiallyIndexed | Include unindexed items that might not match the query. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| reviewSet | [microsoft.graph.security.ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0) | eDiscovery review set to which items matching source collection query gets added. |
| search | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) | eDiscovery search that gets added to review set. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryAddToReviewSetOperation",
  "action": "String",
  "additionalDataOptions": "String",
  "cloudAttachmentVersion": "String",
  "completedDateTime": "String (timestamp)",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "documentVersion": "String",
  "id": "String (identifier)",
  "itemsToInclude": "String",
  "percentProgress": "Int32",
  "reportFileMetadata": [{"@odata.type": "microsoft.graph.reportFileMetadata"}],
  "resultInfo": {"@odata.type": "microsoft.graph.resultInfo"},
  "status": "String"
}
```
