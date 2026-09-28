<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usertrainingeventinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# userTrainingEventInfo resource type

Namespace: microsoft.graph

Represents events of a training assigned to a user in an attack simulation and training campaign. Training events include assigning the training, updating the training in progress, and completing the training.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the training. |
| latestTrainingStatus | trainingStatus | Latest status of the training assigned to the user. The possible values are: `unknown`, `assigned`, `inProgress`, `completed`, `overdue`, `unknownFutureValue`. |
| trainingAssignedProperties | [userTrainingContentEventInfo](https://learn.microsoft.com/en-us/graph/api/resources/usertrainingcontenteventinfo?view=graph-rest-1.0) | Event details of the training when it was assigned to the user. |
| trainingCompletedProperties | [userTrainingContentEventInfo](https://learn.microsoft.com/en-us/graph/api/resources/usertrainingcontenteventinfo?view=graph-rest-1.0) | Event details of the training when it was completed by the user. |
| trainingUpdatedProperties | [userTrainingContentEventInfo](https://learn.microsoft.com/en-us/graph/api/resources/usertrainingcontenteventinfo?view=graph-rest-1.0) | Event details of the training when it was updated/in-progress by the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userTrainingEventInfo",
  "displayName": "String",
  "latestTrainingStatus": "String",
  "trainingAssignedProperties": {
    "@odata.type": "microsoft.graph.userTrainingContentEventInfo"
  },
  "trainingCompletedProperties": {
    "@odata.type": "microsoft.graph.userTrainingContentEventInfo"
  },
  "trainingUpdatedProperties": {
    "@odata.type": "microsoft.graph.userTrainingContentEventInfo"
  }
}
```
