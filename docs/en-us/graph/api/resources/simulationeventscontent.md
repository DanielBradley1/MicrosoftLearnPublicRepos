<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/simulationeventscontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# simulationEventsContent resource type

Namespace: microsoft.graph

Represents simulation events in an attack simulation and training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compromisedRate | Double | Actual percentage of users who fell for the simulated attack in an attack simulation and training campaign. |
| events | [simulationEvent](https://learn.microsoft.com/en-us/graph/api/resources/simulationevent?view=graph-rest-1.0) collection | List of simulation events in an attack simulation and training campaign. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.simulationEventsContent",
  "compromisedRate": "Double",
  "events": [
    {
      "@odata.type": "microsoft.graph.simulationEvent"
    }
  ]
}
```
