<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-manualalert?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# manualAlert resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a manually created security alert in Microsoft 365 Defender. Enables security analysts to create custom alerts based on their investigations and findings. When a manual alert is created, the backend automatically creates a new incident to contain the alert, or links the alert to an existing incident if specified.

Inherits from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-alert-post-manualalert?view=graph-rest-beta) | [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta) | Create a manual security alert with specified entities and metadata. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actorDisplayName | String | The adversary or activity group associated with this alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| additionalData | [microsoft.graph.security.dictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-dictionary?view=graph-rest-beta) | A collection of other alert properties, including user-defined properties. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| alertPolicyId | String | The ID of the policy that generated the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| alertWebUrl | String | URL for the alert page in the Microsoft 365 Defender portal. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| assignedTo | String | Owner of the alert, or null if no owner is assigned. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| categories | String collection | The attack kill-chain categories that the alert belongs to. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| category | String | The attack kill-chain category that the alert belongs to. Aligned with the MITRE ATT&CK framework. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| classification | [microsoft.graph.security.alertClassification](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta#alertclassification-values) | Specifies whether the alert represents a true threat. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| comments | [microsoft.graph.security.alertComment](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcomment?view=graph-rest-beta) collection | Array of comments created by the Security Operations \(SecOps\) team during the alert management process. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Time when Microsoft 365 Defender created the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| customDetails | [microsoft.graph.security.dictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-dictionary?view=graph-rest-beta) | A dictionary of custom key-value pairs associated with the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| description | String | String value describing each alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| detectionSource | [microsoft.graph.security.detectionSource](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionsource?view=graph-rest-beta) | Detection technology or sensor that identified the notable component or activity. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| detectorId | String | The ID of the detector that triggered the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| determination | [microsoft.graph.security.alertDetermination](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta#alertdetermination-values) | Specifies the result of the investigation, whether the alert represents a true attack and if so, the nature of the attack. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| evidence | [microsoft.graph.security.alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-beta) collection | Collection of evidence related to the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| firstActivityDateTime | DateTimeOffset | The earliest activity associated with the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| id | String | Unique identifier for the alert. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| incidentId | String | Unique identifier to represent the incident this alert resource is associated with. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| incidentWebUrl | String | URL for the incident page in the Microsoft 365 Defender portal. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| investigationState | [microsoft.graph.security.investigationState](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta#investigationstate-values) | The state of the investigation. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| isExcludedFromCorrelation | Boolean | When `true`, excludes the alert from automatic correlation. Default is `false`. |
| lastActivityDateTime | DateTimeOffset | The oldest activity associated with the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| lastUpdateDateTime | DateTimeOffset | Time when the alert was last updated at Microsoft 365 Defender. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| linkToIncident | Int64 | ID of an existing incident to link to. If not provided, a new incident is created automatically. |
| mitreTechniques | String collection | The attack techniques, as aligned with the MITRE ATT&CK framework. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| productName | String | The name of the product which published this alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| providerAlertId | String | The ID of the alert as it appears in the security provider product that generated the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| recommendedActions | String | Recommended response and remediation actions to take in the event this alert was generated. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| resolvedDateTime | DateTimeOffset | Time when the alert was resolved. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| sentinelWorkspace | String | Sentinel workspace identifier for workspace routing. |
| serviceSource | [microsoft.graph.security.serviceSource](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta) | The service or product that created this alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| severity | [microsoft.graph.security.alertSeverity](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta#alertseverity-values) | Indicates the possible impact on assets. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| status | [microsoft.graph.security.alertStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta) | The status of the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| systemTags | String collection | The system tags associated with the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| tenantId | String | The Microsoft Entra tenant the alert was created in. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| threatDisplayName | String | The threat associated with this alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| threatFamilyName | String | Threat family associated with this alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |
| title | String | Brief identifying string value describing the alert. Inherited from [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| entityDefinitions | [microsoft.graph.security.entityDefinitionInput](https://learn.microsoft.com/en-us/graph/api/resources/security-entitydefinitioninput?view=graph-rest-beta) collection | The entities associated with the alert. Each item specifies a security entity \(such as a user, device, or IP address\), its identifier, and its role in the alert context. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.manualAlert",
  "id": "String (identifier)",
  "providerAlertId": "String",
  "incidentId": "String",
  "status": "String",
  "severity": "String",
  "classification": "String",
  "determination": "String",
  "serviceSource": "String",
  "detectionSource": "String",
  "productName": "String",
  "detectorId": "String",
  "tenantId": "String",
  "title": "String",
  "description": "String",
  "recommendedActions": "String",
  "category": "String",
  "categories": [
    "String"
  ],
  "assignedTo": "String",
  "alertWebUrl": "String",
  "incidentWebUrl": "String",
  "actorDisplayName": "String",
  "threatDisplayName": "String",
  "threatFamilyName": "String",
  "mitreTechniques": [
    "String"
  ],
  "createdDateTime": "String (timestamp)",
  "lastUpdateDateTime": "String (timestamp)",
  "resolvedDateTime": "String (timestamp)",
  "firstActivityDateTime": "String (timestamp)",
  "lastActivityDateTime": "String (timestamp)",
  "comments": [
    {
      "@odata.type": "microsoft.graph.security.alertComment"
    }
  ],
  "evidence": [
    {
      "@odata.type": "microsoft.graph.security.alertEvidence"
    }
  ],
  "systemTags": [
    "String"
  ],
  "alertPolicyId": "String",
  "additionalData": {
    "@odata.type": "microsoft.graph.security.dictionary"
  },
  "customDetails": {
    "@odata.type": "microsoft.graph.security.dictionary"
  },
  "investigationState": "String",
  "linkToIncident": "Integer",
  "isExcludedFromCorrelation": "Boolean",
  "sentinelWorkspace": "String"
}
```
