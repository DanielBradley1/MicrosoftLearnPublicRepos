<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworksystemconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# teamworkSystemConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the system configuration for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta). Not applicable for Microsoft Teams Rooms devices.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dateTimeConfiguration | [teamworkDateTimeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdatetimeconfiguration?view=graph-rest-beta) | The date and time configurations for a device. |
| defaultPassword | String | The default password for the device. Write-Only. |
| deviceLockTimeout | Duration | The device lock timeout in seconds. |
| isDeviceLockEnabled | Boolean | `True` if the device lock is enabled. |
| isLoggingEnabled | Boolean | `True` if logging is enabled. |
| isPowerSavingEnabled | Boolean | `True` if power saving is enabled. |
| isScreenCaptureEnabled | Boolean | `True` if screen capture is enabled. |
| isSilentModeEnabled | Boolean | `True` if silent mode is enabled. |
| language | String | The language option for the device. |
| lockPin | String | The pin that unlocks the device. Write-Only. |
| loggingLevel | String | The logging level for the device. |
| networkConfiguration | [teamworkNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworknetworkconfiguration?view=graph-rest-beta) | The network configuration for the device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkSystemConfiguration",
  "dateTimeConfiguration": {
    "@odata.type": "microsoft.graph.teamworkDateTimeConfiguration"
  },
  "defaultPassword": "String",
  "deviceLockTimeout": "String (duration)",
  "isDeviceLockEnabled": "Boolean",
  "isLoggingEnabled": "Boolean",
  "isPowerSavingEnabled": "Boolean",
  "isScreenCaptureEnabled": "Boolean",
  "isSilentModeEnabled": "Boolean",
  "language": "String",
  "lockPin": "String",
  "loggingLevel": "String",
  "networkConfiguration": {
    "@odata.type": "microsoft.graph.teamworkNetworkConfiguration"
  }
}
```
