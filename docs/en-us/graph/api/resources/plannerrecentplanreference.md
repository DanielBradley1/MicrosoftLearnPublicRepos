<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerrecentplanreference?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerRecentPlanReference resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerRecentPlanReference** resource type repesents a reference to a [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) that has recently been viewed by a user. The **plannerRecentPlanReferences** for a user are explicitly maintained by apps. Any app that implements the recent plans feature should record when the user last viewed a plan, and update **plannerRecentPlanReference** entries accordingly. Apps should note that **plannerRecentPlanReference** entries can reference **plannerPlans** that are deleted, that the user can no longer access, or that have been updated with a different title. We recommend that apps notify users when there are discrepancies and keep the entries up to date.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastAccessedDateTime | DateTimeOffset | The date and time the plan was last viewed by the user. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| planTitle | String | The title of the plan at the time the user viewed it. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "lastAccessedDateTime": "String (timestamp)",
  "planTitle": "String"
}
```
