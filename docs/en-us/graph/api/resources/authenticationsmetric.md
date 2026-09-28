<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationsmetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# authenticationsMetric resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents insights of daily and monthly authentications on apps registered in your tenant that is configured for Microsoft Entra External ID for customers.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List daily](https://learn.microsoft.com/en-us/graph/api/dailyuserinsightmetricsroot-list-authentications?view=graph-rest-beta) | [authenticationsMetric](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsmetric?view=graph-rest-beta) collection | Get a list of daily [authentications](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsmetric?view=graph-rest-beta) on apps registered in your Microsoft Entra External ID for customers tenant. |
| [List monthly](https://learn.microsoft.com/en-us/graph/api/monthlyuserinsightmetricsroot-list-authentications?view=graph-rest-beta) | [authenticationsMetric](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsmetric?view=graph-rest-beta) collection | Get a list of monthly [authentications](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsmetric?view=graph-rest-beta) on apps registered in your tenant configured for Microsoft Entra External ID for customers. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appid | String | The ID of the Microsoft Entra application. Supports `$filter` \(`eq`\). |
| attemptsCount | Int64 | The number of authentication requests made in the specified period. Supports `$filter` \(`eq`\). |
| country | String | The location where the customers authenticated from. Supports `$filter` \(`eq`\). |
| factDate | Date | The date of the user insight. |
| id | String | Identifier for the user insight. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| os | String | The platform for the device that the customers used. Supports `$filter` \(`eq`\). |
| successCount | Int64 | Number of successful authentication requests. Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationsMetric",
  "appid": "String",
  "attemptsCount": "Int64",
  "country": "String",
  "factDate": "String (date)",
  "id": "String (identifier)",
  "os": "String",
  "successCount": "Int64"
}
```
