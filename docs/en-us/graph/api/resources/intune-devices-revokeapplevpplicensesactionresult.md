<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-revokeapplevpplicensesactionresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# revokeAppleVppLicensesActionResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Revoke Apple Vpp licenses action result

Inherits from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | String | Action name Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta) |
| actionState | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-actionstate?view=graph-rest-beta) | State of the action Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta). Possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| startDateTime | DateTimeOffset | Time the action was initiated Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta) |
| lastUpdatedDateTime | DateTimeOffset | Time the action state was last updated Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta) |
| totalLicensesCount | Int32 | Total number of Apple Vpp licenses associated |
| failedLicensesCount | Int32 | Total number of Apple Vpp licenses that failed to revoke |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.revokeAppleVppLicensesActionResult",
  "actionName": "String",
  "actionState": "String",
  "startDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)",
  "totalLicensesCount": 1024,
  "failedLicensesCount": 1024
}
```
