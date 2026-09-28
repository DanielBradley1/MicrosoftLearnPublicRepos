<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/disableanddeleteuserapplyaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# disableAndDeleteUserApplyAction resource type

Namespace: microsoft.graph

In an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), the **applyActions** property of [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) can use **disableAndDeleteUserApplyAction** to disable a denied B2B guest user for 30 days and then delete their account. This option doesn't contain any configuration options.

Inherits from [accessReviewApplyAction](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewapplyaction?view=graph-rest-1.0).

## Properties

None.

## Relationships

None.

## JSON representation

The following, is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.disableAndDeleteUserApplyAction"
}
```
