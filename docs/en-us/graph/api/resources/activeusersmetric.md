<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/activeusersmetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# activeUsersMetric resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents insights of daily and monthly user activity on apps registered in your tenant that is configured for Microsoft Entra External ID for customers. The count value returned is calculated based on the total number of users who made at least one authentication request within a specific period. A user can be counted more that once if they use multiple device platforms or applications.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List daily](https://learn.microsoft.com/en-us/graph/api/dailyuserinsightmetricsroot-list-activeusers?view=graph-rest-beta) | [activeUsersMetric](https://learn.microsoft.com/en-us/graph/api/resources/activeusersmetric?view=graph-rest-beta) collection | Get a list of daily [active users](https://learn.microsoft.com/en-us/graph/api/resources/activeusersmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers. |
| [List monthly](https://learn.microsoft.com/en-us/graph/api/monthlyuserinsightmetricsroot-list-activeusers?view=graph-rest-beta) | [activeUsersMetric](https://learn.microsoft.com/en-us/graph/api/resources/activeusersmetric?view=graph-rest-beta) collection | Get a list of monthly [active users](https://learn.microsoft.com/en-us/graph/api/resources/activeusersmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| count | Int64 | The total number of users who made at least one authentication request within the specified time period. |
| factDate | Date | Date of the insight. |
| id | String | Identifier for the user insight. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.activeUsersMetric",
  "count": "Int64",
  "factDate": "String (date)",
  "id": "String (identifier)"
}
```
