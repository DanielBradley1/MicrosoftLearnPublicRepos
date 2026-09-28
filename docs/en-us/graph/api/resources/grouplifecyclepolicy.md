<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-27 -->

# groupLifecyclePolicy resource type

Namespace: microsoft.graph

Represents a lifecycle policy for a Microsoft 365 group. A group lifecycle policy allows administrators to set an expiration period for groups. For example, after 180 days, a group expires. When a group reaches its expiration, owners of the group are required to renew their group within a time interval defined by the administrator.

- Once renewed, the group expiration is extended by the number of days defined in the policy and the group's **expirationDateTime** property defines the new expiration date.
- If the group is not renewed, it expires and is deleted. The group can be restored within a period of 30 days from deletion.

For more information, see [Manage the lifecycle of Microsoft 365 groups in your tenant](https://learn.microsoft.com/en-us/entra/identity/users/groups-lifecycle).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/grouplifecyclepolicy-list?view=graph-rest-1.0) | [groupLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0) collection | List all the groupLifecyclePolicies. Only one policy exists in the |
| [Create](https://learn.microsoft.com/en-us/graph/api/grouplifecyclepolicy-post-grouplifecyclepolicies?view=graph-rest-1.0) | [groupLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0) | Create a new groupLifecyclePolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/grouplifecyclepolicy-get?view=graph-rest-1.0) | [groupLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0) | Read properties and relationships of a groupLifecyclePolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/grouplifecyclepolicy-update?view=graph-rest-1.0) | [groupLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0) | Update a groupLifecyclePolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/grouplifecyclepolicy-delete?view=graph-rest-1.0) | None | Delete a groupLifecyclePolicy object. |
| [Add group](https://learn.microsoft.com/en-us/graph/api/grouplifecyclepolicy-addgroup?view=graph-rest-1.0) | None | Add a group to a lifecycle policy |
| [Remove group](https://learn.microsoft.com/en-us/graph/api/grouplifecyclepolicy-removegroup?view=graph-rest-1.0) | None | Remove a group to a lifecycle policy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alternateNotificationEmails | String | List of email address to send notifications for groups without owners. Multiple email address can be defined by separating email address with a semicolon. |
| groupLifetimeInDays | Int32 | Number of days before a group expires and needs to be renewed. Once renewed, the group expiration is extended by the number of days defined. |
| id | String | A unique identifier for a policy. Read-only. |
| managedGroupTypes | String | The group type for which the expiration policy applies. Possible values are **All**, **Selected** or **None**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "alternateNotificationEmails": "String",
  "groupLifetimeInDays": 180,
  "id": "String (identifier)",
  "managedGroupTypes": "String"
}
```
