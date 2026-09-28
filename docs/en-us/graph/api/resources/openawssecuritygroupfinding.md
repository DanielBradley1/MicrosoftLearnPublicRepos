<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/openawssecuritygroupfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# openAwsSecurityGroupFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

View AWS open security groups.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/openawssecuritygroupfinding-list?view=graph-rest-beta) | [openAwsSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/openawssecuritygroupfinding?view=graph-rest-beta) collection | Get a list of the [openAwsSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/openawssecuritygroupfinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/openawssecuritygroupfinding-get?view=graph-rest-beta) | [openAwsSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/openawssecuritygroupfinding?view=graph-rest-beta) | Read the properties and relationships of an [openAwsSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/openawssecuritygroupfinding?view=graph-rest-beta) object. |
| [List assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/openawssecuritygroupfinding-list-assignedcomputeinstancesdetails?view=graph-rest-beta) | [assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/assignedcomputeinstancedetails?view=graph-rest-beta) collection | Retrieve a list of compute instances for an AWS open security group finding. |
| [Get assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/assignedcomputeinstancedetails-get?view=graph-rest-beta) | [assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/assignedcomputeinstancedetails?view=graph-rest-beta) | Get the details of a compute instance for an AWS open security group finding. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| inboundPorts | [inboundPorts](https://learn.microsoft.com/en-us/graph/api/resources/inboundports?view=graph-rest-beta) | Contains information on inbound ports related to an open security group. Supports `$filter` \(`eq`\) `$select`. |
| totalStorageBucketCount | Int32 | The number of storage buckets accessed by the assigned compute instances. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignedComputeInstancesDetails | [assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/assignedcomputeinstancedetails?view=graph-rest-beta) collection | A set of AWS EC2 compute instances related to this open security group. |
| securityGroup | [awsAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemresource?view=graph-rest-beta) | Represents a resource in an AWS authorization system. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.openAwsSecurityGroupFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "totalStorageBucketCount": "Integer",
  "inboundPorts": {
    "@odata.type": "microsoft.graph.inboundPorts"
  }
}
```
