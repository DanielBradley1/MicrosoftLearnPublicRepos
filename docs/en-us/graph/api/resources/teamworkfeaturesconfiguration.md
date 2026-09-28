<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkfeaturesconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkFeaturesConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Microsoft Teams client configuration details for a Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailToSendLogsAndFeedback | String | Email address to send logs and feedback. |
| isAutoScreenShareEnabled | Boolean | `True` if auto screen shared is enabled. |
| isBluetoothBeaconingEnabled | Boolean | `True` if Bluetooth beaconing is enabled. |
| isHideMeetingNamesEnabled | Boolean | `True` if hiding meeting names is enabled. |
| isSendLogsAndFeedbackEnabled | Boolean | `True` if sending logs and feedback is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkFeaturesConfiguration",
  "emailToSendLogsAndFeedback": "String",
  "isAutoScreenShareEnabled": "Boolean",
  "isBluetoothBeaconingEnabled": "Boolean",
  "isHideMeetingNamesEnabled": "Boolean",
  "isSendLogsAndFeedbackEnabled": "Boolean"
}
```
