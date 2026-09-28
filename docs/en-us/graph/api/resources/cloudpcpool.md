<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcPool resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a pool for Cloud PC provisioning with common configurations and capabilities.

Base type of [cloudPcAgentPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpool?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-cloudpcpools?view=graph-rest-beta) | [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) collection | List the properties and relationships of the [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-cloudpcpools?view=graph-rest-beta) | [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) | Create a new [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpcpool-get?view=graph-rest-beta) | [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/cloudpcpool-update?view=graph-rest-beta) | None | Update the properties of a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/cloudpcpool-delete?view=graph-rest-beta) | None | Delete a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object. |
| [List assignments](https://learn.microsoft.com/en-us/graph/api/cloudpcpool-list-assignments?view=graph-rest-beta) | [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) collection | List the assignments of a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| [Create assignment](https://learn.microsoft.com/en-us/graph/api/cloudpcpool-post-assignments?view=graph-rest-beta) | [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) | Create a new [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) for a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [cloudPcPoolCapabilityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolcapabilityconfiguration?view=graph-rest-beta) | The capabilities configuration for the pool, including single sign-on settings. |
| cloudPcConfiguration | [cloudPcConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconfiguration?view=graph-rest-beta) | The Cloud PC specification, including image and operating system locale settings for provisioning. |
| createdDateTime | DateTimeOffset | The date and time when the pool was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2026 is `2026-01-01T00:00:00Z`. Read-only. |
| description | String | The description of the pool. The maximum length is 512 characters. |
| displayName | String | The display name of the pool. The name is unique across Cloud PC pools in an organization. The maximum length is 60 characters. |
| id | String | The unique identifier for the pool. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the pool was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2026 is `2026-01-01T00:00:00Z`. Read-only. |
| networkConfiguration | [cloudPcNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcnetworkconfiguration?view=graph-rest-beta) | The network configuration for the pool. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) collection | The collection of assignments that grant user or service principal identities access to this pool. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcPool",
  "capabilities": {
    "@odata.type": "microsoft.graph.cloudPcPoolCapabilityConfiguration"
  },
  "cloudPcConfiguration": {
    "@odata.type": "microsoft.graph.cloudPcConfiguration"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "networkConfiguration": {
    "@odata.type": "microsoft.graph.cloudPcNetworkConfiguration"
  }
}
```
