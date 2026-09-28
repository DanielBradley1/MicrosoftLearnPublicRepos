<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkonlinemeetinginfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkOnlineMeetingInfo resource type

Namespace: microsoft.graph

Represents details about an online meeting in Microsoft Teams.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| calendarEventId | String | The identifier of the calendar event associated with the meeting. |
| joinWebUrl | String | The URL that users click to join or uniquely identify the meeting. |
| organizer | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0) | The organizer of the meeting. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "calendarEventId": "string",
  "joinWebUrl": "string",
  "organizer": {"@odata.type": "microsoft.graph.teamworkUserIdentity"}
}
```

## Related content

- [Chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)
