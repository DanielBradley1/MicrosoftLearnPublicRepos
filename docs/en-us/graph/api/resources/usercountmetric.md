<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usercountmetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# userCountMetric resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents daily insights on the total number of users for apps registered in your tenant that is configured for Microsoft Entra External ID for customers.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List daily](https://learn.microsoft.com/en-us/graph/api/dailyuserinsightmetricsroot-list-usercount?view=graph-rest-beta) | [userCountMetric](https://learn.microsoft.com/en-us/graph/api/resources/usercountmetric?view=graph-rest-beta) collection | Get a list of daily [user count](https://learn.microsoft.com/en-us/graph/api/resources/usercountmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| count | Int64 | The total number of users in the tenant over time. |
| factDate | Date | The date of the insight. |
| id | String | Identifier for the insight. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userCountMetric",
  "count": "Int64",
  "factDate": "String (date)",
  "id": "String (identifier)",
}
```
