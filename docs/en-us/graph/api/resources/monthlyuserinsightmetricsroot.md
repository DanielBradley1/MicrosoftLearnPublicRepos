<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/monthlyuserinsightmetricsroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-18 -->

# monthlyUserInsightMetricsRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a container for summaries of monthly user activities on apps registered in your tenant that is configured for Microsoft Entra External ID for customers.

## Properties

None.

## Relationships

| Property | Type | Description |
| :--- | :--- | :--- |
| activeUsers | [activeUsersMetric](https://learn.microsoft.com/en-us/graph/api/resources/activeusersmetric?view=graph-rest-beta) collection | Insights for active users on apps registered in the tenant for a specified period. |
| authentications | [authenticationsMetric](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsmetric?view=graph-rest-beta) collection | Insights for authentications on apps registered in the tenant for a specified period. |
| mfaCompletions | [mfaCompletionMetric](https://learn.microsoft.com/en-us/graph/api/resources/mfacompletionmetric?view=graph-rest-beta) collection | Insights for MFA usage on apps registered in the tenant for a specified period. |
| requests | [userRequestsMetric](https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta) collection | Insights for all user requests on apps registered in the tenant for a specified period. |
| signUps | [userSignUpMetric](https://learn.microsoft.com/en-us/graph/api/resources/usersignupmetric?view=graph-rest-beta) collection | Total sign-ups on apps registered in the tenant for a specified period. |
| summary | [insightSummary](https://learn.microsoft.com/en-us/graph/api/resources/insightsummary?view=graph-rest-beta) collection | Summary of all usage insights on apps registered in the tenant for a specified period. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.monthlyUserInsightMetricsRoot"
}
```
