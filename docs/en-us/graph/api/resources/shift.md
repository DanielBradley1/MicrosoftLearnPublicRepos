<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# shift resource type

Namespace: microsoft.graph

Represents a unit of scheduled work in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

The duration of a shift can't be less than 1 minute or longer than 24 hours.

Inherits from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/schedule-list-shifts?view=graph-rest-1.0) | [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) collection | Get the list of **shifts** in this schedule. |
| [Create](https://learn.microsoft.com/en-us/graph/api/schedule-post-shifts?view=graph-rest-1.0) | [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) | Create a new **shift**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/shift-get?view=graph-rest-1.0) | [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) | Get a **shift** by ID. |
| [Replace](https://learn.microsoft.com/en-us/graph/api/shift-put?view=graph-rest-1.0) | [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) | Replace a **shift**. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/shift-delete?view=graph-rest-1.0) | None | Delete a **shift** from the schedule. |
| [Stage for deletion](https://learn.microsoft.com/en-us/graph/api/changetrackedentity-stagefordeletion?view=graph-rest-1.0) | None | Stage the deletion of a [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) in draft mode. |

## Properties

| Name | Type | Description |
| --- | --- | --- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the creator of **shift** object. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time at which this **shift** was first created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| draftShift | [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0) | Draft changes in the **shift**. Draft changes are only visible to managers. The changes are visible to employees when they're [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0), which copies the changes from the **draftShift** to the **sharedShift** property. |
| id | String | ID of the **shift**. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| isStagedForDeletion | Boolean | The **shift** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity that last updated this **shift**. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time at which this **shift** was last updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| schedulingGroupId | String | ID of the scheduling group the **shift** is part of. Required. |
| sharedShift | [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0) | The shared version of this **shift** that is viewable by both employees and managers. Updates to the **sharedShift** property send notifications to users in the Teams client. |
| userId | String | ID of the user assigned to the **shift**. Required. |

## JSON representation

The following JSON representation shows the resource.

```json
{
  "@odata.type": "#microsoft.graph.shift",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "draftShift": {"@odata.type": "microsoft.graph.shiftItem"},
  "id": "String (identifier)",
  "isStagedForDeletion": "Boolean",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "schedulingGroupId": "String",
  "sharedShift": {"@odata.type": "microsoft.graph.shiftItem"},
  "userId": "String"
}
```
