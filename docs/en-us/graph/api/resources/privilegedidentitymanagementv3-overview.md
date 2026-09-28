<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# Manage Microsoft Entra role assignments by using PIM APIs

[Privileged Identity Management \(PIM\)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure) is a feature of Microsoft Entra ID Governance that enables you to manage, control, and monitor access to important resources in your organization. One method through which principals such as users, groups, and service principals \(applications\) are granted access to important resources is through assignment of [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json).

The PIM for Microsoft Entra roles APIs allow you to govern privileged access and limit excessive access to Microsoft Entra roles. This article introduces the governance capabilities of PIM for Microsoft Entra roles APIs in Microsoft Graph.

Note

To manage Azure resource roles, use the [Azure Resource Manager APIs for PIM](https://learn.microsoft.com/en-us/rest/api/authorization/privileged-role-eligibility-rest-sample).

PIM APIs for managing security alerts for Microsoft Entra roles are available on the `/beta` endpoint only. For more information, see [Security alerts for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-beta#security-alerts-for-azure-ad-roles&preserve-view=true).

## Methods of assigning roles

PIM for Microsoft Entra roles provides two methods for assigning roles to principals:

- **Active role assignments**: A principal can have a permanent or temporary perpetually active role assignment.
- **Eligible role assignments**: A principal can be eligible for a role either permanently or temporarily. With eligible assignments, the principal activates their role - thereby creating a temporarily active role assignment - when they need to perform privileged tasks. The activation is always time-bound for a maximum of 8 hours but the maximum duration can be lowered in the role settings. The activation can also be renewed or extended.

## PIM APIs for managing active role assignments

PIM enables you to manage active role assignments by creating permanent assignments or temporary assignments. Use the [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) resource type and its related methods to manage role assignments.

Note

Use PIM to manage active role assignments instead of using the [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) or the [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) resource types to manage them directly.

The following table lists scenarios for using PIM to manage role assignments and the APIs to call.

| Scenarios | API |
| --- | --- |
| An administrator creates and assigns to a principal a permanent role assignment  <br>An administrator assigns to a principal a temporary role | [Create roleAssignmentScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0) |
| An administrator renews, updates, extends, or removes role assignments | [Create roleAssignmentScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0) |
| An administrator queries all role assignments and their details | [List roleAssignmentScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleassignmentschedulerequests?view=graph-rest-1.0) |
| An administrator queries a role assignment and its details | [Get unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentschedulerequest-get?view=graph-rest-1.0) |
| A principal queries their role assignments and the details | [unifiedRoleAssignmentScheduleRequest: filterByCurrentUser](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentschedulerequest-filterbycurrentuser?view=graph-rest-1.0) |
| A principal performs just-in-time and time-bound activation of their *eligible* role assignment | [Create roleAssignmentScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0) |
| A principal cancels a role assignment request they created | [unifiedRoleAssignmentScheduleRequest: cancel](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentschedulerequest-cancel?view=graph-rest-1.0) |
| A principal that activated their eligible role assignment deactivates it when they no longer need access | [Create roleAssignmentScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0) |
| A principal deactivates, extends, or renews their own role assignment. | [Create roleAssignmentScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0) |

## PIM APIs for managing role eligibilities

Your principals might not need permanent role assignments because they don't always require the privileges granted through the privileged role. In this case, PIM enables you to create role eligibilities and assign them to the principals. With role eligibilities, the principal activates the role when they need to perform privileged tasks. The activation is always time-bound for a maximum of eight hours. The principal can also be permanently or temporarily eligible for the role.

Use the [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) resource type and its related methods to manage role eligibilities.

The following table lists scenarios for using PIM to manage role eligibilities and the APIs to call.

| Scenarios | API |
| --- | --- |
| An administrator creates and assigns to a principal an eligible role  <br>An administrator assigns a temporary role eligibility to a principal | [Create roleEligibilityScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleeligibilityschedulerequests?view=graph-rest-1.0) |
| An administrator renews, updates, extends, or removes role eligibilities | [Create roleEligibilityScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleeligibilityschedulerequests?view=graph-rest-1.0) |
| An administrator queries all role eligibilities and their details | [List roleEligibilityScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleeligibilityschedulerequests?view=graph-rest-1.0) |
| An administrator queries a role eligibility and its details | [Get unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedulerequest-get?view=graph-rest-1.0) |
| An administrator cancels a role eligibility request they created | [unifiedRoleEligibilityScheduleRequest: cancel](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedulerequest-cancel?view=graph-rest-1.0) |
| A principal queries their role eligibilities and the details | [unifiedRoleEligibilityScheduleRequest: filterByCurrentUser](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedulerequest-filterbycurrentuser?view=graph-rest-1.0) |
| A principal deactivates, extends, or renews their own role eligibility. | [Create roleEligibilityScheduleRequests](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleeligibilityschedulerequests?view=graph-rest-1.0) |

## Role settings and PIM

Each Microsoft Entra role defines settings or rules. Such rules include whether multifactor authentication \(MFA\), justification, or approval is required to activate an eligible role, or whether you can create permanent assignments or eligibilities for principals to the role. These role-specific rules determine the settings you can apply while creating or managing role assignments and eligibilities through PIM.

In Microsoft Graph, you manage these rules through the [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) and the [unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment?view=graph-rest-1.0) resource types and their related methods.

For example, assume that by default, a role doesn't allow permanent active assignments and defines a maximum of 15 days for active assignments. Attempting to create a [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) object without expiry date returns a `400 Bad Request` response code for violation of the expiration rule.

With PIM, you can configure various rules, including:

- Whether principals can be assigned permanent eligible assignments
- The maximum duration allowed for a role activation and whether justification or approval is required to activate eligible roles
- The users who are allowed to approve activation requests for a Microsoft Entra role
- Whether MFA is required to both activate and enforce a role assignment
- The principals who get notified of role activations

The following table lists scenarios for using PIM to manage rules for Microsoft Entra roles and the APIs to call.

| Scenarios | API |
| --- | --- |
| Retrieve role management policies and associated rules or settings | [List unifiedRoleManagementPolicies](https://learn.microsoft.com/en-us/graph/api/policyroot-list-rolemanagementpolicies?view=graph-rest-1.0) |
| Retrieve a role management policy and its associated rules or settings | [Get unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-get?view=graph-rest-1.0) |
| Update a role management policy on its associated rules or settings | [Update unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-update?view=graph-rest-1.0) |
| Retrieve the rules defined for role management policy | [List rules](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-list-rules?view=graph-rest-1.0) |
| Retrieve a rule defined for a role management policy | [Get unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-get?view=graph-rest-1.0) |
| Update a rule defined for a role management policy | [Update unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-update?view=graph-rest-1.0) |
| Get the details of all role management policy assignments including the policies and rules or settings associated with the Microsoft Entra roles | [List unifiedRoleManagementPolicyAssignments](https://learn.microsoft.com/en-us/graph/api/policyroot-list-rolemanagementpolicyassignments?view=graph-rest-1.0) |
| Get the details of a role management policy assignment including the policy and rules or settings associated with the Microsoft Entra role | [Get unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyassignment-get?view=graph-rest-1.0) |

For more information about using Microsoft Graph to configure rules, see [Overview of rules for Microsoft Entra roles in PIM APIs](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview). For examples of updating rules, see [Use PIM APIs to update rules for Microsoft Entra ID roles](https://learn.microsoft.com/en-us/graph/how-to-pim-update-rules).

## Audit logs

Microsoft Entra audit logs record all activities made through PIM for Microsoft Entra roles. You can read these logs through the [List directory audits](https://learn.microsoft.com/en-us/graph/api/directoryaudit-list) API.

## Zero Trust

This feature helps organizations to align their tenants with the three guiding principles of a Zero Trust architecture:

- Verify explicitly
- Use least privilege
- Assume breach

To find out more about Zero Trust and other ways to align your organization to the guiding principles, see the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/).

## Licensing

The tenant where you use Privileged Identity Management must have enough purchased or trial licenses. For more information, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals).

## Related content

- To learn more about security operations, see [Microsoft Entra security operations for Privileged Identity Management](https://learn.microsoft.com/en-us/azure/active-directory/architecture/security-operations-privileged-identity-management?source=docs#privileged-identity-management-alerts) in the Microsoft Entra architecture center.
