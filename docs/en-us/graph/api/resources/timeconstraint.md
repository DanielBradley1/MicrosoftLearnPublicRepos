<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timeconstraint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# timeConstraint resource type

Namespace: microsoft.graph

Restricts meeting time suggestions to certain hours and days of the week according to the specified nature of activity and open time slots.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "activityDomain": "String",
  "timeslots": [{"@odata.type": "microsoft.graph.timeSlot"}]
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityDomain | activityDomain | The nature of the activity, optional. The possible values are: `work`, `personal`, `unrestricted`, or `unknown`. |
| timeslots | [timeSlot](https://learn.microsoft.com/en-us/graph/api/resources/timeslot?view=graph-rest-1.0) collection | An array of time periods. |
