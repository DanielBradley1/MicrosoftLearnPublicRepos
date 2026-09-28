<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkTagMember resource type

Namespace: microsoft.graph

Represents a user in a team to whom a tag is applied.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/teamworktagmember-list?view=graph-rest-1.0) | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) collection | Get a list of the [members](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) of a standard tag in a team and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/teamworktagmember-post?view=graph-rest-1.0) | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) | Create a new [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) object in a team. |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamworktagmember-get?view=graph-rest-1.0) | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) | Get the properties and relationships of a [member](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) of a standard tag in a team. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/teamworktagmember-delete?view=graph-rest-1.0) | None | Delete a [member](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) from a standard tag in a team. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The member's display name. |
| id | String | The unique identifier for the member. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| tenantId | String | The ID of the tenant that the tag member is a part of. |
| userId | String | The user ID of the member. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkTagMember",
  "displayName": "String",
  "id": "String (Identifier)",
  "tenantId": "String",
  "userId": "String"
}
```
