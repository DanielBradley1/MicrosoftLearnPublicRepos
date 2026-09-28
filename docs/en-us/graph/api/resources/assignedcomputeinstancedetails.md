<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignedcomputeinstancedetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# assignedComputeInstanceDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the details of a list of S3 buckets associated with this EC2 instance.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/openawssecuritygroupfinding-list-assignedcomputeinstancesdetails?view=graph-rest-beta) | [assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/assignedcomputeinstancedetails?view=graph-rest-beta) collection | Get a list of the [assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/assignedcomputeinstancedetails?view=graph-rest-beta) objects and their properties. |
| [Get assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/assignedcomputeinstancedetails-get?view=graph-rest-beta) | [assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/assignedcomputeinstancedetails?view=graph-rest-beta) | Read the properties and relationships of an [assignedComputeInstanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/assignedcomputeinstancedetails?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessedStorageBuckets | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) collection | Represents a set of S3 buckets accessed by this EC2 instance. |
| assignedComputeInstance | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) | assigned EC2 instance. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.assignedComputeInstanceDetails",
  "id": "String (identifier)"
}
```
