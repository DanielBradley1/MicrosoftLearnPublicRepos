<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-19 -->

# calendar resource type

Namespace: microsoft.graph

Represents a container for [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) resources. It can be a calendar for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), or the default calendar of a Microsoft 365 [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0).

> **Note:** There are a few minor differences in the way you can interact with user calendars and group calendars:

- You can organize only user calendars in a [calendarGroup](https://learn.microsoft.com/en-us/graph/api/resources/calendargroup?view=graph-rest-1.0).
- Outlook automatically accepts all meeting requests on behalf of groups. You can [accept](https://learn.microsoft.com/en-us/graph/api/event-accept?view=graph-rest-1.0), [tentatively accept](https://learn.microsoft.com/en-us/graph/api/event-tentativelyaccept?view=graph-rest-1.0), or [decline](https://learn.microsoft.com/en-us/graph/api/event-decline?view=graph-rest-1.0) meeting requests for user calendars only.
- Outlook doesn't support reminders for group events. You can [snooze](https://learn.microsoft.com/en-us/graph/api/event-snoozereminder?view=graph-rest-1.0) or [dismiss](https://learn.microsoft.com/en-us/graph/api/event-dismissreminder?view=graph-rest-1.0) a [reminder](https://learn.microsoft.com/en-us/graph/api/resources/reminder?view=graph-rest-1.0) for user calendars only.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/user-list-calendars?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) collection | Get all the user's calendars, or the calendars in the default or other specific calendar group. |
| [Create](https://learn.microsoft.com/en-us/graph/api/user-post-calendars?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Create a new calendar in the default calendar group or specified calendar group for a user. |
| [Get](https://learn.microsoft.com/en-us/graph/api/calendar-get?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Get the properties and relationships of a **calendar** object. The calendar can be one for a user or the default calendar of a Microsoft 365 group. |
| [Update](https://learn.microsoft.com/en-us/graph/api/calendar-update?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Update the properties of a **calendar** object. The calendar can be one for a user or the default calendar of a Microsoft 365 group. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/calendar-delete?view=graph-rest-1.0) | None | Delete calendar object. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/calendar-permanentdelete?view=graph-rest-1.0) | None | Permanently delete the **calendar** folder and remove it from the mailbox. |
| [List calendar view](https://learn.microsoft.com/en-us/graph/api/calendar-list-calendarview?view=graph-rest-1.0) | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection | Get the occurrences, exceptions, and single instances of events in a calendar view defined by a time range, from the user's primary calendar `(../me/calendarview)` or from a specified calendar. |
| [List events](https://learn.microsoft.com/en-us/graph/api/calendar-list-events?view=graph-rest-1.0) | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection | Retrieve a list of events in a calendar. The list contains single instance meetings and series masters. |
| [Create Event](https://learn.microsoft.com/en-us/graph/api/calendar-post-events?view=graph-rest-1.0) | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Create a new event in the default or specified calendar. |
| [Get free/busy schedule](https://learn.microsoft.com/en-us/graph/api/calendar-getschedule?view=graph-rest-1.0) | [scheduleInformation](https://learn.microsoft.com/en-us/graph/api/resources/scheduleinformation?view=graph-rest-1.0) collection | Get the free/busy availability information for a collection of users, distributions lists, or resources, for a specified time period. |
| [Find meeting times](https://learn.microsoft.com/en-us/graph/api/user-findmeetingtimes?view=graph-rest-1.0) | [meetingTimeSuggestionsResult](https://learn.microsoft.com/en-us/graph/api/resources/meetingtimesuggestionsresult?view=graph-rest-1.0) | Suggest meeting times and locations based on the organizer and attendee availability, and time or location constraints. |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Create one or more single-value extended properties in a new or existing calendar. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Get calendars that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Create one or more multi-value extended properties in a new or existing calendar. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Get a calendar that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedOnlineMeetingProviders | onlineMeetingProviderType collection | Represent the online meeting service providers that can be used to create online meetings in this calendar. The possible values are: `unknown`, `skypeForBusiness`, `skypeForConsumer`, `teamsForBusiness`. |
| canEdit | Boolean | `true` if the user can write to the calendar, `false` otherwise. This property is `true` for the user who created the calendar. This property is also `true` for a user who shared a calendar and granted write access. |
| canShare | Boolean | `true` if the user has permission to share the calendar, `false` otherwise. Only the user who created the calendar can share it. |
| canViewPrivateItems | Boolean | If `true`, the user can read calendar items that have been marked private, `false` otherwise. |
| changeKey | String | Identifies the version of the calendar object. Every time the calendar is changed, changeKey changes as well. This allows Exchange to apply changes to the correct version of the object. Read-only. |
| color | calendarColor | Specifies the color theme to distinguish the calendar from other calendars in a UI. The property values are: `auto`, `lightBlue`, `lightGreen`, `lightOrange`, `lightGray`, `lightYellow`, `lightTeal`, `lightPink`, `lightBrown`, `lightRed`, `maxColor`. |
| defaultOnlineMeetingProvider | onlineMeetingProviderType | The default online meeting provider for meetings sent from this calendar. The possible values are: `unknown`, `skypeForBusiness`, `skypeForConsumer`, `teamsForBusiness`. |
| hexColor | String | The calendar color, expressed in a hex color code of three hexadecimal values, each ranging from 00 to FF and representing the red, green, or blue components of the color in the RGB color space. If the user has never explicitly set a color for the calendar, this property is empty. Read-only. |
| id | String | The calendar's unique identifier. Read-only. |
| isDefaultCalendar | Boolean | `true` if this is the default calendar where new events are created by default, `false` otherwise. |
| isRemovable | Boolean | Indicates whether this user calendar can be deleted from the user mailbox. |
| isTallyingResponses | Boolean | Indicates whether this user calendar supports tracking of meeting responses. Only meeting invites sent from users' primary calendars support tracking of meeting responses. |
| name | String | The calendar name. |
| owner | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | If set, this represents the user who created or added the calendar. For a calendar that the user created or added, the **owner** property is set to the user. For a calendar shared with the user, the **owner** property is set to the person who shared that calendar with the user. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| calendarPermissions | [calendarPermission](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission?view=graph-rest-1.0) collection | The permissions of the users with whom the calendar is shared. |
| calendarView | [Event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection | The calendar view for the calendar. Navigation property. Read-only. |
| events | [Event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection | The events in the calendar. Navigation property. Read-only. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the calendar. Read-only. Nullable. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the calendar. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowedOnlineMeetingProviders": ["string"],
  "canEdit": "boolean",
  "canShare": "boolean",
  "canViewPrivateItems": "boolean",
  "changeKey": "string",
  "color": "String",
  "defaultOnlineMeetingProvider": "string",
  "hexColor": "String",
  "id": "string (identifier)",
  "isDefaultCalendar": "boolean",
  "isRemovable": "boolean",
  "isTallyingResponses": "boolean",
  "name": "string",
  "owner": {"@odata.type": "microsoft.graph.emailAddress"}
}
```
