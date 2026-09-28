<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# schedulingGroup resource type

Namespace: microsoft.graph

A logical grouping of users in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) \(usually by role\).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/schedule-list-schedulinggroups?view=graph-rest-1.0) | [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) collection | Get the list of **schedulingGroups** in a schedule. |
| [Create](https://learn.microsoft.com/en-us/graph/api/schedule-post-schedulinggroups?view=graph-rest-1.0) | [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) | Create a new **schedulingGroup**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/schedulinggroup-get?view=graph-rest-1.0) | [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) | Get a **schedulingGroup** by ID. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/schedulinggroup-delete?view=graph-rest-1.0) | None | Mark **schedulingGroup** as inactive. |
| [Replace](https://learn.microsoft.com/en-us/graph/api/schedulinggroup-put?view=graph-rest-1.0) | [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) | Replace a **schedulingGroup**. |

## Properties

| Name | Type | Description |
| --- | --- | --- |
| code | `string` | The code for the `schedulingGroup` to represent an external identifier. This field must be unique within the team in Microsoft Teams and uses an alphanumeric format, with a maximum of 100 characters. |
| createdDateTime | `DateTimeOffset` | The time stamp in which this **schedulingGroup** was first created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | `string` | The display name for the **schedulingGroup**. Required. |
| id | `string` | ID of the **schedulingGroup**. |
| isActive | `bool` | Indicates whether the `schedulingGroup` can be used when creating new entities or updating existing ones. Required. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity that last updated this **schedulingGroup**. |
| lastModifiedDateTime | `DateTimeOffset` | The time stamp in which this **schedulingGroup** was last updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| userIds | `collection(string)` | The list of user IDs that are a member of the **schedulingGroup**. Required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string (identifier)",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "isActive": true,
  "userIds": ["String (identifier)"],
  "lastModifiedBy":{"@odata.type":"microsoft.graph.identitySet"},
  "code": "String"  
}
```
