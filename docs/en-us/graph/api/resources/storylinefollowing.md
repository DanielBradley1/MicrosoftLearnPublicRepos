<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/storylinefollowing?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# storylineFollowing resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user that the specified user is following.

This resource is part of the user follow feature in employee engagement, enabling users to follow other users in their organization.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List followings](https://learn.microsoft.com/en-us/graph/api/storyline-list-followings?view=graph-rest-beta) | [storylineFollowing](https://learn.microsoft.com/en-us/graph/api/resources/storylinefollowing?view=graph-rest-beta) collection | Get a list of users that the specified user is following. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| following | [engagementIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/engagementidentityset?view=graph-rest-beta) | The identity information of the user being followed. |
| id | String | The unique identifier for the following relationship. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.storylineFollowing",
  "id": "String (identifier)",
  "following": {
    "@odata.type": "microsoft.graph.engagementIdentitySet"
  }
}
```
