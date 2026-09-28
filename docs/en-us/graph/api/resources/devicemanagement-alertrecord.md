<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# alertRecord resource type

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the record of an alert event in the Microsoft Endpoint Manager admin center triggered by an [alertRule](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta).

When the threshold of an **alertRule** is reached, an **alertRecord** is generated and stored, and administrators receive notifications via defined notification channels.

For more information, see the [monitoring](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta) resource.

Note

This API is part of the [alert monitoring API set](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta&preserve-view=true) which currently supports only [Windows 365](https://learn.microsoft.com/en-us/windows-365/overview) and Cloud PC scenarios. The API set allows admins to set up rules to alert issues with provisioning Cloud PCs, uploading Cloud PC images, and checking Azure network connections.

Have a different scenario that can use additional programmatic alert support on the Microsoft Endpoint Manager admin center? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/devicemanagement-alertrecord-list?view=graph-rest-beta) | [microsoft.graph.deviceManagement.alertRecord](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) collection | Get a list of the [alertRecord](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/devicemanagement-alertrecord-get?view=graph-rest-beta) | [microsoft.graph.deviceManagement.alertRecord](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) | Read the properties and relationships of an [alertRecord](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) object. |
| [Get portal notifications](https://learn.microsoft.com/en-us/graph/api/devicemanagement-alertrecord-getportalnotifications?view=graph-rest-beta) | [microsoft.graph.deviceManagement.portalNotification](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-portalnotification?view=graph-rest-beta) collection | Get a list of all portal notifications that one or more users can access, from the Microsoft Endpoint Manager admin center. |
| [Set portal notification as sent](https://learn.microsoft.com/en-us/graph/api/devicemanagement-alertrecord-setportalnotificationassent?view=graph-rest-beta) | None | Set the status of the specified notification on the Microsoft EndPoint Manager admin center as sent. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertImpact | [microsoft.graph.deviceManagement.alertImpact](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertimpact?view=graph-rest-beta) | The impact of the alert event. Consists of a list of key-value pair and a number followed by the aggregation type. For example, `6 affectedCloudPcCount` means that 6 Cloud PCs are affected. `12 affectedCloudPcPercentage` means 12% of Cloud PCs are affected. The list of key-value pair indicates the details of the alert impact. |
| alertRuleId | String | The corresponding ID of the alert rule. |
| alertRuleTemplate | [microsoft.graph.deviceManagement.alertRuleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta#alertruletemplate-values) | The rule template of the alert event. The possible values are: `cloudPcProvisionScenario`, `cloudPcImageUploadScenario`, `cloudPcOnPremiseNetworkConnectionCheckScenario`, `unknownFutureValue`, `cloudPcInGracePeriodScenario`, `cloudPcFrontlineInsufficientLicensesScenario`, `cloudPcInaccessibleScenario`, `cloudPcFrontlineConcurrencyScenario`, `cloudPcUserSettingsPersistenceScenario`, `cloudPcDeprovisionFailedScenario`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `cloudPcInGracePeriodScenario`, `cloudPcFrontlineInsufficientLicensesScenario`, `cloudPcInaccessibleScenario`, `cloudPcFrontlineConcurrencyScenario`, `cloudPcUserSettingsPersistenceScenario`, `cloudPcDeprovisionFailedScenario`. |
| detectedDateTime | DateTimeOffset | The date and time when the alert event was detected. The Timestamp type represents date and time information using ISO 8601 format. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The display name of the alert record. |
| id | String | The unique identifier for the alert record. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastUpdatedDateTime | DateTimeOffset | The date and time when the alert record was last updated. The Timestamp type represents date and time information using ISO 8601 format. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| resolvedDateTime | DateTimeOffset | The date and time when the alert event was resolved. The Timestamp type represents date and time information using ISO 8601 format. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| severity | [microsoft.graph.deviceManagement.ruleSeverityType](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta#ruleseveritytype-values) | The severity of the alert event. The possible values are: `unknown`, `informational`, `warning`, `critical`, `unknownFutureValue`. |
| status | [microsoft.graph.deviceManagement.alertStatusType](#alertstatustype-values) | The status of the alert record. The possible values are: `active`, `resolved`, `unknownFutureValue`. |

### alertStatusType values

| Member | Description |
| :--- | :--- |
| active | The alert is active. |
| resolved | The alert is marked as resolved. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagement.alertRecord",
  "alertImpact": {
    "@odata.type": "microsoft.graph.deviceManagement.alertImpact"
  },  
  "alertRuleId": "String",
  "alertRuleTemplate": "String",
  "detectedDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "lastUpdatedDateTime": "String (timestamp)",
  "resolvedDateTime": "String (timestamp)",
  "severity": "String",
  "status": "String"
}
```
