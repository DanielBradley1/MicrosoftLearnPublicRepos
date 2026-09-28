<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcfrontlineserviceplan?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# cloudPcFrontLineServicePlan resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a service plan that provides an allotment of three Cloud PCs for the admin to provision for up to three users, but can't be assigned to a specific user. This service plan enables the service to create a concept of a time-share across these provisioned users, where customers can deploy a larger number of users. Windows 365 enforces a limit on active users at a given time, effectively creating an innovative way to provide the personalized experience of a Cloud PC along with the improved economics of sharing.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-frontlineserviceplans?view=graph-rest-beta) | [cloudPcFrontLineServicePlan](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcfrontlineserviceplan?view=graph-rest-beta) collection | Get a list of the [cloudPcFrontLineServicePlan](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcfrontlineserviceplan?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpcfrontlineserviceplan-get?view=graph-rest-beta) | [cloudPcFrontLineServicePlan](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcfrontlineserviceplan?view=graph-rest-beta) | Get the properties and relationships of a [cloudPcFrontLineServicePlan](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcfrontlineserviceplan?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the frontline service plan. For example, `2vCPU/8GB/128GB Front-line` or `4vCPU/16GB/256GB Front-line`. |
| id | String | The unique identifier \(ID\) of the frontline service plan. |
| totalCount | Int32 | The total number of frontline service plans purchased by the customer. |
| usedCount | Int32 | The number of service plans that have been used for the account. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcFrontLineServicePlan",
  "displayName": "String",
  "id": "String (identifier)",
  "usedCount": "Int32",
  "totalCount": "Int32"
}
```
