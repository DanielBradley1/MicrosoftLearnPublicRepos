<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/notrainingsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# noTrainingSetting resource type

Namespace: microsoft.graph

Represents a no-training setting for simulation creation.

Inherits from [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingType | trainingSettingType | The setting type. The possible values are: `microsoftCustom`, `microsoftManaged`, `noTraining`, `custom`, `unknownFutureValue`. Inherited from [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.noTrainingSetting",
  "settingType": "String"
}
```
