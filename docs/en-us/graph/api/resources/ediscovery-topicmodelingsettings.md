<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-topicmodelingsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# topicModelingSettings resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Article modeling \(Themes\) settings for an eDiscovery case. To learn more, see [Configure search and analytics settings in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dynamicallyAdjustTopicCount | Boolean | To learn more, see [Adjust maximum number of themes dynamically](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#themes). |
| ignoreNumbers | Boolean | To learn more, see [Include numbers in themes](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#themes). |
| isEnabled | Boolean | Indicates whether themes are enabled for the case. |
| topicCount | Int32 | To learn more, see [Maximum number of themes](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#themes). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.topicModelingSettings",
  "isEnabled": "Boolean",
  "ignoreNumbers": "Boolean",
  "topicCount": "Integer",
  "dynamicallyAdjustTopicCount": "Boolean"
}
```
