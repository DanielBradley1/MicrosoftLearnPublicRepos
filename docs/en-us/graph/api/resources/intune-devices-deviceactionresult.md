<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# deviceActionResult resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device action result

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | String | Action name |
| actionState | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-actionstate?view=graph-rest-1.0) | State of the action. The possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| startDateTime | DateTimeOffset | Time the action was initiated |
| lastUpdatedDateTime | DateTimeOffset | Time the action state was last updated |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceActionResult",
  "actionName": "String",
  "actionState": "String",
  "startDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)"
}
```
