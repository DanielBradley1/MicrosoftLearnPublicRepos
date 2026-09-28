<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# engagementRoleMember resource type

Namespace: microsoft.graph

Represents the role of member management in Viva Engage, which involves assigning and managing various administrative roles and the corporate communications role within the Viva Engage platform. Each role member links a predefined role to a specific user, and multiple users can be assigned to the same role.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/engagementrole-list-members?view=graph-rest-1.0) | [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) collection | Get a list of users with assigned [roles](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) in Viva Engage. |
| [Create](https://learn.microsoft.com/en-us/graph/api/engagementrole-post-members?view=graph-rest-1.0) | [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) | Create a new [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) object that assigns a Viva Engage role to a user. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/engagementrole-delete-members?view=graph-rest-1.0) | None | Delete a Viva Engage [role](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) from a user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the role was assigned to the user. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier of the **engagementRoleMember** object. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| userId | String | The Microsoft Entra ID of the user who has the role assigned. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| user | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The user who has this role assigned. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.engagementRoleMember",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "userId": "String"
}
```
