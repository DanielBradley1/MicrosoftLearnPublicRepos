<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplancreation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerPlanCreation resource type

Namespace: microsoft.graph

The resources that derive from plannerPlanCreation contain information about the origin of the [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta). Apps do not need to know the origin of the plan to be able to work with it; however, some apps can use the additional information to provide specific experiences around these plans. This is the abstract base type of [plannerExternalPlanSource](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalplansource?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| creationSourceKind | plannerCreationSourceKind | Specifies what kind of creation source the plan is created with. The possible values are: `external`, `publication` and `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerPlanCreation",
  "creationSourceKind": "String-value"
}
```
