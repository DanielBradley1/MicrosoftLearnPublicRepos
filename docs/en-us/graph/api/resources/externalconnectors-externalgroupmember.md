<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroupmember?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# externalGroupMember resource type

Namespace: microsoft.graph.externalConnectors

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a member of an [externalGroup](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup?view=graph-rest-beta) used to set permissions on external content added to Microsoft Graph.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalgroup-post-members?view=graph-rest-beta) | [externalGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroupmember?view=graph-rest-beta) | Create a new **externalGroupMember** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalgroupmember-delete?view=graph-rest-beta) | None | Delete an **externalGroupMember** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique ID of the member. It would be the objectId for Microsoft Entra users or groups and the **id** property of the **externalGroup** for external groups. |
| type | microsoft.graph.externalConnectors.externalGroupMemberType | The type of member added to the external group. The possible values are: `user` or `group` when the **identitySource** is `azureActiveDirectory` and just `group` when the **identitySource** is `external`. |
| identitySource | microsoft.graph.externalConnectors.identitySourceType | The identity source that the member belongs to. The possible values are: `azureActiveDirectory`, `external`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "type": "String",
  "identitySource": "String"
}
```
