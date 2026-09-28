<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/storyline?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# storyline resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user's storyline for following and engagement features. This resource enables users to follow other users in their organization and manage their following relationships.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Follow user](https://learn.microsoft.com/en-us/graph/api/storyline-follow?view=graph-rest-beta) | None | Follow a user in the organization. |
| [Unfollow user](https://learn.microsoft.com/en-us/graph/api/storyline-unfollow?view=graph-rest-beta) | None | Remove the specified user from the signed-in user's following list. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the storyline. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| followers | [storylineFollower](https://learn.microsoft.com/en-us/graph/api/resources/storylinefollower?view=graph-rest-beta) collection | The users who are following this user. |
| followings | [storylineFollowing](https://learn.microsoft.com/en-us/graph/api/resources/storylinefollowing?view=graph-rest-beta) collection | The users that this user is following. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.storyline",
  "id": "String (identifier)"
}
```
