<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-portalnotification?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# portalNotification resource type

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the portal notification associated with the [alert record](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) of a user.

Note

This API is part of the [alert monitoring API set](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta&preserve-view=true) which currently supports only [Windows 365](https://learn.microsoft.com/en-us/windows-365/overview) and Cloud PC scenarios. The API set allows admins to set up rules to alert issues with provisioning Cloud PCs, uploading Cloud PC images, and checking Azure network connections.

Have a different scenario that can use additional programmatic alert support on the Microsoft Endpoint Manager admin center? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertImpact | [microsoft.graph.deviceManagement.alertImpact](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertimpact?view=graph-rest-beta) | The associated alert impact. |
| alertRecordId | String | The associated alert record ID. |
| alertRuleId | String | The associated alert rule ID. |
| alertRuleName | String | The associated alert rule name. |
| alertRuleTemplate | [microsoft.graph.deviceManagement.alertRuleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta#alertruletemplate-values) | The associated alert rule template. The possible values are: `cloudPcProvisionScenario`, `cloudPcImageUploadScenario`, `cloudPcOnPremiseNetworkConnectionCheckScenario`, `unknownFutureValue`, `cloudPcInGracePeriodScenario`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `cloudPcInGracePeriodScenario`. |
| id | String | The unique identifier for the portal notification. |
| isPortalNotificationSent | Boolean | `true` if the portal notification has already been sent to the user; `false` otherwise. |
| severity | [microsoft.graph.deviceManagement.ruleSeverityType](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta#ruleseveritytype-values) | The associated alert rule severity. The possible values are: `unknown`, `informational`, `warning`, `critical`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagement.portalNotification",
  "alertImpact": {
    "@odata.type": "microsoft.graph.deviceManagement.alertImpact"
  },
  "alertRecordId": "String",
  "alertRuleId": "String",
  "alertRuleName": "String",
  "alertRuleTemplate": "String",
  "id": "String (identifier)",
  "isPortalNotificationSent": "Boolean",
  "severity": "String"
}
```
