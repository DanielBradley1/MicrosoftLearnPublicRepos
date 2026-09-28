<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontext?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerPlanContext resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerPlanContext** resource represents the relationship of a [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) to a user experience outside of Planner. Plans in Planner can be surfaced in other experiences, such as Microsoft Teams, to track work in the context of that experience. Experiences that have external links in the [plannerPlanContextDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontextdetails?view=graph-rest-beta) can be displayed in a user interface, allowing users to visit these experiences.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| associationType | String | Nullable. An app-defined type of association between the [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) and the app. The app can use this information to track different kinds of relationships to the same [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Read-only. The date and time when the **plannerPlanContext** was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayNameSegments | String collection | The segments of the name of the external experience. Segments represent a hierarchical structure that allows other apps to display the relationship. |
| isCreationContext | Boolean | Read-only. Indicates whether the plan is created from the specified context. Auto-generated based on whether the context is specified as part of plan creation. |
| ownerAppId | String | Read-only. ID of the app that created the **plannerPlanContext**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "associationType": "Board",
  "createdDateTime": "2015-10-14T00:57:28.4698344Z",
  "displayNameSegments": [
    "Finance Team",
    "Budget Plans"
  ],
  "isCreationContext": false,
  "ownerAppId": "5e3ce6c0-2b1f-4285-8d4b-75ee78787346"
}
```
