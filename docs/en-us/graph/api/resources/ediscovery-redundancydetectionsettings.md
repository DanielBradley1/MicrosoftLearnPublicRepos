<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-redundancydetectionsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# redundancyDetectionSettings resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Redundancy \(email threading and near duplicate detection\) settings for an eDiscovery case.

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
  "@odata.type": "#microsoft.graph.ediscovery.redundancyDetectionSettings",
  "isEnabled": "Boolean",
  "similarityThreshold": "Integer",
  "minWords": "Integer",
  "maxWords": "Integer"
}
```
