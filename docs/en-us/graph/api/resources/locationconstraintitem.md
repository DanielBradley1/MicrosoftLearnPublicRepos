<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/locationconstraintitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# locationConstraintItem resource type

Namespace: microsoft.graph

The conditions stated by a client for the location of a meeting.

Derived from [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0).

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "resolveAvailability": true,
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "displayName": "string",
  "locationEmailAddress": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The street address of the location. |
| displayName | String | The name associated with the location. |
| locationEmailAddress | String | Optional email address of the location. |
| resolveAvailability | Boolean | If set to true and the specified resource is busy, [findMeetingTimes](https://learn.microsoft.com/en-us/graph/api/user-findmeetingtimes?view=graph-rest-1.0) looks for another resource that is free. If set to false and the specified resource is busy, **findMeetingTimes** returns the resource best ranked in the user's cache without checking if it's free. Default is true. |
