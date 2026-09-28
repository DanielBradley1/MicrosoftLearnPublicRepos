<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsanalyticsaggregation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsAnalyticsAggregation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents permissions analytics findings for authorization systems onboarded to Microsoft Entra Permissions Management. Currently, only AWS, Azure, and GCP are supported.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| aws | [permissionsAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/permissionsanalytics?view=graph-rest-beta) | AWS permissions analytics findings. |
| azure | [permissionsAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/permissionsanalytics?view=graph-rest-beta) | Azure permissions analytics findings. |
| gcp | [permissionsAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/permissionsanalytics?view=graph-rest-beta) | GCP permissions analytics findings. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsAnalyticsAggregation",
  "id": "String (identifier)"
}
```
