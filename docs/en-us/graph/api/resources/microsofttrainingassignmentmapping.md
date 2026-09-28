<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsofttrainingassignmentmapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# microsoftTrainingAssignmentMapping resource type

Namespace: microsoft.graph

Represents a Microsoft training assignment mapping.

Inherits from [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | trainingAssignedTo collection | A user collection that specifies to whom the training should be assigned. The possible values are: `none`, `allUsers`, `clickedPayload`, `compromised`, `reportedPhish`, `readButNotClicked`, `didNothing`, `unknownFutureValue`. |
| settingType | trainingSettingType | Type of training setting. The possible values are: `microsoftCustom`, `microsoftManaged`, `noTraining`, `custom`, `unknownFutureValue`. Inherited from [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| training | [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) | Represents training details. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftTrainingAssignmentMapping",
  "assignedTo": ["String"],
  "settingType": "String"
}
```
