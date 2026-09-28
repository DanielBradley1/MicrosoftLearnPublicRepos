<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewapplyaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewApplyAction resource type

Namespace: microsoft.graph

In an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), the **applyActions** property of [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) configures the actions to take on reviewed users after an access review instance is completed. The following derived types are supported:

- [removeAccessApplyAction](https://learn.microsoft.com/en-us/graph/api/resources/removeaccessapplyaction?view=graph-rest-1.0) indicates removing access of an entity being reviewed upon completion of the review. This is the default type for the **applyActions** property of [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) and doesn't need to be specified.
- [disableAndDeleteUserApplyAction](https://learn.microsoft.com/en-us/graph/api/resources/disableanddeleteuserapplyaction?view=graph-rest-1.0) indicates disabling and deleting the user being reviewed upon completion of the review. This type must be explicitly specified in the **applyActions** property of [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewApplyAction"
}
```
