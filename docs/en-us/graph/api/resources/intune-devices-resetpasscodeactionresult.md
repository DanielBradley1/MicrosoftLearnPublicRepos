<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-resetpasscodeactionresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# resetPasscodeActionResult resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Reset passcode action result

Inherits from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | String | Action name Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-1.0) |
| actionState | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-actionstate?view=graph-rest-1.0) | State of the action Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-1.0). The possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| startDateTime | DateTimeOffset | Time the action was initiated Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-1.0) |
| lastUpdatedDateTime | DateTimeOffset | Time the action state was last updated Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-1.0) |
| passcode | String | Newly generated passcode for the device |
| errorCode | Int32 | RotateBitLockerKeys action error code. Valid values 0 to 2147483647 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.resetPasscodeActionResult",
  "actionName": "String",
  "actionState": "String",
  "startDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)",
  "passcode": "String",
  "errorCode": 1024
}
```
