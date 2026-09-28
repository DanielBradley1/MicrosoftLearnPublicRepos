<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicyassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# cloudPcProvisioningPolicyAssignment resource type

Namespace: microsoft.graph

Represents a defined collection of provisioning policy assignments.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the provisioning policy assignment. If **target** is a user group, then the ID is shown as `{policyId_groupId}`. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| target | [cloudPcManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagementassignmenttarget?view=graph-rest-1.0) | The assignment target for the provisioning policy. Currently, the only target supported for this policy is a user group. For details, see [cloudPcManagementGroupAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagementgroupassignmenttarget?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignedUsers | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | The assignment targeted users for the provisioning policy. This list of users is computed based on assignments, licenses, group memberships, and policies. Read-only. Supports` $expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcProvisioningPolicyAssignment",
  "id": "String (identifier)",
  "target": {"@odata.type": "microsoft.graph.cloudPcManagementGroupAssignmentTarget"}
}
```
