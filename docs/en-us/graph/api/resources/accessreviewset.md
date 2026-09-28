<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# accessReviewSet resource type

Namespace: microsoft.graph

Container for the base resources that expose the access reviews API and features.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitions | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) collection | Represents the template and scheduling for an access review. |
| historyDefinitions | [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) collection | Represents a collection of access review history data and the scopes used to collect that data. |
| unified | [unifiedRoot](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroot?view=graph-rest-1.0) | Entry point for the unified \(vNext\) access reviews API surface. Requests under this path are routed to the vNext service through the dedicated `accessReviews/unified` path segment. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewSet"
}
```
