<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# ediscoverySearchExportOperation resource type

Namespace: microsoft.graph.security

Represents the process of an [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) export.

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.security.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseaction-values) | The type of action the operation represents. The possible values are: `contentExport`, `applyTags`, `convertToPdf`, `index`, `estimateStatistics`, `addToReviewSet`, `holdUpdate`, `unknownFutureValue`, `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| additionalOptions | [microsoft.graph.security.additionalOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#additionaloptions-values) | The additional items to include in the export. The possible values are: `none`, `teamsAndYammerConversations`, `cloudAttachments`, `allDocumentVersions`, `subfolderContents`, `listAttachments`, `unknownFutureValue`, `htmlTranscripts`, `advancedIndexing`, `allItemsInFolder`, `includeFolderAndPath`, `condensePaths`, `friendlyName`, `splitSource`, `includeReport`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `htmlTranscripts`, `advancedIndexing`, `allItemsInFolder`, `includeFolderAndPath`, `condensePaths`, `friendlyName`, `splitSource`, `includeReport`. |
| cloudAttachmentVersion | microsoft.graph.security.cloudAttachmentVersion | The versions of cloud attachments to include in messages. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. |
| completedDateTime | DateTimeOffset | The date and time when the operation was completed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the operation was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| description | String | The description of the export by the user. |
| displayName | String | The name of export provided by the user. |
| documentVersion | microsoft.graph.security.documentVersion | The versions of files in SharePoint to include. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. |
| exportCriteria | [microsoft.graph.security.exportCriteria](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#exportcriteria-values) | Items to be included in the export. The possible values are: `searchHits`, `partiallyIndexed`, `unknownFutureValue`. |
| exportFileMetadata | [microsoft.graph.security.ediscoveryExportFileMetadata](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryexportfilemetadata?view=graph-rest-1.0) collection | Contains the properties for an export file metadata, including **downloadUrl**, **fileName**, and **size**. |
| exportFormat | [microsoft.graph.security.exportFormat](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#exportformat-values) | Format of the emails of the export. The possible values are: `pst`, `msg`, `eml` \(deprecated\), `unknownFutureValue`. The `eml` member is deprecated. It remains in v1.0 for backward compatibility. Going forward, use either `pst` or `msg`. |
| exportLocation | [microsoft.graph.security.exportLocation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearchexportoperation?view=graph-rest-1.0#exportlocation-values) | Location scope for partially indexed items. You can choose to include partially indexed items only in responsive locations with search hits or in all targeted locations. The possible values are: `responsiveLocations`, `nonresponsiveLocations`, `unknownFutureValue`. |
| exportSingleItems | Boolean | Indicates whether to export single items. |
| id | String | The ID for the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| percentProgress | Int32 | The progress of the operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| resultInfo | [microsoft.graph.resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | Contains success and failure-specific result information. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| status | [microsoft.graph.security.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseoperationstatus-values) | The status of the case operation. The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`, `unknownFutureValue`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |

### additionalOptions values

| Member | Description |
| :--- | --- |
| none | No additional options selected. |
| teamsAndYammerConversations | Collect up to 12 hours of related conversations when a message matches a search. |
| cloudAttachments | Collect items from links to SharePoint or OneDrive. |
| allDocumentVersions | Collect all versions of SharePoint documents. If not selected, only current versions are collected. |
| subfolderContents | Collect items inside subfolders of a matched folder. |
| listAttachments | Collect files attached to SharePoint lists and their child items. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| htmlTranscripts | Contextual chat messages are threaded into HTML transcripts. |
| advancedIndexing | Perform advanced indexing during export to reduce false matches. |
| allItemsInFolder | Include all content in the list if the list itself matches a query. |
| includeFolderAndPath | Include the folder and path structure of the source. |
| condensePaths | Shorten file paths to fit within 1,024 characters. |
| friendlyName | Give each item a friendly name. |
| splitSource | Organize data from different locations into separate folders or PSTs. |
| includeReport | Include report of item metadata. |

### exportCriteria values

| Member | Description |
| :--- | --- |
| searchHits | Export collected items with search hits. |
| partiallyIndexed | Include partially indexed items, such as those in unrecognized formats, encrypted, or not indexed for other reasons. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### exportFormat values

| Member | Description |
| :--- | --- |
| pst | Individual .pst files for each mailbox. |
| msg | Individual .msg files for each message. |
| eml \(deprecated\) | Individual .eml files for each message. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

Tip

The `eml` member is deprecated. It remains in v1.0 for backward compatibility. Going forward, use either `pst` or `msg`.

### exportLocation values

| Member | Description |
| :--- | --- |
| responsiveLocations | Locations with search hits only. |
| nonresponsiveLocations | Locations with no search hits. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| search | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) | The eDiscovery searches under each case. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoverySearchExportOperation",
  "action": "String",
  "additionalOptions": "String",
  "cloudAttachmentVersion": "String",
  "completedDateTime": "String (timestamp)",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "documentVersion": "String",
  "exportCriteria": "String",
  "exportFileMetadata": [{"@odata.type": "microsoft.graph.security.ediscoveryExportFileMetadata"}],
  "exportFormat": "String",
  "exportLocation": "String",
  "exportSingleItems": "Boolean",
  "id": "String (identifier)",
  "percentProgress": "Int32",
  "resultInfo": {"@odata.type": "microsoft.graph.resultInfo"},
  "status": "String"
}
```
