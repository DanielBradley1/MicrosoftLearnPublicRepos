<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/simulationreportoverview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# simulationReportOverview resource type

Namespace: microsoft.graph

Represents an overview report of an attack simulation and training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| recommendedActions | [recommendedAction](https://learn.microsoft.com/en-us/graph/api/resources/recommendedaction?view=graph-rest-1.0) collection | List of recommended actions for a tenant to improve its security posture based on the attack simulation and training campaign attack type. |
| resolvedTargetsCount | Int32 | Number of valid users in the attack simulation and training campaign. |
| simulationEventsContent | [simulationEventsContent](https://learn.microsoft.com/en-us/graph/api/resources/simulationeventscontent?view=graph-rest-1.0) | Summary of simulation events in the attack simulation and training campaign. |
| trainingEventsContent | [trainingEventsContent](https://learn.microsoft.com/en-us/graph/api/resources/trainingeventscontent?view=graph-rest-1.0) | Summary of assigned trainings in the attack simulation and training campaign. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.simulationReportOverview",
  "recommendedActions": [
    {
      "@odata.type": "microsoft.graph.recommendedAction"
    }
  ],
  "resolvedTargetsCount": "Int32",
  "simulationEventsContent": {
    "@odata.type": "microsoft.graph.simulationEventsContent"
  },
  "trainingEventsContent": {
    "@odata.type": "microsoft.graph.trainingEventsContent"
  }
}
```
