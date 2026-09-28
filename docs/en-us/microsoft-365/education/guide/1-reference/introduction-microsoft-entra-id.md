<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/introduction-microsoft-entra-id -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Introduction to Microsoft Entra tenants

Identity and access challenges that higher education institutions face are distinct from other industries. Large research universities manage diverse populations: students, faculty, researchers, staff, alumni, and external collaborators. Each population has different access needs and lifecycle patterns. As IT administrators, you might create and deprovision tens of thousands of identities every academic term. You might provide research partners with secure collaboration and multilateral federation across institutional boundaries.

To address such challenges, Microsoft Entra ID provides a unified identity and access management \(IAM\) platform. Benefits of secure access for each person and resource across your organization include the following.

- **Simplified scale and complexity**—Microsoft Entra ID is a single identity platform that spans academic, medical, and research units. It reduces the need for separate identity systems even when your institution supports hundreds of thousands of active users.
- **Adaptive access**—Access policies can account for device type, location, and risk level. Within the same framework, you can manage faculty on campus, students on personal devices, and researchers abroad.
- **Lifecycle automation**—You can automate provisioning and deprovisioning to match admission, enrollment, and graduation rhythms. Automation helps you to reduce manual work and stale account risk.
- **Cross-institutional collaboration**—You can grant scoped shared resource access to external researchers and partner institutions. They don't need separate credentials that weaken your institution's security boundary.
- **Security controls**—Phishing-resistant authentication methods, risk-based access controls, and governance capabilities help institutions meet compliance obligations and protect sensitive data.
- **Broad integration**—Microsoft Entra ID isn't a standalone tool. It's the identity layer of Microsoft 365, Azure, and thousands of EdTech platforms and applications \(such as Learning Management Systems and Student Information Systems\).

As an educational institution, you can sign up for a free trial of [Microsoft 365 Education](https://www.microsoft.com/education/products/office). You can complete an [eligibility verification wizard](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/verify-academic-eligibility) to purchase subscriptions at academic prices.

## What is a Microsoft Entra tenant?

A Microsoft Entra tenant provides IAM capabilities to applications and resources that your organization uses. An identity is a directory object that authenticates and authorizes for resource access. Identity objects exist for human identities such as students, faculty, and researchers. You can configure identity objects for nonhuman identities such as classroom devices, lab workstations, applications, service principals, and AI agents.

The Microsoft Entra tenant is an identity security boundary that your organization's IT department controls. Within this security boundary, IT administrators manage object administration \(such as user objects\) and configure tenant-wide settings.

![Diagram that shows the Microsoft Entra tenant boundary.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/intro-to-tenants-1.png)

## Create a Microsoft Entra tenant

When you sign up for a paid or trial Microsoft 365 for education subscription, you create a Microsoft Entra tenant as part of the underlying Microsoft 365 services. Similarly, when you sign up for Azure, you create a Entra tenant.

To create an additional Microsoft Entra tenant, you need a paid Microsoft license plan.

Important

When you create a Microsoft Entra tenant, specify a logical region that determines the data center location. Choose the region carefully because you can't change it after creation.

The [Microsoft 365 Education deployment guide](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start/a-start) provides more information about how to create a Microsoft Entra tenant.

## Tenant resources

![Diagram that shows the Microsoft Entra tenant boundary resources.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/intro-to-tenants-2.png)

Use Microsoft Entra ID to grant resource access to objects that represent identities. Resources can include applications and their underlying Azure resources such as databases and Learning Management Systems \(LMS\).

### Access to apps that use Microsoft Entra ID

You can grant identities access to the following application types.

- **Microsoft productivity services** such as Exchange Online, Microsoft Teams, and SharePoint Online
- **Microsoft security services** such as Microsoft Sentinel, Microsoft Intune, and Microsoft Defender for Endpoint
- **Microsoft Developer tools** such as Azure DevOps
- **Non-Microsoft applications** such as Learning Management Systems \(LMS\) and Student Information Systems \(SIS\)
- **On-premises applications** that integrate with hybrid access capabilities such as Microsoft Entra application proxy
- **Custom in-house developed applications**

Applications that use Microsoft Entra ID require you to configure and manage directory objects in the trusted Microsoft Entra tenant. Examples of directory objects include application registrations, service principals, groups, and [schema attribute extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).

Some applications can have multiple instances per tenant, such as test and production instances. Some Microsoft services, such as Exchange Online, can only have one instance per tenant.

### Directory object access

The Microsoft Entra tenant represents identities, resources, and their relationships as directory objects. Examples of directory objects include users, groups, service principals, and app registrations.

![Diagram that shows the Microsoft Entra tenant boundary directory objects.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/intro-to-tenants-3.png)

When you add objects to a Entra tenant, you get the following benefits.

- **Visibility**—If they have the right permissions, identities can discover or enumerate reporting and audit logs for resources, users, groups, and access usage. For example, a directory member can discover users in the directory with [default user permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions).
- **Applications can affect objects**—Applications can manipulate directory objects through Microsoft Graph as part of their business logic. Typical examples include reading or setting user attributes, updating user calendars, and sending emails on behalf of a user. Consent is necessary to allow applications to affect the tenant. Administrators can consent for all users. [Permissions and consent in the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-admin-consent) provides more information on application consent.

  Note

  Use caution with application permissions. For example, Exchange Online can [scope application permissions to specific mailboxes](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac).
- **Throttling and service limits**—Resource runtime behavior can trigger [throttling](https://learn.microsoft.com/en-us/graph/throttling) to prevent overuse or service degradation. Throttling can occur at the application, tenant, or entire service level. Most commonly, throttling occurs when an application has many requests within or across tenants.

Each tenant has a total object limit \(50,000 total objects by default\). After you add a custom domain, the limit increases to 300,000. To increase this object limit, contact the [EDU Customer Success Team](https://aka.ms/sdssignup). We recommend that a single Microsoft Entra tenant doesn't have more than one million users, which usually equates to approximately three million total objects. [Microsoft Entra service limits and restrictions](https://learn.microsoft.com/en-us/entra/identity/users/directory-service-limits-restrictions) provides more information about service limits in Microsoft Entra ID.

## Tenant configuration

Policies and settings in Microsoft Entra ID affect resources in the Microsoft Entra tenant through targeted or tenant-wide configurations.

![Diagram that shows the Microsoft Entra tenant boundary configuration.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/intro-to-tenants-4.png)

Examples of tenant-wide policies and settings include the following options.

- **External identities**—Global administrators for the tenant identify and control the [external identities](https://learn.microsoft.com/en-us/entra/external-id/identity-providers) that they provision in the tenant, including:

  - Whether to allow external identities in the tenant
  - From which domains they can add external identities
  - Whether users can invite users from other tenants

- **Named locations**—Global administrators can create [named locations](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-assignment-network). They can then use them to block sign-in from specific locations and trigger Conditional Access policies that require specific authentication strengths to access resources.
- **Allowed authentication methods**—Global administrators can configure tenant [authentication methods](https://learn.microsoft.com/en-us/entra/identity/authentication/overview-authentication) and [authentication strengths](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths). Settings include phishing-resistant options like passkeys and FIDO2 security keys.
- **Self-service options**—Global administrators can configure self-service options such as [authentication method registration](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods-manage) and [Microsoft 365 group creation](https://learn.microsoft.com/en-us/entra/identity/users/groups-self-service-management) at the tenant level.

You can scope some tenant-wide configuration implementation when global administration policies don't override them. For example:

- If the tenant configuration allows external identities, a resource administrator can exclude those identities from accessing a resource.
- If the tenant configuration allows personal device registration, a resource administrator can exclude those devices from accessing specific resources.
- If you configure named locations, a resource administrator can configure policies that allow or exclude access from those locations.

## Tenant administration

Tenant administration includes identity object management and scoped tenant-wide configuration implementation. Objects include users, groups, devices, service principals, and agent identities. You can scope the effects of tenant-wide configurations for authentication, authorization, self-service options, and more.

![Diagram that shows the Microsoft Entra tenant boundary administration.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/intro-to-tenants-5.png)

Tenant-wide administrators or global administrators can perform the following functions.

- Grant access to any resource to any user
- Assign resource roles to any user
- Assign lower-scoped admin roles to any user

### Directory object administration

Administrators manage how identity objects access resources and under what circumstances. They can disable, delete, or modify directory objects based on their privileges.

- **Organizational identity user objects**

  - Administrators
  - Organizational users
  - Organizational developers
  - Test users

- **External identities \(users from outside the organization\)**

  - Partners or other educational institutions that you provision with accounts local to your organization's environment
  - Partners or other educational institutions that you provision via Microsoft Entra External ID B2B collaboration

- **Group objects**

  - Security groups
  - Microsoft 365 groups

- **Device objects**

  - Microsoft Entra hybrid joined devices \(on-premises computers that synchronize from on-premises Active Directory\)
  - Microsoft Entra joined devices
  - Microsoft Entra registered mobile devices that employees use to access their workplace applications.

- **Non-human identity objects**

  - Service principals for applications
  - Managed Identities for Azure workloads
  - AI Agent Identities \(via Agent ID\)

Note

In a hybrid environment, identities typically use [Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect) or [Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync) to synchronize from the on-premises Active Directory environment.

### Identity services administration

Administrators with the right permissions can manage tenant-wide policy implementation at the levels of resource groups, security groups, or applications. For resource administration, consider the following points to decide whether to keep resources together or isolate them.

- An Authentication Administrator can require nonadministrators to reregister for FIDO2 security keys or passkeys.
- A Conditional Access \(CA\) Administrator can create CA policies that require users to sign in to specific apps only from compliant devices. They can scope configurations such as allowing external identities in the tenant while excluding them from accessing a resource.
- A Cloud Application Administrator can consent to application permissions on behalf of all users.
- A Global Administrator can control a subscription.

### Licensing

Microsoft paid cloud services, such as Microsoft 365, require licenses assigned to each user who needs service access. Microsoft Entra ID is the underlying infrastructure that supports identity management for all Microsoft cloud services and stores information about license assignment states for users. Microsoft Entra ID supports [group-based licensing](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal) so that you can assign one or more product licenses to a group of users.

## Microsoft Entra ID in Microsoft 365 Education scenarios

Microsoft Entra ID helps students and faculty sign in and access resources and services that include the following.

- **Resource sign-in and authorization**

  - Configure domains for sign-in and email for cloud authentication in Microsoft Entra ID.
  - [Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview) provides fine-grained access control to resources such as sensitive research applications.
  - [External multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-external-method-manage) \(MFA\) enables integration with non-Microsoft MFA providers.

- **Microsoft 365 capabilities**

  - Microsoft 365 license assignment for Microsoft Entra identities triggers provisioning.
  - Microsoft Entra directory objects represent Microsoft 365 objects \(such as distribution lists, Microsoft 365 Groups, contacts, and Microsoft Teams\) that you manage in Microsoft Entra ID.
  - To provide authorization, Microsoft 365 services use Microsoft Entra groups.
  - Control access to Microsoft 365 through Microsoft Entra ID.

- **Governance and security**

  - Management and security features such as Intune for Education rely on Microsoft Entra users, groups, devices, and policies.
  - [Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure) allows Just-in-Time \(JIT\) and Just Enough Administration \(JEA\) access to privileged operations.
  - [Entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-overview) governs access packages to research resources, labs, and sensitive data.
  - [Sign-in logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins) and [audit activity reports](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-audit-logs) help with compliance and incident investigation.
  - [Verified ID](https://www.microsoft.com/security/business/identity-access/microsoft-entra-verified-id) provides secure user onboarding, help desk, and alumni scenarios.
  - [Access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview) help with periodic access rights certification.
  - [Lifecycle workflows](https://learn.microsoft.com/en-us/entra/id-governance/what-are-lifecycle-workflows) help with management at scale. Automate tasks such as provisioning student accounts when they enroll, adjusting permissions when faculty change departments, and revoking access upon student graduation. Lifecycle workflows can also help with dual persona and account discovery scenarios common in the EDU realm \(such as student workers\).
  - [SCIM APIs](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/entra-id-scim-api-reference) provide industry-standard interfaces for automated user and group provisioning for universities. Integrate with HR systems, SIS platforms, and research grant management systems.

- **External collaboration**

  - [Microsoft Entra External ID B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b) helps you manage external collaboration capabilities.
  - [Multitenant organizations in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/plan-multi-tenant-org-overview) allows multiple tenants to collaborate seamlessly while maintaining separate identities and administrative boundaries.
  - [Introduction to multilateral federation solutions](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-introduction) provides guidance on how to participate in multilateral federations with Microsoft Entra ID.

- **AI and agent governance**—[Microsoft Entra Agent ID](https://learn.microsoft.com/en-us/entra/agent-id/) allows for secure management and governance of your AI workloads.
- **Network access**—[Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access) provides identity-aware network security. It enables secure connectivity to internet resources, SaaS applications, and on-premises research systems without requiring a traditional VPN.
- **Hybrid environments**

  - Microsoft Entra ID [hybrid capabilities](https://learn.microsoft.com/en-us/microsoft-365/enterprise/prepare-for-directory-synchronization) synchronize from on-premises Active Directory through [Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect) and [Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync). With these tools, you can configure the appropriate authentication method for your organization. Authentication methods might include [password hash synchronization](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-phs), [pass-through authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta), or [federation integration](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-fed-whatis) with AD FS or a non-Microsoft SAML identity provider.
  - APIs help you provision directory objects from Student Information Systems \(SIS\) with [School Data Sync](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-school-data-sync).

## Next steps

- [Design a multitenant architecture](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-multi-tenant-architecture)
- [Design tenant configuration strategy](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-tenant-configurations)
