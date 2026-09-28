<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerfavoriteplanreference?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerFavoritePlanReference resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerFavoritePlanReference** resource type repesents a reference to a [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) that has been marked as a favorite by the user. Clients should note that **plannerFavoritePlanReference** entries can reference **plannerPlans** that are deleted, that the user can no longer access, or that have been updated with a different title.

We recommend that clients notify users when there are discrepancies and keep the entries up to date.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| orderHint | String | Hint used to order items of this type in a list view. The format is defined in [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-beta). |
| planTitle | String | Title of the plan at the time the user marked it as a favorite. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "orderHint": "String",
  "planTitle": "String"
}
```
