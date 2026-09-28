<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# microsoftTunnelSite resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents a Microsoft Tunnel site

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List microsoftTunnelSites](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelsite-list?view=graph-rest-beta) | [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta) collection | List properties and relationships of the [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta) objects. |
| [Get microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelsite-get?view=graph-rest-beta) | [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta) | Read properties and relationships of the [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta) object. |
| [Create microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelsite-create?view=graph-rest-beta) | [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta) | Create a new [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta) object. |
| [Delete microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelsite-delete?view=graph-rest-beta) | None | Deletes a [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta). |
| [Update microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelsite-update?view=graph-rest-beta) | [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta) | Update the properties of a [microsoftTunnelSite](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelsite?view=graph-rest-beta) object. |
| [requestUpgrade action](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelsite-requestupgrade?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the site id. $Insert, $skip, $top is not supported. Read-only. |
| displayName | String | The display name for the site. This property is required when a site is created. |
| description | String | The site's description \(optional\) |
| publicAddress | String | The site's public domain name or IP address |
| upgradeWindowUtcOffsetInMinutes | Int32 | The site's timezone represented as a minute offset from UTC |
| upgradeWindowStartTime | TimeOfDay | The site's upgrade window start time of day |
| upgradeWindowEndTime | TimeOfDay | The site's upgrade window end time of day |
| upgradeAutomatically | Boolean | The site's automatic upgrade setting. True for automatic upgrades, false for manual control |
| upgradeAvailable | Boolean | The site provides the state of when an upgrade is available |
| internalNetworkProbeUrl | String | The site's Internal Network Access Probe URL |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| microsoftTunnelConfiguration | [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) | The MicrosoftTunnelConfiguration that has been applied to this MicrosoftTunnelSite |
| microsoftTunnelServers | [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) collection | A list of MicrosoftTunnelServers that are registered to this MicrosoftTunnelSite |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.microsoftTunnelSite",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "publicAddress": "String",
  "upgradeWindowUtcOffsetInMinutes": 1024,
  "upgradeWindowStartTime": "String (time of day)",
  "upgradeWindowEndTime": "String (time of day)",
  "upgradeAutomatically": true,
  "upgradeAvailable": true,
  "internalNetworkProbeUrl": "String",
  "roleScopeTagIds": [
    "String"
  ]
}
```
