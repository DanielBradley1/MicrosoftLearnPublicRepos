<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/calendargroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-08 -->

# calendarGroup resource type

Namespace: microsoft.graph

A group of user calendars.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List calendar groups](https://learn.microsoft.com/en-us/graph/api/user-list-calendargroups?view=graph-rest-1.0) | [Calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) collection | Get the user's calendar groups. |
| [Create calendar group](https://learn.microsoft.com/en-us/graph/api/user-post-calendargroups?view=graph-rest-1.0) | [Calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Create a new calendar group. |
| [Get calendar group](https://learn.microsoft.com/en-us/graph/api/calendargroup-get?view=graph-rest-1.0) | [calendarGroup](https://learn.microsoft.com/en-us/graph/api/resources/calendargroup?view=graph-rest-1.0) | Read properties and relationships of a calendar group object. |
| [Update calendar group](https://learn.microsoft.com/en-us/graph/api/calendargroup-update?view=graph-rest-1.0) | [calendarGroup](https://learn.microsoft.com/en-us/graph/api/resources/calendargroup?view=graph-rest-1.0) | Update calendarGroup object. |
| [Delete calendar group](https://learn.microsoft.com/en-us/graph/api/calendargroup-delete?view=graph-rest-1.0) | None | Delete calendarGroup object. |
| [List calendars in calendar group](https://learn.microsoft.com/en-us/graph/api/calendargroup-list-calendars?view=graph-rest-1.0) | [Calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) collection | List calendars in a calendar group. |
| [Create calendar in calendar group](https://learn.microsoft.com/en-us/graph/api/calendargroup-post-calendars?view=graph-rest-1.0) | [Calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Create a new Calendar in a calendar group. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The group name. |
| changeKey | String | Identifies the version of the calendar group. Every time the calendar group is changed, ChangeKey changes as well. This allows Exchange to apply changes to the correct version of the object. Read-only. |
| classId | Guid | The class identifier. Read-only. |
| id | String | The group's unique identifier. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| calendars | [Calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) collection | The calendars in the calendar group. Navigation property. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "changeKey": "string",
  "classId": "guid",
  "id": "string (identifier)",
  "name": "string"
}
```
