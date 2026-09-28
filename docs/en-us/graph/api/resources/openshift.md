<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# openShift resource type

Namespace: microsoft.graph

Represents an unassigned, open shift in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

Inherits from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/openshift-list?view=graph-rest-1.0) | Collection of [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) | List the properties and relationships of **openShift** objects in a team. |
| [Create](https://learn.microsoft.com/en-us/graph/api/openshift-post?view=graph-rest-1.0) | [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) | Create an instance of an **openShift** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/openshift-get?view=graph-rest-1.0) | [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) | Read the properties and relationships of an **openShift** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/openshift-update?view=graph-rest-1.0) | [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) | Update an **openShift** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/openshift-delete?view=graph-rest-1.0) | None | Delete an **openShift** object. |
| [Stage for deletion](https://learn.microsoft.com/en-us/graph/api/changetrackedentity-stagefordeletion?view=graph-rest-1.0) | None | Stage the deletion of an [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) in draft mode. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the creator of the **openShift** object. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | Date and time when the **openShift** was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| draftOpenShift | [openShiftItem](https://learn.microsoft.com/en-us/graph/api/resources/openshiftitem?view=graph-rest-1.0) | Draft changes in the **openShift** are only visible to managers until they're [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). |
| id | String | Unique identifier for the **openShift** object. Read-only. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| isStagedForDeletion | Boolean | The **openShift** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user who last modified the **openShift** object. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | Date and time when the **openShift** was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [changeTrackedEntity](https://learn.microsoft.com/en-us/graph/api/resources/changetrackedentity?view=graph-rest-1.0). |
| schedulingGroupId | String | The ID of the [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) that contains the **openShift**. |
| sharedOpenShift | [openShiftItem](https://learn.microsoft.com/en-us/graph/api/resources/openshiftitem?view=graph-rest-1.0) | The shared version of this **openShift** that is viewable by both employees and managers. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.openShift",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "draftOpenShift": {"@odata.type": "microsoft.graph.openShiftItem"},
  "id": "String (identifier)",
  "isStagedForDeletion": "Boolean",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "schedulingGroupId": "String",
  "sharedOpenShift": {"@odata.type": "microsoft.graph.openShiftItem"}
}
```
