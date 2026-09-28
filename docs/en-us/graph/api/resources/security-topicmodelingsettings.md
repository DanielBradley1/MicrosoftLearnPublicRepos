<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-topicmodelingsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# topicModelingSettings resource type

Namespace: microsoft.graph.security

Represents topic modeling \(Themes\) settings for an eDiscovery case. To learn more, see [Configure search and analytics settings in eDiscovery \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dynamicallyAdjustTopicCount | Boolean | Indicates whether the themes model should dynamically optimize the number of generated topics. To learn more, see [Adjust maximum number of themes dynamically](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#themes). |
| ignoreNumbers | Boolean | Indicates whether the themes model should exclude numbers while parsing document texts. To learn more, see [Include numbers in themes](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#themes). |
| isEnabled | Boolean | Indicates whether themes model is enabled for the case. |
| topicCount | Int32 | The total number of topics that the themes model will generate for a review set. To learn more, see [Maximum number of themes](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery#themes). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.topicModelingSettings",
  "isEnabled": "Boolean",
  "ignoreNumbers": "Boolean",
  "topicCount": "Integer",
  "dynamicallyAdjustTopicCount": "Boolean"
}
```
