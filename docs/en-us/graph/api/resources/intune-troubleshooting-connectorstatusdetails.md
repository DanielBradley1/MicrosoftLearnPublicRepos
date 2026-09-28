<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-connectorstatusdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# connectorStatusDetails resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represent connector status

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connectorName | [connectorName](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-connectorname?view=graph-rest-beta) | Connector name. Possible values are: `applePushNotificationServiceExpirationDateTime`, `vppTokenExpirationDateTime`, `vppTokenLastSyncDateTime`, `windowsAutopilotLastSyncDateTime`, `windowsStoreForBusinessLastSyncDateTime`, `jamfLastSyncDateTime`, `ndesConnectorLastConnectionDateTime`, `appleDepExpirationDateTime`, `appleDepLastSyncDateTime`, `onPremConnectorLastSyncDateTime`, `googlePlayAppLastSyncDateTime`, `googlePlayConnectorLastModifiedDateTime`, `windowsDefenderATPConnectorLastHeartbeatDateTime`, `mobileThreatDefenceConnectorLastHeartbeatDateTime`, `chromebookLastDirectorySyncDateTime`, `futureValue`. |
| connectorInstanceId | String | Connector Instance Id |
| status | [connectorHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-connectorhealthstate?view=graph-rest-beta) | Connector health state. Possible values are: `healthy`, `warning`, `unhealthy`, `unknown`. |
| eventDateTime | DateTimeOffset | Event datetime |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.connectorStatusDetails",
  "connectorName": "String",
  "connectorInstanceId": "String",
  "status": "String",
  "eventDateTime": "String (timestamp)"
}
```
