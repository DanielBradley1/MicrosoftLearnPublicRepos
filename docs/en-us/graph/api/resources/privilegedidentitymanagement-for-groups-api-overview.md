<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagement-for-groups-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# Govern membership and ownership of groups by using PIM for Groups

With [Privileged Identity Management for groups \(PIM for Groups\)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/concept-pim-for-groups), you can govern how principals are assigned membership or ownership of [groups](https://learn.microsoft.com/en-us/graph/api/resources/groups-overview?view=graph-rest-1.0). Security and Microsoft 365 Groups are critical resources that you can use to provide access to Microsoft cloud resources like Microsoft Entra roles, Azure roles, Azure SQL, Azure Key Vault, Intune, and third-party applications. PIM for Groups gives you more control over how and when principals are members or owners of groups, and therefore have privileges granted through their group membership or ownership.

The PIM for Groups APIs in Microsoft Graph provide you with more governance over security and Microsoft 365 Groups, such as the following capabilities:

- Providing principals just-in-time membership or ownership of groups
- Assigning principals temporary membership or ownership of groups

This article introduces the governance capabilities of the APIs for PIM for Groups in Microsoft Graph.

## PIM for Groups APIs for managing active assignments of group owners and members

The PIM for Groups APIs in Microsoft Graph allow you to assign principals permanent or temporary and time-bound membership or ownership to groups.

The following table lists scenarios for using PIM for Groups APIs to manage active assignments for principals and the corresponding APIs to call.

| **Scenarios** | **API** |
| --- | --- |
| An administrator:<br><br><li>Assigns a principal active membership or ownership to a group </li><br><br><li> Renews, updates, extends, or removes a principal from their active membership or ownership to a group <br><br> A principal: </li><br><br><li> Performs just-in-time and time-bound activation of their <em>eligible</em> membership or ownership assignment for a group </li><br><br><li> Deactivates their eligible membership and ownership assignment it when they no longer need access </li><br><br><li> Deactivates, extends, or renews their own membership and ownership assignment</li> | [Create assignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-post-assignmentschedulerequests?view=graph-rest-1.0) |
| An administrator lists all requests for active membership and ownership assignments for a group | [List assignmentScheduleRequests](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentschedulerequests?view=graph-rest-1.0) |
| An administrator lists all active assignments, and requests for assignments to be created in the future, for membership and ownership for a group | [List assignmentSchedules](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentschedules?view=graph-rest-1.0) |
| An administrator lists all active membership and ownership assignments for a group | [List assignmentScheduleInstances](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentscheduleinstances?view=graph-rest-1.0) |
| An administrator queries a member and ownership assignment for a group and its details | [Get privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupassignmentschedulerequest-get?view=graph-rest-1.0) |
| A principal queries their membership or ownership assignment requests and the details  <br>  <br>An approver queries membership or ownership requests waiting for their approval and details of these requests | [privilegedAccessGroupAssignmentScheduleRequest: filterByCurrentUser](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupassignmentschedulerequest-filterbycurrentuser?view=graph-rest-1.0) |
| A principal cancels a membership or ownership assignment request they created | [privilegedAccessGroupAssignmentScheduleRequest: cancel](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupassignmentschedulerequest-cancel?view=graph-rest-1.0) |
| An approver gets details for approval request, including information about approval steps | [Get approval](https://learn.microsoft.com/en-us/graph/api/approval-get?view=graph-rest-1.0) |
| An approver approves or denies approval request by approving or denying approval step | [Update approvalStep](https://learn.microsoft.com/en-us/graph/api/approvalstage-update?view=graph-rest-1.0) |

## PIM for Groups APIs for managing eligible assignments of group owners and members

Your principals might not require permanent membership or ownership of groups because they don't need the privileges granted through the membership or ownership all the time. In this case, PIM for Groups allows you to make the principals eligible for the membership or ownership of the groups.

When a principal has an eligible assignment, they activate their assignment when they need the privileges granted through the groups to perform privileged tasks. An eligible assignment can be permanent or temporary. The activation is always time-bound for a maximum of eight hours. The principal can also extend or renew their membership or ownership of the group.

The following table lists scenarios for using PIM for Groups APIs to manage eligible assignments for principals and the corresponding APIs to call.

| **Scenarios** | **API** |
| --- | --- |
| An administrator:<br><br><li> Creates an eligible membership or ownership assignment for the group </li><br><br><li> Renews, updates, extends, or removes an eligible membership/ownership assignment for the group </li><br><br><li> Deactivates, extends, or renews their own membership/ownership eligibility</li> | [Create eligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-post-eligibilityschedulerequests?view=graph-rest-1.0) |
| An administrator queries all eligible membership or ownership requests and their details | [List eligibilityScheduleRequests](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-eligibilityschedulerequests?view=graph-rest-1.0) |
| An administrator queries an eligible membership or ownership request and its details | [Get eligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedulerequest-get?view=graph-rest-1.0) |
| An administrator cancels an eligible membership or ownership request they created | [privilegedAccessGroupEligibilityScheduleRequest:cancel](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedulerequest-cancel?view=graph-rest-1.0) |
| A principal queries their eligible membership or ownership request their details | [privilegedAccessGroupEligibilityScheduleRequest: filterByCurrentUser](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroupeligibilityschedulerequest-filterbycurrentuser?view=graph-rest-1.0) |

## Policy settings in PIM for Groups

PIM for Groups defines settings or rules that govern how principals can be assigned membership or ownership of security and Microsoft 365 Groups. Such rules include whether multifactor authentication \(MFA\), justification, or approval is required to activate an eligible membership or ownership for a group, or whether you can create permanent assignments or eligibilities for principals to the groups. You define the rules in policies, and you can apply a policy to a group.

In Microsoft Graph, you manage these rules through the [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) and the [unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment?view=graph-rest-1.0) resource types and their related methods.

For example, assume that by default, PIM for Groups doesn't allow permanent active membership and ownership assignments and defines a maximum of six months for active assignments. Attempting to create a [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) object without expiry date returns a `400 Bad Request` response code for violation of the expiration rule.

PIM for Groups allows you to configure various rules, including:

- Whether principals can be assigned permanent eligible assignments
- The maximum duration allowed for a group membership or ownership activation and whether justification or approval is required to activate eligible membership or ownership
- The users who are allowed to approve activation requests for a group membership or ownership
- Whether MFA is required to both activate and enforce a group membership or ownership assignment
- The principals who get notified of group membership or ownership activations

The following table lists scenarios for using PIM for Groups to manage rules and the APIs to call.

| Scenarios | API |
| --- | --- |
| Retrieve PIM for Groups policies and associated rules or settings | [List unifiedRoleManagementPolicies](https://learn.microsoft.com/en-us/graph/api/policyroot-list-rolemanagementpolicies?view=graph-rest-1.0) |
| Retrieve a PIM for Groups policy and its associated rules or settings | [Get unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-get?view=graph-rest-1.0) |
| Update a PIM for Groups policy on its associated rules or settings | [Update unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-update?view=graph-rest-1.0) |
| Retrieve the rules defined for a PIM for Groups policy | [List rules](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-list-rules?view=graph-rest-1.0) |
| Retrieve a rule defined for a PIM for Groups policy | [Get unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-get?view=graph-rest-1.0) |
| Update a rule defined for a PIM for Groups policy | [Update unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-update?view=graph-rest-1.0) |
| Get the details of all PIM for Groups policy assignments, including the policies and rules associated with the groups membership and ownership | [List unifiedRoleManagementPolicyAssignments](https://learn.microsoft.com/en-us/graph/api/policyroot-list-rolemanagementpolicyassignments?view=graph-rest-1.0) |
| Get the details of a PIM for Groups policy assignment, including the policy and rules associated with the groups membership or ownership | [Get unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyassignment-get?view=graph-rest-1.0) |

For more information about using Microsoft Graph to configure rules, see [Overview of rules in PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview). For examples of updating rules, see [Use PIM APIs in Microsoft Graph to update rules](https://learn.microsoft.com/en-us/graph/how-to-pim-update-rules).

## Onboarding groups to PIM for Groups

You can't explicitly onboard a group to PIM for Groups. When you request to add an assignment to a group by using [Create assignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-post-assignmentschedulerequests?view=graph-rest-1.0) or [Create eligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-post-eligibilityschedulerequests?view=graph-rest-1.0), or when you update the PIM policy \(role settings\) for a group by using [Update unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-update?view=graph-rest-1.0) or [Update unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-update?view=graph-rest-1.0), PIM automatically onboards the group if it wasn't onboarded before.

You can call the following APIs for both groups that are onboarded to PIM and groups that aren't onboarded to PIM yet. To reduce the chances of getting throttled, call these APIs only for groups that are onboarded to PIM.

- [List assignmentScheduleRequests](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentschedulerequests?view=graph-rest-1.0)
- [List assignmentSchedules](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentschedules?view=graph-rest-1.0)
- [List assignmentScheduleInstances](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-assignmentscheduleinstances?view=graph-rest-1.0)
- [List eligibilityScheduleRequests](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-eligibilityschedulerequests?view=graph-rest-1.0)
- [List eligibilitySchedules](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-eligibilityschedules?view=graph-rest-1.0)
- [List eligibilityScheduleInstances](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-eligibilityscheduleinstances?view=graph-rest-1.0)

After PIM onboards a group, the IDs of the PIM policies and policy assignments for the specific group change. To get the updated IDs, call the [Get unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-get?view=graph-rest-1.0) or [Get unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyassignment-get?view=graph-rest-1.0) API.

Once PIM onboards a group, you can't offboard it, but you can remove all eligible and time-bound assignments as necessary.

## PIM for Groups and the group object

You can use PIM for Groups to govern membership and ownership of any security and Microsoft 365 group, except dynamic groups and groups synchronized from on-premises. The group doesn't need to be role-assignable to enable it in PIM for Groups.

When you assign a principal *active* permanent or temporary membership or ownership of a group, or when they make a just-in-time activation:

- You see the principal's details when you query the **members** and **owners** relationships through the [List group members](https://learn.microsoft.com/en-us/graph/api/group-list-members?view=graph-rest-1.0) or [List group owners](https://learn.microsoft.com/en-us/graph/api/group-list-owners?view=graph-rest-1.0) APIs.
- You can remove the principal from the group by using the [Remove group owner](https://learn.microsoft.com/en-us/graph/api/group-delete-owners?view=graph-rest-1.0) or [Remove group member](https://learn.microsoft.com/en-us/graph/api/group-delete-members?view=graph-rest-1.0) APIs.
- If you track changes to the group by using the [Get delta](https://learn.microsoft.com/en-us/graph/api/group-delta?view=graph-rest-1.0) and [Get delta for directory objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-delta?view=graph-rest-1.0) functions, an `@odata.nextLink` contains the new member or owner.
- You see the changes to group **members** and **owners** made through PIM for Groups logged in Microsoft Entra audit logs, and you can read them through the [List directory audits](https://learn.microsoft.com/en-us/graph/api/directoryaudit-list?view=graph-rest-1.0) API.

When you assign a principal *eligible* permanent or temporary membership or ownership of a group, the members and owners relationships of the group aren't updated.

When a principal's *temporary active* membership or ownership of a group expires:

- The principal's details are automatically removed from the **members** and **owners** relationships.
- If you track changes to the group by using the [Get delta](https://learn.microsoft.com/en-us/graph/api/group-delta?view=graph-rest-1.0) and [Get delta for directory objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-delta?view=graph-rest-1.0) functions, an `@odata.nextLink` indicates the removed group member or owner.

## Zero Trust

This feature helps organizations to align their tenants with the three guiding principles of a Zero Trust architecture:

- Verify explicitly
- Use least privilege
- Assume breach

To find out more about Zero Trust and other ways to align your organization to the guiding principles, see the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/).

## Licensing

The tenant where you use Privileged Identity Management must have enough purchased or trial licenses. For more information, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals).

## Related content

- [Microsoft Entra security operations for Privileged Identity Management](https://learn.microsoft.com/en-us/azure/active-directory/architecture/security-operations-privileged-identity-management?source=docs#privileged-identity-management-alerts) in the Microsoft Entra architecture center
