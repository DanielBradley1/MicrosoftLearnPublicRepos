<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attendeeavailability?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# attendeeAvailability resource type

Namespace: microsoft.graph

The availability of an attendee.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "attendee": {"@odata.type": "microsoft.graph.attendeeBase"},
  "availability": "String"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attendee | [attendeeBase](https://learn.microsoft.com/en-us/graph/api/resources/attendeebase?view=graph-rest-1.0) | The email address and type of attendee - whether it's a person or a resource, and whether required or optional if it's a person. |
| availability | freeBusyStatus | The availability status of the attendee. The possible values are: `free`, `tentative`, `busy`, `oof`, `workingElsewhere`, `unknown`. |
