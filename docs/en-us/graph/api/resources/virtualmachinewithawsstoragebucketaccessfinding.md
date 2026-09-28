<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualmachinewithawsstoragebucketaccessfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# virtualMachineWithAwsStorageBucketAccessFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

View EC2 instances with S3 Bucket access.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List virtualMachineWithAwsStorageBucketAccessFinding objects](https://learn.microsoft.com/en-us/graph/api/virtualmachinewithawsstoragebucketaccessfinding-list?view=graph-rest-beta) | [virtualMachineWithAwsStorageBucketAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/virtualmachinewithawsstoragebucketaccessfinding?view=graph-rest-beta) collection | Get a list of the [virtualMachineWithAwsStorageBucketAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/virtualmachinewithawsstoragebucketaccessfinding?view=graph-rest-beta) objects and their properties. |
| [Get virtualMachineWithAwsStorageBucketAccessFinding](https://learn.microsoft.com/en-us/graph/api/virtualmachinewithawsstoragebucketaccessfinding-get?view=graph-rest-beta) | [virtualMachineWithAwsStorageBucketAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/virtualmachinewithawsstoragebucketaccessfinding?view=graph-rest-beta) | Read the properties and relationships of a [virtualMachineWithAwsStorageBucketAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/virtualmachinewithawsstoragebucketaccessfinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessibleCount | Int32 | The total number of storage buckets that the EC2 instance can access using the role. |
| bucketCount | Int32 | The total number of storage buckets in the authorization system that hosts the EC2 instance. |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| ec2Instance | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) | The AWS EC2 instance that is assigned using the role. |
| role | [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) | Represents an AWS role. Supports `$filter` as follows: `$filter=role/authorizationSystem/authorizationSystemId IN ('authorizationSystemIds')`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualMachineWithAwsStorageBucketAccessFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "bucketCount": "Integer",
  "accessibleCount": "Integer",
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  }
}
```
