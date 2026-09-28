<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagementgroupassignmenttarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# cloudPcManagementGroupAssignmentTarget resource type

Namespace: microsoft.graph

Represents an assignment target group.

Inherits from [cloudPcManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagementassignmenttarget?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupId | String | The ID of the target group for the assignment. |
| servicePlanId | String | The unique identifier for the service plan that indicates which size of the Cloud PC to provision for the user. Use a `null` value, when the **provisioningType** is `dedicated`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcManagementGroupAssignmentTarget",
  "groupId": "String",
  "servicePlanId": "String"
}
```
