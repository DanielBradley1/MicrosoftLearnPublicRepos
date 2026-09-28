<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanageractionresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# configurationManagerActionResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Result of the ConfigurationManager action

Inherits from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | String | Action name Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta) |
| actionState | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-actionstate?view=graph-rest-beta) | State of the action Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta). Possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| startDateTime | DateTimeOffset | Time the action was initiated Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta) |
| lastUpdatedDateTime | DateTimeOffset | Time the action state was last updated Inherited from [deviceActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactionresult?view=graph-rest-beta) |
| actionDeliveryStatus | [configurationManagerActionDeliveryStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanageractiondeliverystatus?view=graph-rest-beta) | State of the action being delivered to on-prem server. Possible values are: `unknown`, `pendingDelivery`, `deliveredToConnectorService`, `failedToDeliverToConnectorService`, `deliveredToOnPremisesServer`. |
| errorCode | Int32 | Error code of Configuration Manager action from client |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.configurationManagerActionResult",
  "actionName": "String",
  "actionState": "String",
  "startDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)",
  "actionDeliveryStatus": "String",
  "errorCode": 1024
}
```
