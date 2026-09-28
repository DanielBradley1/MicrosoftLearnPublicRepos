<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# ediscoveryCaseSettings resource type

Namespace: microsoft.graph.security

Contains settings for an eDiscovery case. For details, see [Configure search and analytics settings in eDiscovery \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get settings](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycasesettings-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCaseSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoveryCaseSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0) object. |
| [Update settings](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycasesettings-update?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCaseSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0) | Update the properties of an [ediscoveryCaseSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasesettings?view=graph-rest-1.0) object. |
| [Reset settings to default](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycasesettings-resettodefault?view=graph-rest-1.0) | None | Reset all settings to the default values. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| caseType | [microsoft.graph.security.caseType](#casetype-values) | The type of the eDiscovery case. The possible values are: `standard`, `premium`, `unknownFutureValue`. |
| id | String | The ID of the eDiscovery case. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| ocr | [microsoft.graph.security.ocrSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-ocrsettings?view=graph-rest-1.0) | The OCR \(Optical Character Recognition\) settings for the case. |
| redundancyDetection | [microsoft.graph.security.redundancyDetectionSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-redundancydetectionsettings?view=graph-rest-1.0) | The redundancy \(near duplicate and email threading\) detection settings for the case. |
| reviewSetSettings | [microsoft.graph.security.reviewSetSettings](#reviewsetsettings-values) | The settings of the review set for the case. The possible values are: `none`, `disableGrouping`, `unknownFutureValue`. |
| topicModeling | [microsoft.graph.security.topicModelingSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-topicmodelingsettings?view=graph-rest-1.0) | The Topic Modeling \(Themes\) settings for the case. |

### caseType values

| Member | Description |
| :--- | :--- |
| standard | Standard eDiscovery case for E3 tenants. |
| premium | Premium eDiscovery case with advanced features for E5 tenants. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### reviewSetSettings values

| Member | Description |
| :--- | :--- |
| none | No other options selected. |
| disableGrouping | Disable the grouping control. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryCaseSettings",
  "caseType": "String",
  "id": "String (identifier)",
  "ocr": {"@odata.type": "microsoft.graph.security.ocrSettings"},
  "redundancyDetection": {"@odata.type": "microsoft.graph.security.redundancyDetectionSettings"},
  "reviewSetSettings": "String",
  "topicModeling": {"@odata.type": "microsoft.graph.security.topicModelingSettings"}
}
```
