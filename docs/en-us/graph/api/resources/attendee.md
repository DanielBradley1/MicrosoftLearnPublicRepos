<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attendee?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# attendee resource type

Namespace: microsoft.graph

An event attendee that can be a person or resource such as a meeting room or equipment, that has been set up as a resource on the Exchange server for the tenant.

Derived from [attendeeBase](https://learn.microsoft.com/en-us/graph/api/resources/attendeebase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | Includes the name and SMTP address of the attendee. |
| proposedNewTime | [timeSlot](https://learn.microsoft.com/en-us/graph/api/resources/timeslot?view=graph-rest-1.0) | An alternate date/time proposed by the attendee for a meeting request to start and end. If the attendee hasn't proposed another time, then this property isn't included in a response of a GET event. |
| status | [ResponseStatus](https://learn.microsoft.com/en-us/graph/api/resources/responsestatus?view=graph-rest-1.0) | The attendee's response \(none, accepted, declined, etc.\) for the event and date-time that the response was sent. |
| type | String | The attendee type: `required`, `optional`, `resource`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "emailAddress": {"@odata.type": "microsoft.graph.emailAddress"},
  "proposedNewTime": {"@odata.type": "microsoft.graph.timeSlot"},
  "status": {"@odata.type": "microsoft.graph.responseStatus"},
  "type": "String"
}
```
