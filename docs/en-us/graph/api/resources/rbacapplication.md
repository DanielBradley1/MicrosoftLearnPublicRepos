<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rbacapplication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# rbacApplication resource type

Namespace: microsoft.graph

Role management container for unified role definitions and role assignments for Microsoft 365 role-based access control \(RBAC\) providers. The role assignments support only a single principal and a single scope. Currently **directory** and **entitlementManagement** are the two RBAC providers supported.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleAssignments | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) collection | Resource to grant access to users or groups. |
| roleAssignmentScheduleInstances | [unifiedRoleAssignmentScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentscheduleinstance?view=graph-rest-1.0) collection | Instances for active role assignments. |
| roleAssignmentScheduleRequests | [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) collection | Requests for active role assignments to principals through PIM. |
| roleAssignmentSchedules | [unifiedRoleAssignmentSchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedule?view=graph-rest-1.0) collection | Schedules for active role assignment operations. |
| roleDefinitions | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) collection | Resource representing the roles allowed by RBAC providers and the permissions assigned to the roles. |
| roleEligibilityScheduleInstances | [unifiedRoleEligibilityScheduleInstance](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityscheduleinstance?view=graph-rest-1.0) collection | Instances for role eligibility requests. |
| roleEligibilityScheduleRequests | [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) collection | Requests for role eligibilities for principals through PIM. |
| roleEligibilitySchedules | [unifiedRoleEligibilitySchedule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedule?view=graph-rest-1.0) collection | Schedules for role eligibility operations. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.rbacApplication",
  "id": "String (identifier)"
}
```
