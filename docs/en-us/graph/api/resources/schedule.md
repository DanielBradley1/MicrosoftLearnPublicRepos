<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# schedule resource type

Namespace: microsoft.graph

A collection of [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) objects, [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) objects, [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) objects, and [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) objects within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create or replace](https://learn.microsoft.com/en-us/graph/api/team-put-schedule?view=graph-rest-1.0) | [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) | Create or replace a schedule. |
| [Get](https://learn.microsoft.com/en-us/graph/api/schedule-get?view=graph-rest-1.0) | [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) | Get a schedule. |
| [Share](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0) | None | Share a schedule time range with schedule members. |

## Properties

| Name | Type | Description |
| --- | --- | --- |
| enabled | Boolean | Indicates whether the schedule is enabled for the team. Required. |
| id | string | ID of the schedule. |
| isActivitiesIncludedWhenCopyingShiftsEnabled | Boolean | Indicates whether copied shifts include activities from the original shift. |
| offerShiftRequestsEnabled | Boolean | Indicates whether offer shift requests are enabled for the schedule. |
| openShiftsEnabled | Boolean | Indicates whether open shifts are enabled for the schedule. |
| provisionStatus | operationStatus | The status of the schedule provisioning. The possible values are `notStarted`, `running`, `completed`, `failed`. |
| provisionStatusCode | string | Additional information about why schedule provisioning failed. |
| startDayOfWeek | dayOfWeek | Indicates the start day of the week. The possible values are: `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`. |
| swapShiftsRequestsEnabled | Boolean | Indicates whether swap shifts requests are enabled for the schedule. |
| timeClockEnabled | Boolean | Indicates whether time clock is enabled for the schedule. |
| timeClockSettings | [timeClockSettings](https://learn.microsoft.com/en-us/graph/api/resources/timeclocksettings?view=graph-rest-1.0) | The time clock location settings for this schedule. |
| timeOffRequestsEnabled | Boolean | Indicates whether time off requests are enabled for the schedule. |
| timeZone | string | The time zone of the schedule team as an IANA time zone database \(tz database\) name; for example, `America/Chicago`. For the full list of valid values, see [List of tz database time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). Required. |
| workforceIntegrationIds | String collection | The IDs for the workforce integrations associated with this schedule. |

## Relationships

| Name | Type | Description |
| --- | --- | --- |
| dayNotes | [dayNote](https://learn.microsoft.com/en-us/graph/api/resources/daynote?view=graph-rest-1.0) collection | The day notes in the schedule. |
| offerShiftRequests | [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0) collection | The offer requests for shifts in the schedule. |
| openShiftChangeRequests | [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0) collection | The open shift requests in the schedule. |
| openShifts | [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) collection | The set of open shifts in a scheduling group in the schedule. |
| schedulingGroups | [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) collection | The logical grouping of users in the schedule \(usually by role\). |
| shifts | [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) collection | The shifts in the schedule. |
| swapShiftsChangeRequests | [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0) collection | The swap requests for shifts in the schedule. |
| timeCards | [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) collection | The time cards in the schedule. |
| timesOff | [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) collection | The instances of times off in the schedule. |
| timeOffReasons | [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) collection | The set of reasons for a time off in the schedule. |
| timeOffRequests | [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0) collection | The time off requests in the schedule. |
| workforceIntegrations | [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0) collection | An instance of a workforce integration per team with outbound data flow on synchronous change notifications \(for supported entities\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.schedule",
  "id": "String (identifier)",
  "enabled": "Boolean",
  "timeZone": "String",
  "provisionStatus": "String",
  "provisionStatusCode": "String",
  "workforceIntegrationIds": [
    "String"
  ],
  "timeClockEnabled": "Boolean",
  "timeClockSettings": {
    "@odata.type": "microsoft.graph.timeClockSettings"
  },
  "openShiftsEnabled": "Boolean",
  "swapShiftsRequestsEnabled": "Boolean",
  "offerShiftRequestsEnabled": "Boolean",
  "timeOffRequestsEnabled": "Boolean",
  "startDayOfWeek": "String",
  "isActivitiesIncludedWhenCopyingShiftsEnabled": "Boolean"
}
```
