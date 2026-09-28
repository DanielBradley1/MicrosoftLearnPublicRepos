<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# connectorGroup resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Each [Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy) connector is always part of a connector group. All the connectors that belong to the same connector group act as a separate unit for high-availability and load balancing. If you don't create connector groups, all your connectors will be part of the default group. When configuring an application with Application Proxy, you must also specify which connector group to assign the application to.

After a connector group is created, you can add or move connectors to the connector group by using [Add connector](https://learn.microsoft.com/en-us/graph/api/connectorgroup-post-members?view=graph-rest-beta). You can also use [Add application](https://learn.microsoft.com/en-us/graph/api/connectorgroup-post-applications?view=graph-rest-beta) to assign an application to a connector group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/connectorgroup-list?view=graph-rest-beta) | [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) collection | Retrieve a list of connectorGroup objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/connectorgroup-post?view=graph-rest-beta) | [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) collection | Create a connectorGroup object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/connectorgroup-get?view=graph-rest-beta) | [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) | Read properties and relationships of a connectorGroup object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/connectorgroup-update?view=graph-rest-beta) | [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) | Update a connectorGroup object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/connectorgroup-delete?view=graph-rest-beta) | None | Delete a connectorGroup object. All connectors must be removed from the connectorGroup before a connectorGroup can be deleted. |
| [List members](https://learn.microsoft.com/en-us/graph/api/connectorgroup-list-members?view=graph-rest-beta) | [connector](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta) collection | Get a connector object collection. |
| [List applications](https://learn.microsoft.com/en-us/graph/api/connectorgroup-list-applications?view=graph-rest-beta) | [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) collection | Get the application object collection associated with the connectorGroup. |
| [Add application](https://learn.microsoft.com/en-us/graph/api/connectorgroup-post-applications?view=graph-rest-beta) | [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) | Associate an application with the connectorGroup by posting to the applications collection. |
| [Add connector](https://learn.microsoft.com/en-us/graph/api/connectorgroup-post-members?view=graph-rest-beta) | [connector](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta) | Add a connector to the connectorGroup by posting to the connectorGroup collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connectorGroupType | connectorGroupType | Indicates the type of hybrid agent. This pre-set by the system. The possible values are: `applicationProxy`, `syncFabric`. Read-only. |
| id | string | Unique identifier for this connectorGroup. Read-only. |
| isDefault | Boolean | Indicates if the connectorGroup is the default connectorGroup. Only a single connector group can be the default connectorGroup and this is pre-set by the system. Read-only. |
| name | string | The name associated with the connectorGroup. |
| region | connectorGroupRegion | The region the connectorGroup is assigned to and will optimize traffic for. This region can only be set if **no connectors or applications** are assigned to the connectorGroup. The possible values are: `nam` \(for **North America**\), `eur` \(for Europe\), `aus` \(for Australia\), `asia` \(for Asia\), `ind` \(for India\), and `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| applications | [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) collection | Read-only. Nullable. |
| members | [connector](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta) collection | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "isDefault": true,
  "name": "String",
  "region": "string"
}
```
