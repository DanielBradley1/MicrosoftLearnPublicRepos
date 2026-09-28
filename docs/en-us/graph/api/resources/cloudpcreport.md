<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# cloudPcReport resource type

Namespace: microsoft.graph

Represents the Windows 365 Cloud PC-related reports.

Use a method in the [Methods](#methods) section to get the corresponding report data in the response.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Retrieve Cloud PC recommendation reports](https://learn.microsoft.com/en-us/graph/api/cloudpcreport-retrievecloudpcrecommendationreports?view=graph-rest-1.0) | Stream | Retrieve Cloud PC recommendation [reports](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreport?view=graph-rest-1.0) for usage optimization and cost savings. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the reports. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

### cloudPcRecommendationReportType values

| Member | Description |
| :--- | :--- |
| cloudPcUsageCategoryReport | Indicates the report that shows the usage of Cloud PCs along with their associated categories. The possible report columns for these categories are: `Undersized`, `Oversized`, `Rightsized`, or `Underutilized` based on usage. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcReport",
  "id": "String (identifier)"
}
```
