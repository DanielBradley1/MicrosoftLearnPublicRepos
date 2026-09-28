<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# educationOutcome resource type

Namespace: microsoft.graph

Represents a base class for the result of grading an assignment. The derived types are [educationFeedbackOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationfeedbackoutcome?view=graph-rest-1.0), [educationPointsOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationpointsoutcome?view=graph-rest-1.0), [educationRubricOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationrubricoutcome?view=graph-rest-1.0), and [educationFeedbackResourceOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationfeedbackresourceoutcome?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Update outcome](https://learn.microsoft.com/en-us/graph/api/educationoutcome-update?view=graph-rest-1.0) | [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) | Update the **educationOutcome** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **educationOutcome** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The individual who updated the resource. |
| lastModifiedDateTime | DateTimeOffset | The moment in time when the resource was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2021 is `2021-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)"
}
```
