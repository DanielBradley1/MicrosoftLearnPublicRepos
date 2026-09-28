<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# microsoftTunnelServer resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents a single Microsoft Tunnel server

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List microsoftTunnelServers](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-list?view=graph-rest-beta) | [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) collection | List properties and relationships of the [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) objects. |
| [Get microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-get?view=graph-rest-beta) | [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) | Read properties and relationships of the [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) object. |
| [Create microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-create?view=graph-rest-beta) | [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) | Create a new [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) object. |
| [Delete microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-delete?view=graph-rest-beta) | None | Deletes a [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta). |
| [Update microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-update?view=graph-rest-beta) | [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) | Update the properties of a [microsoftTunnelServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserver?view=graph-rest-beta) object. |
| [getHealthMetrics action](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-gethealthmetrics?view=graph-rest-beta) | [keyLongValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keylongvaluepair?view=graph-rest-beta) collection |  |
| [getHealthMetricTimeSeries action](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-gethealthmetrictimeseries?view=graph-rest-beta) | [metricTimeSeriesDataPoint](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-metrictimeseriesdatapoint?view=graph-rest-beta) collection |  |
| [createServerLogCollectionRequest action](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-createserverlogcollectionrequest?view=graph-rest-beta) | [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) |  |
| [generateServerLogCollectionRequest action](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserver-generateserverlogcollectionrequest?view=graph-rest-beta) | [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the managed server. This ID is assigned at registration time. Supports: $filter, $select, $top, $skip, $orderby. $search is not supported. Read-only. |
| displayName | String | The display name of the server. It is the same as the host name during registration and can be changed later. Supports: $filter, $select, $top, $skip, $orderby. $search is not supported. Max allowed length is 200 chars. |
| tunnelServerHealthStatus | [microsoftTunnelServerHealthStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverhealthstatus?view=graph-rest-beta) | Indicates the server's health Status as of the last evaluation time. Health is evaluated every 60 seconds, and the possible values are: unknown, healthy, unhealthy, warning, offline, upgradeInProgress, upgradeFailed. Supports: $filter, $select, $top, $skip, $orderby. $search is not supported. Read-only. Possible values are: `unknown`, `healthy`, `unhealthy`, `warning`, `offline`, `upgradeInProgress`, `upgradeFailed`, `unknownFutureValue`. |
| lastCheckinDateTime | DateTimeOffset | Indicates when the server last checked in. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Supports: $filter, $select, $top, $skip, $orderby. $search is not supported Read-only. |
| agentImageDigest | String | The digest of the current agent image running on this server. Supports: $filter, $select, $top, $skip, $orderby. $search is not supported. Read-only. |
| serverImageDigest | String | The digest of the current server image running on this server. Supports: $filter, $select, $top, $skip, $orderby. $search is not supported. Read-only. |
| deploymentMode | [microsoftTunnelDeploymentMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunneldeploymentmode?view=graph-rest-beta) | Microsoft Tunnel server deployment mode. The value is set when the server is registered. Possible values are standaloneRootful, standaloneRootless, podRootful, podRootless. Default value: standaloneRootful. Supports: $filter, $select, $top, $skip, $orderby. $search is not supported. Read-only. Possible values are: `standaloneRootful`, `standaloneRootless`, `podRootful`, `podRootless`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.microsoftTunnelServer",
  "id": "String (identifier)",
  "displayName": "String",
  "tunnelServerHealthStatus": "String",
  "lastCheckinDateTime": "String (timestamp)",
  "agentImageDigest": "String",
  "serverImageDigest": "String",
  "deploymentMode": "String"
}
```
