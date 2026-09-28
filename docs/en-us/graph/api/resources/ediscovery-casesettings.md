<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# caseSettings resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Contains settings for an eDiscovery case. For details, see [Configure search and analytics settings in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/configure-search-and-analytics-settings-in-advanced-ediscovery).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get settings](https://learn.microsoft.com/en-us/graph/api/ediscovery-casesettings-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.ediscovery.caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) object. |
| [Update settings](https://learn.microsoft.com/en-us/graph/api/ediscovery-casesettings-update?view=graph-rest-beta) | [microsoft.graph.ediscovery.caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) | Update the properties of a [microsoft.graph.ediscovery.caseSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-casesettings?view=graph-rest-beta) object. |
| [Reset to default](https://learn.microsoft.com/en-us/graph/api/ediscovery-casesettings-resettodefault?view=graph-rest-beta) | None | Reset all settings to the default values. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| Id | String | The ID of the eDiscovery case. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| ocr | [microsoft.graph.ediscovery.ocrSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-ocrsettings?view=graph-rest-beta) | The OCR \(Optical Character Recognition\) settings for the case. |
| redundancyDetection | [microsoft.graph.ediscovery.redundancyDetectionSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-redundancydetectionsettings?view=graph-rest-beta) | The redundancy \(near duplicate and email threading\) detection settings for the case. |
| topicModeling | [microsoft.graph.ediscovery.topicModelingSettings](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-topicmodelingsettings?view=graph-rest-beta) | The article Modeling \(Themes\) settings for the case. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.caseSettings",
  "id": "String (identifier)",
  "redundancyDetection": {
    "@odata.type": "microsoft.graph.ediscovery.redundancyDetectionSettings"
  },
  "topicModeling": {
    "@odata.type": "microsoft.graph.ediscovery.topicModelingSettings"
  },
  "ocr": {
    "@odata.type": "microsoft.graph.ediscovery.ocrSettings"
  }
}
```
