<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# trainingSetting resource type

Namespace: microsoft.graph

An abstract type that represents a training setting for simulation creation.

Base type of [customTrainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/customtrainingsetting?view=graph-rest-1.0), [microsoftCustomTrainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/microsoftcustomtrainingsetting?view=graph-rest-1.0), [microsoftManagedTrainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/microsoftmanagedtrainingsetting?view=graph-rest-1.0), [microsoftTrainingAssignmentMapping](https://learn.microsoft.com/en-us/graph/api/resources/microsofttrainingassignmentmapping?view=graph-rest-1.0), and [noTrainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/notrainingsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingType | trainingSettingType | Type of setting. The possible values are: `microsoftCustom`, `microsoftManaged`, `noTraining`, `custom`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingSetting",
  "settingType": "String"
}
```
