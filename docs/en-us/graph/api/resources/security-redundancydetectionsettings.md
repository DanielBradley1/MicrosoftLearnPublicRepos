<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-redundancydetectionsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# redundancyDetectionSettings resource type

Namespace: microsoft.graph.security

Represents redundancy \(email threading and near duplicate detection\) settings for an eDiscovery case.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether email threading and near duplicate detection are enabled. |
| maxWords | Int32 | Specifies the maximum number of words used for email threading and near duplicate detection. To learn more, see [Minimum/maximum number of words](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#near-duplicates-and-email-threading). |
| minWords | Int32 | Specifies the minimum number of words used for email threading and near duplicate detection. To learn more, see [Minimum/maximum number of words](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#near-duplicates-and-email-threading). |
| similarityThreshold | Int32 | Specifies the similarity level for documents to be put in the same near duplicate set. To learn more, see [Document and email similarity threshold](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#near-duplicates-and-email-threading). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.redundancyDetectionSettings",
  "isEnabled": "Boolean",
  "similarityThreshold": "Integer",
  "minWords": "Integer",
  "maxWords": "Integer"
}
```
