<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customtrainingsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# customTrainingSetting resource type

Namespace: microsoft.graph

Represents a custom training setting for simulation creation.

Inherits from [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | trainingAssignedTo collection | A user collection that specifies to whom the training should be assigned. The possible values are: `none`, `allUsers`, `clickedPayload`, `compromised`, `reportedPhish`, `readButNotClicked`, `didNothing`, `unknownFutureValue`. |
| description | String | The description of the custom training setting. |
| displayName | String | The display name of the custom training setting. |
| durationInMinutes | String | Training duration. |
| settingType | trainingSettingType | Training setting type. The possible values are: `microsoftCustom`, `microsoftManaged`, `noTraining`, `custom`, `unknownFutureValue`. Inherited from [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-1.0). |
| url | String | The training URL. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customTrainingSetting",
  "assignedTo": ["String"],
  "description": "String",
  "displayName": "String",
  "durationInMinutes": "String",
  "settingType": "String",
  "url": "String"
}
```
