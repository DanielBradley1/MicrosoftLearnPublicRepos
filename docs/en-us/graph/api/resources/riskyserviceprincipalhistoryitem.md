<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipalhistoryitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# riskyServicePrincipalHistoryItem resource type

Namespace: microsoft.graph

Represents the risk history of a Microsoft Entra service principal as determined by Microsoft Entra ID Protection. Inherits from [riskyServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipal?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List history](https://learn.microsoft.com/en-us/graph/api/riskyserviceprincipal-list-history?view=graph-rest-1.0) | [riskyServicePrincipalHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipalhistoryitem?view=graph-rest-1.0) collection | Get the risk history of a Microsoft Entra service principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | [riskServicePrincipalActivity](https://learn.microsoft.com/en-us/graph/api/resources/riskserviceprincipalactivity?view=graph-rest-1.0) | The activity related to service principal risk level change. |
| initiatedBy | bool | The identifier of the actor of the operation. |
| servicePrincipalId | string | The identifier of the service principal. |

## JSON representation

```json
{
    "servicePrincipalId": "String",
    "initiatedBy": "String",
    "activity": {"@odata.type": "microsoft.graph.riskServicePrincipalActivity"}
}
```
