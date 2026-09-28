<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissions-management-api-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# Discover, remediate, and monitor permissions in multicloud infrastructures using permissions management APIs \(preview\)

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

[Microsoft Entra Permissions Management](https://www.microsoft.com/en/security/business/identity-access/microsoft-entra-permissions-management) provides comprehensive visibility into permissions assigned to all identities across multiple cloud infrastructures such as Microsoft Azure, Amazon Web Services \(AWS\), and Google Cloud Platform \(GCP\). The permissions management APIs in Microsoft Graph provide the programmatic way to discover, manage, and monitor these permissions in your multicloud infrastructure.

This article introduces the Permissions Management capabilities that you can manage programmatically through Microsoft Graph.

For more information about Permissions Management, see [What's Microsoft Entra Permissions Management](https://learn.microsoft.com/en-us/entra/permissions-management/overview).

## Key use cases of permissions management APIs

By providing you with comprehensive visibility into permissions assigned to all identities across multiple clouds, permissions management APIs allows you to address three key use cases of Microsoft Entra Permissions Management: *discover*, *remediate*, and *monitor*.

## Authorization systems

An authorization system is a platform that contains identities and resources. It exposes permissions that control what resources an identity has access to and what actions they can perform.

Use the [authorizationSystem resource type](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) and its related methods to discover the authorization systems that are onboarded to Permissions Management and their details. Currently, Permissions Management supports Microsoft Azure, AWS, and GCP.

The following key API scenarios allow you to retrieve details for authorization systems.

| Description | APIs |
| --- | --- |
| Retrieve authorization systems | [List authorizationSystems](https://learn.microsoft.com/en-us/graph/api/externalconnectors-external-list-authorizationsystems?view=graph-rest-beta) |
| Get details for an AWS authorization system | [List awsAuthorizationSystems](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list?view=graph-rest-beta) |
| Get details for an Azure authorization system | [List azureAuthorizationSystems](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list?view=graph-rest-beta) |
| Get details for a GCP authorization system | [List gcpAuthorizationSystems](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list?view=graph-rest-beta) |

Discover the API operations quick reference for [AWS authorization systems](https://learn.microsoft.com/en-us/graph/permissions-management-how-to-authorization-system-aws), [Azure authorization systems](https://learn.microsoft.com/en-us/graph/permissions-management-how-to-authorization-system-azure), and [GCP authorization systems](https://learn.microsoft.com/en-us/graph/permissions-management-how-to-authorization-system-gcp).

## Authorization system inventory

Every authorization system has a defined set of objects that form the capabilities of the authorization system. For example, identities such as users and service accounts, or actions and resources.

The following key API scenarios allow you to retrieve the inventory for authorization systems.

| Description | APIs |
| --- | --- |
| List all identities in an authorization system | - [List all AWS identities](https://learn.microsoft.com/en-us/graph/api/awsassociatedidentities-list-all?view=graph-rest-beta)<br>- [List all Azure identities](https://learn.microsoft.com/en-us/graph/api/azureassociatedidentities-list-all?view=graph-rest-beta)<br>- [List all GCP identities](https://learn.microsoft.com/en-us/graph/api/azureassociatedidentities-list-all?view=graph-rest-beta) |
| List identity types in specific authorization systems | - List [roles](https://learn.microsoft.com/en-us/graph/api/awsassociatedidentities-list-roles?view=graph-rest-beta) and [users](https://learn.microsoft.com/en-us/graph/api/awsassociatedidentities-list-users?view=graph-rest-beta) in AWS<br>- List [managed identities](https://learn.microsoft.com/en-us/graph/api/azureassociatedidentities-list-managedidentities?view=graph-rest-beta), [users](https://learn.microsoft.com/en-us/graph/api/azureassociatedidentities-list-users?view=graph-rest-beta), and [service principals](https://learn.microsoft.com/en-us/graph/api/azureassociatedidentities-list-serviceprincipals?view=graph-rest-beta) in Azure<br>- List [users](https://learn.microsoft.com/en-us/graph/api/gcpassociatedidentities-list-users?view=graph-rest-beta), and [service accounts](https://learn.microsoft.com/en-us/graph/api/gcpassociatedidentities-list-serviceaccounts?view=graph-rest-beta) in GCP |
| Other inventory | - List [actions](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-actions?view=graph-rest-beta), [policies](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-policies?view=graph-rest-beta), [resources](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-resources?view=graph-rest-beta), and [services](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-services?view=graph-rest-beta) in AWS<br>- List [actions](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list-actions?view=graph-rest-beta), [resources](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list-resources?view=graph-rest-beta), [role definitions](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list-roledefinitions?view=graph-rest-beta), and [services](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list-services?view=graph-rest-beta) in Azure<br>- List [actions](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list-actions?view=graph-rest-beta), [resources](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list-resources?view=graph-rest-beta), [roles](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list-roles?view=graph-rest-beta), and [services](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list-services?view=graph-rest-beta) in GCP |

## Permissions requests

Identities can request for permissions against actions and resources in an authorization system. The permissions requests capabilities allow callers to request permissions for themselves or on behalf of another identity, and other identities to approve, reject, or cancel the requests.

The following key API scenarios allow you to implement permissions on demand capabilities.

| Scenarios | API |
| --- | --- |
| Request permissions; grant or reject a request | [Create scheduledPermissionsRequest](https://learn.microsoft.com/en-us/graph/api/permissionsmanagement-post-scheduledpermissionsrequests?view=graph-rest-beta) |
| Cancel a permissions request | [scheduledPermissionsRequest: cancelAll](https://learn.microsoft.com/en-us/graph/api/scheduledpermissionsrequest-cancelall?view=graph-rest-beta) |
| Track permissions requests and their status | [List permissionsRequestChanges](https://learn.microsoft.com/en-us/graph/api/permissionsmanagement-list-permissionsrequestchanges?view=graph-rest-beta) |

## Permissions analytics

Through the permissions analytics APIs, Permissions Management helps you discover permissions risk in identities and resources for your authorization systems. You can use these findings to automate use cases such as:

- Building dashboards
- Trigger a risk review
- Prioritize remediation
- Generate tickets

The following sample findings are available through the APIs:

| Finding | Sample scenarios API |  |
| --- | --- | --- |
| Inactive identities: Identities that haven't used any of their granted permissions in the last 90 days. | - [Inactive users across multiple authorization systems](https://learn.microsoft.com/en-us/graph/api/inactiveuserfinding-list?view=graph-rest-beta)<br>- [Inactive serverless functions across multiple authorization systems](https://learn.microsoft.com/en-us/graph/api/inactiveserverlessfunctionfinding-list?view=graph-rest-beta)<br>- [Inactive Azure service principals](https://learn.microsoft.com/en-us/graph/api/inactiveazureserviceprincipalfinding-list?view=graph-rest-beta)<br>- Inactive GCP service accounts<br>- [Inactive AWS roles](https://learn.microsoft.com/en-us/graph/api/inactiveawsrolefinding-list?view=graph-rest-beta)<br>- [Inactive AWS resources, such as ec2](https://learn.microsoft.com/en-us/graph/api/inactiveawsresourcefinding-list?view=graph-rest-beta) |  |
| Inactive groups: No identity has utilized the permissions assigned via the group over the last 90 days. | - [Inactive groups across multiple authorization systems](https://learn.microsoft.com/en-us/graph/api/inactivegroupfinding-list?view=graph-rest-beta) |  |
| Super identities: Administrator-level permissions across the authorization system. These identities can manage all the resources under the authorization system. | - [Super users across multiple authorization systems](https://learn.microsoft.com/en-us/graph/api/superuserfinding-list?view=graph-rest-beta)<br>- [Super serverless functions across multiple authorization systems](https://learn.microsoft.com/en-us/graph/api/superserverlessfunctionfinding-list?view=graph-rest-beta)<br>- [Super Azure service principals](https://learn.microsoft.com/en-us/graph/api/superazureserviceprincipalfinding-list?view=graph-rest-beta)<br>- [Super GCP service accounts](https://learn.microsoft.com/en-us/graph/api/supergcpserviceaccountfinding-list?view=graph-rest-beta)<br>- Super AWS roles<br>- [Super AWS resources, such as ec2](https://learn.microsoft.com/en-us/graph/api/superawsresourcefinding-list?view=graph-rest-beta) |  |

Other findings include:

- Resource-based findings: For example, Azure blob containers, S3 buckets and Storage buckets that are accessible publicly; open network security groups; and identities that can access secret information or utilize security tools
- Overprovisioned users, roles, resources, service principals, and service accounts
- Users with unenforced multifactor authentication in AWS
- Opportunities for privilege escalation
- AWS access key age and usage

---

## Zero Trust

This feature helps organizations to align their tenants with the three guiding principles of a Zero Trust architecture:

- Verify explicitly
- Use least privilege
- Assume breach

To find out more about Zero Trust and other ways to align your organization to the guiding principles, see the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/).

---

## Permissions and privileges

To call the permissions management APIs, the caller doesn't need any Microsoft Graph permissions. However, they must have appropriate privileges in the Microsoft Entra tenant and in the external system.

For more information, see [Permissions Management roles and permissions levels](https://learn.microsoft.com/en-us/entra/permissions-management/product-roles-permissions)

## Related content

- [What's Microsoft Entra Permissions Management](https://learn.microsoft.com/en-us/entra/permissions-management/overview)
- [Quickstart guide to Microsoft Entra Permissions Management](https://learn.microsoft.com/en-us/entra/permissions-management/permissions-management-quickstart-guide)
- [Microsoft Entra Permissions Management operations reference](https://learn.microsoft.com/en-us/entra/architecture/permissions-manage-ops-guide-intro)
- [Quick reference: Permissions Management API operations for Azure, AWS, and GCP authorization systems](https://learn.microsoft.com/en-us/graph/permissions-management-howto)
