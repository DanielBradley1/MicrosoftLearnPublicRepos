<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alert?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# alert resource type \(in Global Secure Access\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an alert detected by Global Secure Access. Each entity is a separate instance of an alert.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-alerts?view=graph-rest-beta) | [microsoft.graph.networkaccess.alert](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alert?view=graph-rest-beta) collection | Get a list of the alert objects and their properties. |
| [Get alert severity summaries](https://learn.microsoft.com/en-us/graph/api/networkaccess-alert-getalertseveritysummaries?view=graph-rest-beta) | [microsoft.graph.networkaccess.alertSeveritySummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alertseveritysummary?view=graph-rest-beta) collection | Returns a collection containing count tables for all alert severity types in global secure access. |
| [Get alert frequencies](https://learn.microsoft.com/en-us/graph/api/networkaccess-alert-getalertfrequencies?view=graph-rest-beta) | [microsoft.graph.networkaccess.alertFrequencyPoint](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alertfrequencypoint?view=graph-rest-beta) collection | Returns a collection containing count tables for all alert severity type per day in global secure access. |
| [Get alert summaries](https://learn.microsoft.com/en-us/graph/api/networkaccess-alert-getalertsummaries?view=graph-rest-beta) | [microsoft.graph.networkaccess.alertSummary](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alertsummary?view=graph-rest-beta) collection | Returns a collection containing count tables for all alert types and their severities in global secure access. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actions | [microsoft.graph.networkaccess.alertAction](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alertaction?view=graph-rest-beta) collection | List of possible action items to take based on the alert \(if applicable\). |
| alertType | microsoft.graph.networkaccess.alertType | The type of the alert out of a closed list. Required. The possible values are: `unhealthyRemoteNetworks`, `unhealthyConnectors`, `deviceTokenInconsistency`, `crossTenantAnomaly`, `suspiciousProcess`, `threatIntelligenceTransactions`, `unknownFutureValue`, `webContentBlocked`, `malware`, `patientZero`, `dlp`, `fallback`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `webContentBlocked` , `malware` , `patientZero` , `dlp` , `fallback`. |
| categories | microsoft.graph.networkaccess.intentCategory collection | Categories associated with the alert. |
| componentName | String | Component name related to the alert. |
| creationDateTime | DateTimeOffset | The time the alert was created in the system. Required. |
| description | String | Text description explaining the alert. |
| detectionTechnology | String | Alert detection technology. |
| displayName | String | The display name of the alert. Required. |
| extendedProperties | [microsoft.graph.networkaccess.extendedProperties](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-extendedproperties?view=graph-rest-beta) | Extended properties for the alert. |
| firstActivityDateTime | DateTimeOffset | The time of the first activity related to the alert. |
| id | String | Generated identifier for the alert. Required. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isPreview | Boolean | Indicates if the alert is a preview. |
| lastActivityDateTime | DateTimeOffset | The time of the last activity related to the alert. |
| productName | String | The name of the product that raised the alert. |
| relatedResources | [microsoft.graph.networkaccess.relatedResource](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedresource?view=graph-rest-beta) collection | List of related resources to the alert \(if applicable\). |
| severity | microsoft.graph.networkaccess.alertSeverity | The severity of the alert as it is reported by the provider. Required. The possible values are: `informational`, `low`, `medium`, `high`, `unknownFutureValue`. |
| subTechniques | String collection | Sub-techniques associated with the alert. |
| techniques | String collection | Techniques associated with the alert. |
| vendorName | String | The name of the vendor that raised the alert. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) | The filtering policy associated with the alert. This relationship allows you to retrieve or manage the filtering policy that triggered or is related to the alert instance. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.alert",
  "id": "String (identifier)",
  "alertType": "String",
  "creationDateTime": "String (timestamp)",
  "description": "String",
  "actions": [
    {
      "@odata.type": "microsoft.graph.networkaccess.alertAction"
    }
  ],
  "relatedResources": [
    {
      "@odata.type": "microsoft.graph.networkaccess.relatedRemoteNetwork"
    }
  ],
  "vendorName": "String",
  "detectionTechnology": "String",
  "severity": "String",
  "displayName": "String",
  "productName": "String",
  "componentName": "String",
  "categories": [
    "String"
  ],
  "techniques": [
    "String"
  ],
  "subTechniques": [
    "String"
  ],
  "firstActivityDateTime": "String (timestamp)",
  "lastActivityDateTime": "String (timestamp)",
  "isPreview": "Boolean",
  "extendedProperties": {
    "@odata.type": "microsoft.graph.networkaccess.extendedProperties"
  }
}
```
