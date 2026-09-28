<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclienthealthstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# configurationManagerClientHealthState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Configuration manager client health state

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| state | [configurationManagerClientState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclientstate?view=graph-rest-beta) | Current configuration manager client state. Possible values are: `unknown`, `installed`, `healthy`, `installFailed`, `updateFailed`, `communicationError`. |
| errorCode | Int32 | Error code for failed state. |
| lastSyncDateTime | DateTimeOffset | Datetime for last sync with configuration manager management point. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.configurationManagerClientHealthState",
  "state": "String",
  "errorCode": 1024,
  "lastSyncDateTime": "String (timestamp)"
}
```
