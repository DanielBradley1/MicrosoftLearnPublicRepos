<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-identity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# identity resource type \(external connectors\)

Namespace: microsoft.graph.externalConnectors

Represents an [identity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-identity?view=graph-rest-1.0) used to set permissions on external content added to Microsoft Graph.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalgroup-post-members?view=graph-rest-1.0) | [identity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-identity?view=graph-rest-1.0) | Create an [identity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-identity?view=graph-rest-1.0) resource for a new member in an [externalGroup](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalgroupmember-delete?view=graph-rest-1.0) | None | Delete an [identity](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-identity?view=graph-rest-1.0) resource to remove the corresponding member from an [externalGroup](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique ID of the identity. It would be the objectId property for Microsoft Entra users or groups and the **id** property of the **externalGroup** in the case of external groups. |
| type | microsoft.graph.externalConnectors.identityType | The type of identity. The possible values are: `user` or `group` for Microsoft Entra identities and `externalgroup` for groups in an external system. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "type": "String"
}
```
