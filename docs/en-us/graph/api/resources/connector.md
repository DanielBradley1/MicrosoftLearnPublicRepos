<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-19 -->

# connector resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an Application Proxy connector. Connectors are lightweight agents that sit on-premises and facilitate the outbound connection to the [Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy) service. Each connector is part of a [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/connector-list?view=graph-rest-beta) | [connector](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta) collection | Retrieve a list of connector objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/connector-get?view=graph-rest-beta) | [connector](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta) | Read the properties and relationships of a connector object. |
| [List memberOf](https://learn.microsoft.com/en-us/graph/api/connector-list-memberof?view=graph-rest-beta) | [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) collection | List the **connectorGroup** object collection the connector is a member of. |
| [Add connector to connectorGroup](https://learn.microsoft.com/en-us/graph/api/connector-post-memberof?view=graph-rest-beta) | [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) | Add a connector to a **connectorGroup**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalIp | String | The external IP address as detected by the connector server. Read-only. |
| id | String | The unique identifier of the connector. Read-only. |
| machineName | String | The name of the computer on which the connector is installed and runs on. |
| status | connectorStatus | Indicates the status of the connector. The possible values are: `active`, `inactive`. Read-only. |
| version | String | The version of the connector. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| memberOf | [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) collection | The **connectorGroup** that the connector is a member of. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "externalIp": "String",
  "id": "String (identifier)",
  "machineName": "String",
  "status": "String",
  "version": "String"
}
```
