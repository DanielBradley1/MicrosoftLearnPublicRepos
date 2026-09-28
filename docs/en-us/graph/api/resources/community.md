<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# community resource type

Namespace: microsoft.graph

Represents a community in Viva Engage that is a central place for conversations, files, events, and updates for people sharing a common interest or goal.

Every community is associated with a [Microsoft 365 group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0), but the group doesn't have the same ID as the community. For more information about managing communities in Viva Engage, see [Use the Microsoft Graph API to work with Viva Engage](https://learn.microsoft.com/en-us/graph/api/resources/engagement-api-overview?view=graph-rest-1.0).

This resource is an open type that allows additional properties beyond those documented here.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/employeeexperience-list-communities?view=graph-rest-1.0) | [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) collection | Get a list of the Viva Engage [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/employeeexperience-post-communities?view=graph-rest-1.0) | [engagementAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0) | Create a new [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) in Viva Engage. |
| [Get](https://learn.microsoft.com/en-us/graph/api/community-get?view=graph-rest-1.0) | [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) | Read the properties and relationships of a [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/community-update?view=graph-rest-1.0) | None | Update the properties of an existing Viva Engage [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/community-delete?view=graph-rest-1.0) | None | Delete a Viva Engage [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) along with all associated Microsoft 365 content, including the connected Microsoft 365 group, OneNote notebook, and Planner plans. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the community. The maximum length is 1,024 characters. |
| displayName | String | The name of the community. The maximum length is 255 characters. |
| groupId | String | The ID of the [Microsoft 365 group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) that manages the membership of this community. |
| id | String | The unique identifier of the community. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| privacy | [communityPrivacy](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0#communityprivacy-values) | Defines the privacy level of the community. The possible values are: `public`, `private`, `unknownFutureValue`. |

### communityPrivacy values

| Member | Description |
| :--- | :--- |
| public | Any user from the tenant can join and participate in the community. |
| private | A community administrator must add tenant users to the community before they can participate. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | The [Microsoft 365 group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) that manages the membership of this community. |
| owners | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | The admins of the community. Limited to 100 users. If this property isn't specified when you create the community, the calling user is automatically assigned as the community owner. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.community",
  "description": "String",
  "displayName": "String",
  "groupId": "String",
  "id": "String (identifier)",
  "privacy": "String"
}
```

## Related content

- [Use the Microsoft Graph API to work with Viva Engage](https://learn.microsoft.com/en-us/graph/api/resources/engagement-api-overview?view=graph-rest-1.0)
- [Create a community](https://learn.microsoft.com/en-us/graph/api/employeeexperience-post-communities?view=graph-rest-1.0)
