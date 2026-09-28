<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignedtraininginfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# assignedTrainingInfo resource type

Namespace: microsoft.graph

Represents assignment information of a training in an attack simulation and training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedUserCount | Int32 | Number of users who were assigned the training in an attack simulation and training campaign. |
| completedUserCount | Int32 | Number of users who completed the training in an attack simulation and training campaign. |
| displayName | String | Display name of the training in an attack simulation and training campaign. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.assignedTrainingInfo",
  "assignedUserCount": "Int32",
  "completedUserCount": "Int32",
  "displayName": "String"
}
```
