<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerteamspublicationinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-27 -->

# plannerTeamsPublicationInfo resource type

Namespace: microsoft.graph

Contains detailed information about the publication process that created a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). A publication process creates copies of tasks based on a template. These tasks are created in multiple plans, and have restricted permissions for the users; for example, they can't be deleted and users might be blocked from editing certain fields. Publication is used to distribute tasks across an organization and track their progress centrally.

Inherited from [plannerTaskCreation](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskcreation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| creationSourceKind | plannerCreationSourceKind | Specifies what kind of creation source the task is created with. The possible values are: `external`, `publication`, `unknownFutureValue`. The default value is `publication`. Inherited from [plannerTaskCreation](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskcreation?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when this task was last modified by the publication process. Read-only. |
| publicationId | String | The identifier of the publication. Read-only. |
| publicationName | String | The name of the published task list. Read-only. |
| publishedToPlanId | String | The identifier of the **plannerPlan** this task was originally placed in. Read-only. |
| publishingTeamId | String | The identifier of the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-beta) that initiated the publication process. Read-only. |
| publishingTeamName | String | The display name of the team that initiated the publication process. This display name is for reference only, and might not represent the most up-to-date name of the team. Read-only. |
| teamsPublicationInfo | [plannerTeamsPublicationInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerteamspublicationinfo?view=graph-rest-beta) | Information about the publication process that created this task. This field is deprecated and shouldn't be used in this resource type. Inherited from [plannerTaskCreation](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskcreation?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTeamsPublicationInfo",
  "creationSourceKind": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "publicationId": "String",
  "publicationName": "String",
  "publishedToPlanId": "String",
  "publishingTeamId": "String",
  "publishingTeamName": "String",
  "teamsPublicationInfo": {"@odata.type": "microsoft.graph.plannerTeamsPublicationInfo"}
}
```
