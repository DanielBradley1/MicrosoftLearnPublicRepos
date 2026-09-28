<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/7-secure-access-conditional-access -->
<!-- Sitemap-Last-Modified: 2024-10-29 -->

# Manage external access to resources with Conditional Access policies

Conditional Access interprets signals, enforces policies, and determines if a user is granted access to resources. In this article, learn about applying Conditional Access policies to external users. The article assumes you might not have access to entitlement management, a feature you can use with Conditional Access.

Learn more:

- [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [Plan a Conditional Access deployment](https://learn.microsoft.com/en-us/entra/identity/conditional-access/plan-conditional-access)
- [What is entitlement management?](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-overview)

The following diagram illustrates signals to Conditional Access that trigger access processes.

![Diagram of Conditional Access signal input and resulting access processes.](https://learn.microsoft.com/en-us/entra/architecture/media/secure-external-access/7-conditional-access-signals.png)

## Before you begin

This article is number 7 in a series of 10 articles. We recommend you review the articles in order. Go to the **Next steps** section to see the entire series.

## Align a security plan with Conditional Access policies

In the third article, in the set of 10 articles, there's guidance on creating a security plan. Use that plan to help create Conditional Access policies for external access. Part of the security plan includes:

- Grouped applications and resources for simplified access
- Sign-in requirements for external users

Important

Create internal and external user test accounts to test policies before applying them.

See article three, [Create a security plan for external access to resources](https://learn.microsoft.com/en-us/entra/architecture/3-secure-access-plan)

## Conditional Access policies for external access

The following sections are best practices for governing external access with Conditional Access policies.

### Entitlement management or groups

If you can't use connected organizations in entitlement management, create a Microsoft Entra security group, or Microsoft 365 Group for partner organizations. Assign users from that partner to the group. You can use the groups in Conditional Access policies.

Learn more:

- [What is entitlement management?](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-overview)
- [Manage Microsoft Entra groups and group membership](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups)
- [Overview of Microsoft 365 Groups for administrators](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/office-365-groups?view=o365-worldwide&preserve-view=true)

### Conditional Access policy creation

Create as few Conditional Access policies as possible. For applications that have the same access requirements, add them to the same policy.

Conditional Access policies apply to a maximum of 250 applications. If more than 250 applications have the same access requirement, create duplicate policies. For instance, Policy A applies to apps 1-250, Policy B applies to apps 251-500, and so on.

### Naming convention

Use a naming convention that clarifies policy purpose. External access examples are:

- ExternalAccess\_actiontaken\_AppGroup
- ExternalAccess\_Block\_FinanceApps

## Allow external access to specific external users

There are scenarios when it's necessary to allow access for a small, specific group.

Before you begin, we recommend you create a security group, which contains external users who access resources. See, [Manage Microsoft Entra groups and group membership](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups).

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access**.
3. Select **Create new policy**.
4. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
5. Under **Assignments**, select **Users or workload identities**.

   1. Under **Include**, select **All guests and external users**.
   2. Under **Exclude**, select **Users and groups** and choose your organization's emergency access or break-glass accounts and the external users security group.

6. Under **Target resources** > **Resources \(formerly cloud apps\)**, select the following options:

   1. Under **Include**, select **All resources \(formerly 'All cloud apps'\)**
   2. Under **Exclude**, select applications you want to exclude.

7. Under **Access controls** > **Grant**, select **Block access**, then select **Select**.
8. Select **Create** to create to enable your policy.

Note

After administrators confirm the settings using [report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-insights-reporting), they can move the **Enable policy** toggle from **Report-only** to **On**.

Learn more: [Manage emergency access accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access)

## Service provider access

Conditional Access policies for external users might interfere with service provider access, for example granular delegated administrate privileges.

Learn more: [Introduction to granular delegated admin privileges \(GDAP\)](https://learn.microsoft.com/en-us/partner-center/gdap-introduction)

## Conditional Access templates

Conditional Access templates are a convenient method to deploy new policies aligned with Microsoft recommendations. These templates provide protection aligned with commonly used policies across various customer types and locations.

Learn more: [Conditional Access templates \(Preview\)](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common)

## Next steps

Use the following series of articles to learn about securing external access to resources. We recommend you follow the listed order.

1. [Determine your security posture for external access with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/architecture/1-secure-access-posture)
2. [Discover the current state of external collaboration in your organization](https://learn.microsoft.com/en-us/entra/architecture/2-secure-access-current-state)
3. [Create a security plan for external access to resources](https://learn.microsoft.com/en-us/entra/architecture/3-secure-access-plan)
4. [Secure external access with groups in Microsoft Entra ID and Microsoft 365](https://learn.microsoft.com/en-us/entra/architecture/4-secure-access-groups)
5. [Transition to governed collaboration with Microsoft Entra B2B collaboration](https://learn.microsoft.com/en-us/entra/architecture/5-secure-access-b2b)
6. [Manage external access with Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/entra/architecture/6-secure-access-entitlement-managment)
7. [Manage external access to resources with Conditional Access policies](https://learn.microsoft.com/en-us/entra/architecture/7-secure-access-conditional-access) \(You're here\)
8. [Control external access to resources in Microsoft Entra ID with sensitivity labels](https://learn.microsoft.com/en-us/entra/architecture/8-secure-access-sensitivity-labels)
9. [Secure external access to Microsoft Teams, SharePoint, and OneDrive for Business with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/architecture/9-secure-access-teams-sharepoint)
10. [Convert local guest accounts to Microsoft Entra B2B guest accounts](https://learn.microsoft.com/en-us/entra/architecture/10-secure-local-guest)
