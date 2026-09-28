<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# userRequestsMetric resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents daily and monthly insights on all user requests for apps registered in your tenant that is configured for Microsoft Entra External ID for customers, including all requests such as authentication requests, sign-up requests, and MFA requests. The user requests are aggregated without no filtering.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List daily](https://learn.microsoft.com/en-us/graph/api/dailyuserinsightmetricsroot-list-requests?view=graph-rest-beta) | [userRequestsMetric](https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta) collection | Get a list of daily [user requests](https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers. |
| [List monthly](https://learn.microsoft.com/en-us/graph/api/monthlyuserinsightmetricsroot-list-requests?view=graph-rest-beta) | [userRequestsMetric](https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta) collection | Get a list of monthly [user requests](https://learn.microsoft.com/en-us/graph/api/resources/userrequestsmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| factDate | Date | The date of the user insight. |
| id | String | Identifier for the user insight. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| requestCount | Int64 | Number of requests to the tenant. Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userRequestsMetric",
  "factDate": "String (date)",
  "id": "String (identifier)",
  "requestCount": "Int64"
}
```
