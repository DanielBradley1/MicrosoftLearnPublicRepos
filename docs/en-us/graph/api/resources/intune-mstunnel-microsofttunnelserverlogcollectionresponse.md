<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# microsoftTunnelServerLogCollectionResponse resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that stores the server log collection status.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List microsoftTunnelServerLogCollectionResponses](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserverlogcollectionresponse-list?view=graph-rest-beta) | [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) collection | List properties and relationships of the [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) objects. |
| [Get microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserverlogcollectionresponse-get?view=graph-rest-beta) | [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) | Read properties and relationships of the [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) object. |
| [Create microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserverlogcollectionresponse-create?view=graph-rest-beta) | [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) | Create a new [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) object. |
| [Delete microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserverlogcollectionresponse-delete?view=graph-rest-beta) | None | Deletes a [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta). |
| [Update microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserverlogcollectionresponse-update?view=graph-rest-beta) | [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) | Update the properties of a [microsoftTunnelServerLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelserverlogcollectionresponse?view=graph-rest-beta) object. |
| [createDownloadUrl action](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserverlogcollectionresponse-createdownloadurl?view=graph-rest-beta) | String |  |
| [generateDownloadUrl action](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelserverlogcollectionresponse-generatedownloadurl?view=graph-rest-beta) | String |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for server log collection response. Read-only. |
| status | [microsoftTunnelLogCollectionStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnellogcollectionstatus?view=graph-rest-beta) | The status of log collection. Possible values are: pending, completed, failed. Possible values are: `pending`, `completed`, `failed`, `unknownFutureValue`. |
| startDateTime | DateTimeOffset | The start time of the logs collected |
| endDateTime | DateTimeOffset | The end time of the logs collected |
| sizeInBytes | Int64 | The size of the logs in bytes |
| serverId | String | ID of the server the log collection is requested upon |
| requestDateTime | DateTimeOffset | The time when the log collection was requested |
| expiryDateTime | DateTimeOffset | The time when the log collection is expired |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.microsoftTunnelServerLogCollectionResponse",
  "id": "String (identifier)",
  "status": "String",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "sizeInBytes": 1024,
  "serverId": "String",
  "requestDateTime": "String (timestamp)",
  "expiryDateTime": "String (timestamp)"
}
```
