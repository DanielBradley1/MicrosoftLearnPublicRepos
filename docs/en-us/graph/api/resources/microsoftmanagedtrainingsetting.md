<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftmanagedtrainingsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# microsoftManagedTrainingSetting resource type

Namespace: microsoft.graph

Represents a Microsoft managed training setting for simulation creation.

Inherits from [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completionDateTime | DateTimeOffset | The completion date for the training. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| settingType | trainingSettingType | The setting type. The possible values are: `microsoftCustom`, `microsoftManaged`, `noTraining`, `custom`, `unknownFutureValue`. Inherited from [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0). |
| trainingCompletionDuration | trainingCompletionDuration | The training completion duration that needs to be provided before scheduling the training. The possible values are: `week`, `fortnite`, `month`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftManagedTrainingSetting",
  "completionDateTime": "String (timestamp)",
  "settingType": "String",
  "trainingCompletionDuration": "String"
}
```
