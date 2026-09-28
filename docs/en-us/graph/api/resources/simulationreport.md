<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/simulationreport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# simulationReport resource type

Namespace: microsoft.graph

Represents a report of an attack simulation and training campaign, including an overview and users who participated in the campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| overview | [simulationReportOverview](https://learn.microsoft.com/en-us/graph/api/resources/simulationreportoverview?view=graph-rest-1.0) | Overview of an attack simulation and training campaign. |
| simulationUsers | [userSimulationDetails](https://learn.microsoft.com/en-us/graph/api/resources/usersimulationdetails?view=graph-rest-1.0) collection | The tenant users and their online actions in an attack simulation and training campaign. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.simulationReport",
  "overview": {
    "@odata.type": "microsoft.graph.simulationReportOverview"
  },
  "simulationUsers": [
    {
      "@odata.type": "microsoft.graph.userSimulationDetails"
    }
  ]
}
```
