<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trainingeventscontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# trainingEventsContent resource type

Namespace: microsoft.graph

Represents training events in an attack simulation and training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTrainingsInfos | [assignedTrainingInfo](https://learn.microsoft.com/en-us/graph/api/resources/assignedtraininginfo?view=graph-rest-1.0) collection | List of assigned trainings and their information in an attack simulation and training campaign. |
| trainingsAssignedUserCount | Int32 | Number of users who were assigned trainings in an attack simulation and training campaign. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingEventsContent",
  "assignedTrainingsInfos": [
    {
      "@odata.type": "microsoft.graph.assignedTrainingInfo"
    }
  ],
  "trainingsAssignedUserCount": "Int32"
}
```
