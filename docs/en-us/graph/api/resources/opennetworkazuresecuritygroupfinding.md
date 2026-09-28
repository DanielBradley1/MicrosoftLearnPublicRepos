<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/opennetworkazuresecuritygroupfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# openNetworkAzureSecurityGroupFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

View Azure open security groups.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/opennetworkazuresecuritygroupfinding-list?view=graph-rest-beta) | [openNetworkAzureSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/opennetworkazuresecuritygroupfinding?view=graph-rest-beta) collection | Get a list of the [openNetworkAzureSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/opennetworkazuresecuritygroupfinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/opennetworkazuresecuritygroupfinding-get?view=graph-rest-beta) | [openNetworkAzureSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/opennetworkazuresecuritygroupfinding?view=graph-rest-beta) | Read the properties and relationships of an [openNetworkAzureSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/opennetworkazuresecuritygroupfinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| inboundPorts | [inboundPorts](https://learn.microsoft.com/en-us/graph/api/resources/inboundports?view=graph-rest-beta) | Contains information on inbound ports related to an open security group. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| securityGroup | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) | Represents a resource in an authorization system. |
| virtualMachines | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) collection | Represents a virtual machine in an authorization system. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.openNetworkAzureSecurityGroupFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "inboundPorts": {
    "@odata.type": "microsoft.graph.inboundPorts"
  }
}
```
