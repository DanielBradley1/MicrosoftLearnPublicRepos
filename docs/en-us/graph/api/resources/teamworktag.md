<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# teamworkTag resource type

Namespace: microsoft.graph

Represents a tag associated with a team.

Tags provide a flexible way for customers to classify users or groups based on a common attribute within a team. For example, a Nurse, Manager, or Designer tag will enable users to reach groups of people in Teams without having to type every single name.

When a tag is added, users can @mention it in a channel. Everyone who has been assigned that tag receives a notification just as they would if they were @mentioned individually. Users can also use a tag to start a new chat with the members of that tag.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/teamworktag-list?view=graph-rest-1.0) | [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) collection | Get a list of the [tag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/teamworktag-post?view=graph-rest-1.0) | [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) | Create a standard [tag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) for members in a team. |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamworktag-get?view=graph-rest-1.0) | [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) | Read the properties and relationships of a [tag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/teamworktag-update?view=graph-rest-1.0) | [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) | Update the properties of a [tag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/teamworktag-delete?view=graph-rest-1.0) | None | Delete a [tag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0) object permanently. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the tag as it appears to the user in Microsoft Teams. A **teamworkTag** can't have more than 200 **teamworkTagMembers**. |
| displayName | String | The name of the tag as it appears to the user in Microsoft Teams. |
| id | String | The unique identifier for the tag. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| memberCount | Int32 | The number of users assigned to the tag. |
| tagType | [teamworkTagType](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0#teamworktagtype-values) | The type of the tag. Default is standard. |
| teamId | String | ID of the team in which the tag is defined. |

### teamworkTagType values

| Member | Description |
| :--- | :--- |
| standard | Default type for a tag. Tags of type standard can be managed in the team by members who have permissions. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| scheduled | Shift-based tag created and managed from the Shifts app. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) collection | Users assigned to the tag. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkTag",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "memberCount": "Int32",
  "tagType": "String",
  "teamId": "String"
}
```

## Related content

- [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0)
