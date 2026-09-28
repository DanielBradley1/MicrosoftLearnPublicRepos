<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-updatewindowsdeviceaccountactionparameter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# updateWindowsDeviceAccountActionParameter resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceAccount | [windowsDeviceAccount](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsdeviceaccount?view=graph-rest-1.0) |  |
| passwordRotationEnabled | Boolean |  |
| calendarSyncEnabled | Boolean |  |
| deviceAccountEmail | String |  |
| exchangeServer | String |  |
| sessionInitiationProtocalAddress | String |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.updateWindowsDeviceAccountActionParameter",
  "deviceAccount": {
    "@odata.type": "microsoft.graph.windowsDeviceAccount",
    "password": "String"
  },
  "passwordRotationEnabled": true,
  "calendarSyncEnabled": true,
  "deviceAccountEmail": "String",
  "exchangeServer": "String",
  "sessionInitiationProtocalAddress": "String"
}
```
