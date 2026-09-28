<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attendeebase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# attendeeBase resource type

Namespace: microsoft.graph

The type of attendee.

Derived from [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0).

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "type": "String",
  "emailAddress": {"@odata.type": "microsoft.graph.emailAddress"}
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | Includes the name and SMTP address of the attendee. |
| type | attendeeType | The type of attendee. The possible values are: `required`, `optional`, `resource`. Currently if the attendee is a person, [findMeetingTimes](https://learn.microsoft.com/en-us/graph/api/user-findmeetingtimes?view=graph-rest-1.0) always considers the person is of the `Required` type. |
