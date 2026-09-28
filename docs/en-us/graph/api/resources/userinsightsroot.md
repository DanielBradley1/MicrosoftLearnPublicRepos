<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userinsightsroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# userInsightsRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A container for entities that represent summaries of daily and monthly user activities on apps registered in your tenant that is configured for Microsoft Entra External ID for customers.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| daily | [dailyUserInsightMetricsRoot](https://learn.microsoft.com/en-us/graph/api/resources/dailyuserinsightmetricsroot?view=graph-rest-beta) | Summaries of daily user activities on apps registered in your tenant that is configured for Microsoft Entra External ID for customers. |
| monthly | [monthlyUserInsightMetricsRoot](https://learn.microsoft.com/en-us/graph/api/resources/monthlyuserinsightmetricsroot?view=graph-rest-beta) | Summaries of monthly user activities on apps registered in your tenant that is configured for Microsoft Entra External ID for customers. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userInsightsRoot"
}
```
