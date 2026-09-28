<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskcreation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# plannerTaskCreation resource type

Namespace: microsoft.graph

The resources that derive from plannerPlanCreation contain information about the origin of the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). Apps do not need to know the origin of the task to be able to work with it; however, some apps can use the additional information to provide specific experiences around these tasks. This is the base type of [plannerTeamsPublicationInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerteamspublicationinfo?view=graph-rest-beta) and [plannerExternalTaskSource](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternaltasksource?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| teamsPublicationInfo | [plannerTeamsPublicationInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerteamspublicationinfo?view=graph-rest-beta) | Information about the publication process that created this task. This field is deprecated and clients should move to using the new inheritance model. |
| creationSourceKind | plannerCreationSourceKind | Specifies what kind of creation source the task is created with. The possible values are: `external`, `publication` and `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskCreation",
  "teamsPublicationInfo": {
    "@odata.type": "microsoft.graph.plannerTeamsPublicationInfo"
  },
  "creationSourceKind": "String-value"
}
```
