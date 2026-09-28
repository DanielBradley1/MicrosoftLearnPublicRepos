<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# externalGroup resource type

Namespace: microsoft.graph.externalConnectors

Represents a non-Microsoft Entra group.

External groups determine permissions to the content in your external data source. These external groups can be used in entries on the [acl](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) of an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0).

Examples of external groups are business units and work teams.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-post-groups?view=graph-rest-1.0) | [microsoft.graph.externalConnectors.externalGroup](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup?view=graph-rest-1.0) | Create a new **externalGroup** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalgroup-get?view=graph-rest-1.0) | [microsoft.graph.externalConnectors.externalGroup](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup?view=graph-rest-1.0) | Get an **externalGroup** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalgroup-update?view=graph-rest-1.0) | [microsoft.graph.externalConnectors.externalGroup](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup?view=graph-rest-1.0) | Update the properties of an **externalGroup** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalgroup-delete?view=graph-rest-1.0) | None | Delete an **externalGroup** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the external group. Optional. |
| displayName | String | The friendly name of the external group. Optional. |
| id | String | The unique ID of the external group within a connection. It must be alphanumeric and can be up to 128 characters long. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [microsoft.graph.externalConnectors.identity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-identity?view=graph-rest-1.0) collection | A member added to an **externalGroup**. You can add Microsoft Entra users, Microsoft Entra groups, or an **externalGroup** as members. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)"
}
```
