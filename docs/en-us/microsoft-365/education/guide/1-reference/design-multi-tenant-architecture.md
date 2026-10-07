<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-multi-tenant-architecture -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Design a multi-tenant architecture for large institutions

A single-tenant architecture is recommended for smaller institutions. However, for organizations that have over 1 million users we recommend a multi-tenant architecture to mitigate performance issues and tenant limitations such as [Azure subscription and quotas](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits) and [Microsoft Entra service limits and restrictions](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-service-limits-restrictions).

## Design principles

When designing your multi-tenant architecture, consider the following design principles to reduce costs and increase efficiency and security:

- Reduce costs

  - Reduce reliance on on-premises infrastructure and multiple identity providers.
  - Enable users to unlock their account or reset passwords using self-service \(for example, [Microsoft Entra self-service password reset](https://learn.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-sspr)\).

- Increase efficiency

  - Standardize architecture, configurations, and processes across tenants to minimize administrative issues.
  - Minimize the need for users to move from one tenant to another.

- Increase security

  - Focus on ensuring student data is secure.
  - Follow the principle of least privilege: grant only those privileges necessary to perform needed tasks and implement Just in Time \(JIT\) access.
  - Enable external users access only through Entitlement Management or [Microsoft Entra B2B collaboration](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/what-is-b2b).
  - Delegate administration of specific tasks to specific users with Just Enough Access \(JEA\) to do the job.

## Common reasons for multiple tenants

We strongly recommend organizations with fewer than 1 million users create a single tenant unless other criteria indicate a need for multiple tenants. For organizations with 1 million or more user objects, we recommend multiple tenants using a regional approach.

Creating separate tenants has the following effects on your education environment.

- Administrative separation

  - May limit the impacts of an administrative security or operational error affecting critical resources.
  - May limit the impact of compromised administrator or user accounts.
  - Usage reports and audit logs are contained within a tenant.

- Resource separation

  - Student privacy. Student user objects are discoverable only within the tenant the object resides in.
  - Resource isolation. Resources in a separate tenant can't be discovered or enumerated by users and administrators in other tenants.
  - Object Footprint. Applications that write to Microsoft Entra ID and other Microsoft Online services through Microsoft Graph or other management interfaces can affect only resources in the local tenant.
  - Quotas. Consumption of tenant-wide [Azure Quotas and Limits](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits) is separated from consumption of the other tenants.

- Configuration separation

  - Provides a separate set of tenant-wide settings that can accommodate resources and trusting applications that have different configuration requirements.
  - Enables a new set of Microsoft Online services such as Office 365.

In addition to having more than 1 million users, the following considerations may lead to multiple tenants.

- Administrative considerations

  - You operate under regulations that constrain who can administer the environment based on criteria such as country of citizenship, country of residency, or clearance level.
  - You have compliance requirements such as student data privacy that require you to create identities in specific local regions.

- Resource considerations

  - You have resources, perhaps for research and development, that you must shield from discovery, enumeration, or takeover by existing administrators for regulatory or business critical reasons.
  - Development cycle of custom applications that can change data of users with MS Graph or similar APIs at scale \(for example applications that are granted Directory.ReadWrite.All\)

- Configuration considerations

  - Resources having requirements that conflict with existing tenant-wide security or collaboration postures such as allowed authentication types, device management policies, ability to self-service, or identity proofing for external identities.

## Determine multi-tenant approach

In this section, we consider a fictional university named School of Fine Arts with 2 million students in 100 schools throughout the United States. Across these schools, there are a total of 130,000 teachers and 30,000 full-time employees and staff.

We recommend a regional approach when deploying multiple tenants as follows:

1. Begin by dividing your student and educator community by geographical regions where each region contains less than 1 million users.
2. Create a Microsoft Entra tenant for each region.

   ![multi-tenant-approach.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-multi-tenant-architecture-1.png)

3. Provision staff, teachers, and students in their corresponding region to optimize collaboration experiences.

   ![provisioning in tenants.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-multi-tenant-architecture-2.png)

### Why use regions?

A regional approach is recommended to minimize the number of users moving across tenants. If you created a tenant for each school level \(for example grade schools, middle schools, and high schools\) you would have to migrate users at the end of every school year. If instead users remain in the same region, then you don't have to move them across tenants as their attributes change.

Other benefits of a regional approach include:

- Optimal collaboration within each region
- Minimal number of guest objects from other tenants are needed

When a tenant has more than 1 million users, management experiences and tools tend to degrade over time. Likewise, some end-user experiences like using the people picker becomes cumbersome and unreliable.

Smaller organizations that choose to deploy multiple tenants without a compelling reason unnecessarily increase their management overhead and the number of user migrations. Doing so also require steps to ensure collaboration experiences across tenants.

## Collaborate across tenants using Microsoft Entra B2B collaboration

[Microsoft Entra B2B collaboration](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/what-is-b2b) enables users to use one set of credentials to sign in to multiple tenants. For educational institutions, the benefits of B2B collaboration include:

- Centralized administration team managing multiple tenants
- Teacher collaboration across regions
- Onboarding parents and guardians with their own credentials
- External partnerships like contractors, or researchers

With B2B collaboration, a user account created in one tenant \(their home tenant\) is invited as a guest user to another tenant \(a resource tenant\) and the user can sign in using the credentials from their home tenant. Administrators can also use B2B collaboration to enable external users to sign in with their existing social or enterprise accounts by setting up federation with identity providers such as [Facebook](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/facebook-federation), [Microsoft accounts](https://support.microsoft.com/help/4558219/microsoft-account-what-is), [Google](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/google-federation), or an [enterprise identity provider](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/direct-federation).

### Members and guests

Users in a Microsoft Entra tenant are either members or guests based on their UserType property. By default, member users are those that are native to the tenant. A Microsoft Entra B2B collaboration user is added as a user with UserType = Guest by default. Guests have [limited permissions](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/users-default-permissions) in the directory and applications. For example, guest users can't browse information from the tenant beyond their own profile information. However, a guest user can retrieve information about another user by providing the User Principal Name \(UPN\) or objectId. A guest user can also read properties of groups they belong to, including group membership, regardless of the **Guest users permissions are limited** setting.

In some cases, a resource tenant might want to treat users from the home tenant as members instead of guests. If so, you can use the Microsoft Entra B2B Invitation Manager APIs to add or invite a user from the home tenant to the resource tenant as a member. For more information, see [Properties of a Microsoft Entra B2B collaboration user](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/user-properties).

## Centralized administration of multiple tenants

Onboard external identities using Microsoft Entra B2B. External identities can then be assigned privileged roles to manage Microsoft Entra tenants as members of a centralized IT team. You can also use Microsoft Entra B2B to create guest accounts for other staff members such as administrators at the regional or district level.

However, roles that are service-specific such as Exchange Administrator or SharePoint Administrator require a local account that is native to their tenant. ​

The following roles can be assigned to B2B accounts

- Application Administrator
- Application Developer
- Authentication Administrator
- B2C IEF Keyset Administrator
- B2C IEF Policy Administrator
- Cloud Application B2C IEF Policy Administrator
- Cloud Device B2C IEF Policy Administrator
- Conditional Access Administrator
- Device Administrators
- Device Join
- Device Users
- Directory Readers
- Directory Writers
- Directory Synchronization Accounts
- External ID User Flow Administrator
- External ID User Flow Attribute Administrator
- External Identity Provider
- Groups Administrator
- Guest Inviter
- Helpdesk Administrator
- Hybrid Identity Administrator
- Intune Service Administrator
- License Administrator
- Password Administrator
- Privileged Authentication Administrator
- Privileged Role Administrator
- Reports Reader
- Restricted Guest User
- Security Administrator
- Security Reader
- User Account Administrator
- Workplace Device Join

[Custom administrator roles in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/roles-custom-overview) surface the underlying permissions of the [built-in roles](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles), so that you can create and organize your own custom roles. This approach allows you to grant access in a more granular way than built-in roles, whenever they're needed.

Here's an example illustrating how administration would work for administrative roles that can be delegated and used across multiple tenants.

Susie’s native account is in the Region 1 tenant, and Microsoft Entra B2B is used to add the account as an Authentication Administrator to the central IT team in the tenants for Region 2 and Region 3.

![centralized administration.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-multi-tenant-architecture-3.png)

### Using apps across multiple tenants

To mitigate issues associated with the administration of apps in a multi-tenant environment, you should consider writing [multi-tenant apps](https://learn.microsoft.com/en-us/azure/active-directory/develop/setup-multi-tenant-app). You'll also need to verify which of your SaaS apps support multiple IdP connections. SaaS apps that support multiple IDP connections should configure individual connections on each tenant. SaaS apps that don't support multiple IDP connections might require independent instances. For more information, see [How to: Sign in any Microsoft Entra user using the multi-tenant application pattern](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant).

Note: Licensing models may vary from one SaaS app to another. check with the vendor to determine if multiple subscriptions will be required in a multi-tenant environment.

## Per-tenant administration

Per-tenant administration is required for roles that are service-specific. Roles that are service-specific require having a local account that is native to the tenant. In addition to having a centralized IT team in each tenant, you'll also need to have a regional IT team in each tenant to manage workloads such as Exchange, SharePoint, and Teams.

The following roles require accounts native to each tenant

- Azure DevOps Administrator
- Azure Information Protection Administrator
- Billing Administrator
- CRM Service Administrator
- Compliance Administrator
- Compliance Data Administrator
- Customer Lockbox Access Approver
- Desktop Analytics Administrator
- Exchange Administrator
- Insights Administrator
- Insights Business Leader
- Kaizala Administrator
- Lync Service Administrator
- Message Center Privacy Reader
- Message Center Reader
- Printer Administrator
- Printer Technician
- Search Administrator
- Search Editor
- Security Operator
- Service Support Administrator
- SharePoint Administrator
- Teams Communications Administrator
- Teams Communications Support Engineer
- Teams Communications Support Specialist
- Teams Service Administrator

Unique admins in each tenant

If you have an IT team native to each region, you could have one of those local administrators manage the Teams administration. In the following example, Charles resides in Region 1 tenant and has the role of Teams Service Administrator. Alice and Ichiro reside in regions 2 and 3 respectively, and hold the same role in their regions. Each local administrator has a single account native to their region.

![Picture 7.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-multi-tenant-architecture-4.png)

Admin roles across tenants

If you don't have a pool of admins local to each region, you might assign the Teams Service Administrator role to just one user. In this scenario, as illustrated below, you can have Bob from the Central IT Team act as Teams Service Administrator in all three tenants by creating a local account for Bob in each tenant.

![Picture 9.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-multi-tenant-architecture-5.png)

## Delegation of admin roles within a tenant

[Administrative units](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-administrative-units) \(AUs\) should be used to logically group Microsoft Entra users and groups. Restricting administrative scope using administrative units is useful in educational organizations that are made up of different regions, districts, or schools.

For example, our fictional School of Fine Arts is spread across three regions, each containing multiple schools. Each region has a team of IT admins who control access, manage users, and sets policies for their respective schools.

For example, an IT administrator could:

- Create an AU for users each of the schools in Region 1, to manage all users in that school. \(not pictured\)
- Create an AU that contains the teachers in each school, to manage teacher accounts.
- Create a separate AU that contains the students in each school, to manage student accounts.
- Assign teachers in the school the Password Administrator role for the Students AU, so that teachers can reset student passwords, but not reset other users’ passwords.

![Administrative units.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-multi-tenant-architecture-6.png)

Roles that can be scoped to administrative units include:

- Authentication Administrator
- Groups Administrator
- Helpdesk Administrator
- License Administrator
- Password Administrator
- User Administrator

For more information, see [Assign scoped roles to an administrative unit](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/roles-admin-units-assign-roles).

## Cross-tenant management

Settings are configured in each tenant individually. Configure them as part of the tenant creation where possible to help minimize having to revisit those settings. While some common tasks can be automated, there's no built-in cross-tenant management portal.

### Managing objects at scale

[Microsoft Graph \(MS Graph\)](https://learn.microsoft.com/en-us/graph/api/resources/identity-network-access-overview?view=graph-rest-1.0) and [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview) let you manage directory objects at scale. They can also be used to manage most policies and settings in your tenant. However, you should understand the following performance considerations:

- MS Graph limits the creation of users, groups, and membership changes to 72,000 per tenant, per hour.
- MS Graph performance may be impacted by user driven actions such as read or write actions within the tenant
- MS Graph performance may be impacted by other competing IT admin tasks within the tenant
- PowerShell, SDS, Microsoft Entra Connect, and custom provisioning solutions add objects and memberships via MS Graph at different rates

## Next Steps

If you haven't reviewed Introduction to Microsoft Entra tenants, you may want to do so. then see:

- [Design a tenant configuration strategy](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-tenant-configurations)
- [Design an account strategy](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-account-strategy)
