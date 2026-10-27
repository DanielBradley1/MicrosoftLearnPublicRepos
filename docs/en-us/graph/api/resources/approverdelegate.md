<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approverdelegate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# approverDelegate resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the delegation of approval responsibilities from one user to another user or group, for a specified period of time.

An approver delegate applies across all [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-beta) access package assignment requests and all [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta) that are assigned to the user. While the delegation is in effect, the delegate can approve or deny on behalf of the user, and the user can still approve or deny their own pending items.

This resource is configured in the **approverDelegate** property of [identityGovernanceUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernanceusersettings?view=graph-rest-beta), which is exposed through the **identityGovernance** property of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) resource. Users can manage their own approver delegate through the `/me/identityGovernance/approverDelegate` path, and administrators can manage the approver delegate of any user through the `/users/{user-id}/identityGovernance/approverDelegate` path.

## Methods

None.

To manage the approver delegate of a user, use the [Get approverDelegate](https://learn.microsoft.com/en-us/graph/api/approverdelegate-get?view=graph-rest-beta) and [Update approverDelegate](https://learn.microsoft.com/en-us/graph/api/approverdelegate-update?view=graph-rest-beta) methods on the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) resource.

There's no delete operation. To stop a delegation, use the update operation to submit a schedule that has already expired.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| delegate | [userSet](https://learn.microsoft.com/en-us/graph/api/resources/userset?view=graph-rest-beta) | The user or group that receives the approval delegation. Only the [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-beta) and [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-beta) subtypes are supported. |
| schedule | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-beta) | The period during which the delegation is in effect, expressed as a start date and an expiration pattern. If you don't specify a schedule, the delegation starts immediately and doesn't expire. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approverDelegate",
  "delegate": {
    "@odata.type": "microsoft.graph.userSet"
  },
  "schedule": {
    "@odata.type": "microsoft.graph.requestSchedule"
  }
}
```
