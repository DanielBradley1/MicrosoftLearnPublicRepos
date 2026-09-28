<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/locationconstraint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# locationConstraint resource type

Namespace: microsoft.graph

The conditions stated by a client for the location of a meeting.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isRequired": true,
  "locations": [{"@odata.type": "microsoft.graph.locationConstraintItem"}],
  "suggestLocation": true
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isRequired | Boolean | The client requests the service to include in the response a meeting location for the meeting. If this is true and all the resources are busy, [findMeetingTimes](https://learn.microsoft.com/en-us/graph/api/user-findmeetingtimes?view=graph-rest-1.0) won't return any meeting time suggestions. If this is false and all the resources are busy, **findMeetingTimes** would still look for meeting times without locations. |
| locations | [locationConstraintItem](https://learn.microsoft.com/en-us/graph/api/resources/locationconstraintitem?view=graph-rest-1.0) collection | Constraint information for one or more locations that the client requests for the meeting. |
| suggestLocation | Boolean | The client requests the service to suggest one or more meeting locations. |
