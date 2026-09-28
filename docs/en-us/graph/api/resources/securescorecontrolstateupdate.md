<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolstateupdate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# secureScoreControlStateUpdate resource type

Namespace: microsoft.graph

Contains the history of the control states updated by the user \(control states include Default, Ignored, ThirdParty, Reviewed\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | Assigns the control to the user who will take the action. |
| comment | String | Provides optional comment about the control. |
| state | String | State of the control, which can be modified via a PATCH command \(for example, ignored, thirdParty\). |
| updatedBy | String | ID of the user who updated tenant state. |
| updatedDateTime | DateTimeOffset | Time at which the control state was updated. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "assignedTo": "String",
 "comment": "String",
 "state": "String",
 "updatedBy": "String",
 "updatedDateTime": "String (timestamp)"
}
```
