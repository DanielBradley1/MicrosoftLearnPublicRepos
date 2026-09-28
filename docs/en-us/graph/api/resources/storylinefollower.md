<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/storylinefollower?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# storylineFollower resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user who is following a specified user.

This resource is part of the user follow feature in employee engagement, enabling users to follow other users in their organization.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List followers](https://learn.microsoft.com/en-us/graph/api/storyline-list-followers?view=graph-rest-beta) | [storylineFollower](https://learn.microsoft.com/en-us/graph/api/resources/storylinefollower?view=graph-rest-beta) collection | Get a list of users who are following a specified user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| follower | [engagementIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/engagementidentityset?view=graph-rest-beta) | The identity information of the user who is following. |
| id | String | The unique identifier for the follower relationship. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.storylineFollower",
  "id": "String (identifier)",
  "follower": {
    "@odata.type": "microsoft.graph.engagementIdentitySet"
  }
}
```
