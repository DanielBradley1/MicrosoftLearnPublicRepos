<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/roles-responsibilities?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Roles and responsibilities

This article explains who can manage apps in Copilot Managed Runtime, who can only view them, and which roles manage licensing and Copilot Credits. If you're new to administering apps in Copilot Managed Runtime, start here to understand the access model before you change settings or assign roles to other people. Other Copilot Managed Runtime admin articles refer to this article for their role requirements.

## What is Copilot Managed Runtime?

Copilot Managed Runtime is a platform for business applications that your organization deploys and governs centrally. The apps are built on Microsoft Power Platform, and you administer them from two places:

- The [Microsoft 365 admin center](https://admin.microsoft.com), where you find apps built with Copilot Managed Runtime under the **Apps** section.
- The [Power Platform admin center](https://admin.powerplatform.microsoft.com), where apps built with Copilot Managed Runtime appear alongside your other Power Platform resources.

The role you're assigned determines which admin center you use and what you can do there.

Note

- The **Power Platform administrator** and **Global administrator** roles can work from **either** admin center and change settings in both.
- The **Dynamics 365 administrator** role manages Copilot Managed Runtime from the **Power Platform admin center** only.
- The read-only roles—**AI administrator**, **AI reader**, and **Global reader**—use the **Microsoft 365 admin center** to view the Copilot Managed Runtime experience. Viewing app details in the Power Platform admin center isn't supported for these roles yet.

## Two kinds of access: Manage and Read only

Every administrator role falls into one of two groups:

- **Manage \(read and write\)** — You can view apps in Copilot Managed Runtime *and* make changes. This access includes updating settings, adjusting governance and security policies, and creating alerts.
- **Read only** — You can view apps in Copilot Managed Runtime, their components, and their health, but you can't make changes.

This split lets you give people the visibility they need without giving everyone the ability to change your configuration.

## Roles at a glance

The following table lists the Microsoft Entra roles that can access Copilot Managed Runtime, the kind of access each one has, and the equivalent [Power Platform role-based access control \(RBAC\)](#how-these-roles-relate-to-power-platform-rbac) role that each one receives automatically.

| Role | Access | Where it applies | Equivalent Power Platform RBAC role |
| --- | --- | --- | --- |
| [Power Platform administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#power-platform-administrator) | **Manage** \(read/write\) | Microsoft 365 admin center and Power Platform admin center | Power Platform owner |
| [Global administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) | **Manage** \(read/write\) | Microsoft 365 admin center and Power Platform admin center | Power Platform owner |
| [Dynamics 365 administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#dynamics-365-administrator) | **Manage** \(read/write\) | Power Platform admin center | Power Platform owner |
| [AI administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) | **Read only** | Microsoft 365 admin center | Power Platform reader |
| [AI reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-reader) | **Read only** | Microsoft 365 admin center | Power Platform reader |
| [Global reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader) | **Read only** | Microsoft 365 admin center | Power Platform reader |

For more information about these roles and their permissions, note the following details:

- The **Power Platform administrator** is the primary role for managing apps in Copilot Managed Runtime. It has full read and write access to every Copilot Managed Runtime capability.
- A **Global administrator** has the same kind of management access as a Power Platform administrator for Copilot Managed Runtime. If you already use Global administrator to run Microsoft 365, you already have what you need to manage these apps.
- The **AI administrator** and **AI reader** roles in the Microsoft 365 admin center are read-only for Copilot Managed Runtime. They can see apps and their health, but they can't change settings. The AI administrator role can also edit existing Copilot Credits spending policies. For details, see [Roles for licensing and Copilot Credits](#roles-for-licensing-and-copilot-credits).
- A **Global reader** has the same read-only access as an AI reader. It's the read-only counterpart to the Global administrator role.

Licensing and Copilot Credits use a different set of roles. For details, see [Roles for licensing and Copilot Credits](#roles-for-licensing-and-copilot-credits).

## What a Manage role can do

If you have a Manage role, you can do everything a read-only role can do, plus make changes. For example, you can:

- **Update app settings and environment group policies**, such as connectors, actions, sharing rules, and content security. See [Review and customize default settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide).
- **Apply security and compliance policies**, such as advanced connector policies \(ACP\) and access controls. See [Manage security and compliance](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/security-compliance?view=o365-worldwide).
- **Create and manage alert rules** on app health metrics. See [Monitor operational health](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide).
- **Block, unblock, and delete apps** from the **All apps** page in the Microsoft 365 admin center. See [View and oversee apps across your tenant](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/inventory?view=o365-worldwide).
- **Configure integrations**, such as [Copilot Managed Runtime for Lovable](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/configure-lovable?view=o365-worldwide).
- **Onboard and remove apps in Copilot Managed Runtime**, and decide how they're shared across your organization.

## What a read-only role can do

If you have a read-only role, you can see what's happening without the risk of changing your configuration. For example, you can:

- **View the list of apps in Copilot Managed Runtime** and open any app to see its components and details. The **All apps** list is under **Apps** in the Microsoft 365 admin center. You can't block or delete apps. See [View and oversee apps across your tenant](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/inventory?view=o365-worldwide).
- **View environment group policies and security settings**, including connectors, actions, sharing rules, and content security, without changing them. See [Review and customize default settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide) and [Manage security and compliance](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/security-compliance?view=o365-worldwide).
- **View app health metrics** on the **Monitor** tab of an app, including success rates and performance. See [Monitor operational health](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide).
- **View existing alert rules and triggered alerts**, even though you can't create or change them.

Read-only access is a good fit for people who need visibility for reporting, auditing, or support, but who shouldn't change settings. For example, help-desk staff or compliance reviewers.

The **All apps** page shows only the tabs that your role grants access to. The **Integrated apps** tab on that page uses the same roles as integrated apps do today. For details, see [Manage integrated apps in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-addins-in-the-admin-center).

## How these roles relate to Power Platform RBAC

Apps in Copilot Managed Runtime run on Power Platform, so [role-based access control for the Power Platform admin center](https://learn.microsoft.com/en-us/power-platform/admin/security/role-based-access-control) \(preview\) also governs access to the underlying platform. Power Platform RBAC uses built-in roles, such as Power Platform owner, contributor, and reader, that you can assign at the tenant, environment group, or environment scope.

You don't need to assign Power Platform RBAC roles to people who already have one of the Microsoft Entra roles in this article. Power Platform automatically treats each of these Entra roles as a tenant-scope assignment of a built-in Power Platform role:

| Microsoft Entra role | Equivalent Power Platform RBAC role \(tenant scope\) |
| --- | --- |
| Global administrator, Power Platform administrator, Dynamics 365 administrator | Power Platform owner |
| Global reader, AI administrator, AI reader | Power Platform reader |

Keep the following points in mind:

- **Power Platform RBAC is additive.** It never removes access that an Entra role grants. Explicit role assignments only add access.
- **Some Power Platform roles have no Entra equivalent.** The Power Platform contributor and Power Platform role-based access control administrator roles are available only through an explicit role assignment.
- **Explicit assignments support least privilege and automation.** You can assign built-in roles to users, security groups, service principals, and managed identities, and scope them to the tenant, an environment group, or an environment. Use explicit assignments to give automation access to the Power Platform API without giving it a Microsoft Entra admin role.
- **Power Platform RBAC applies to the Power Platform admin center and the Power Platform API.** Access to the Copilot Managed Runtime experience in the Microsoft 365 admin center depends only on the Microsoft Entra roles in this article. An explicit Power Platform RBAC assignment doesn't grant access to the Microsoft 365 admin center.
- **Read-only roles can use the Power Platform API.** Because the AI administrator, AI reader, and Global reader roles map to Power Platform reader, these roles can read Power Platform resources through [Power Platform API endpoints that support RBAC](https://learn.microsoft.com/en-us/power-platform/admin/programmability-extensibility-overview#known-limitations), even though the Power Platform admin center doesn't support them for Copilot Managed Runtime yet.
- **Scoped assignments are API-first.** Assignments at the environment group or environment scope apply to the Power Platform API today. Support for scoped assignments in the Power Platform admin center experience is on the roadmap.
- **Assigning roles requires owner-level access.** To create role assignments, you need the Power Platform owner or Power Platform role-based access control administrator role. Global administrators, Power Platform administrators, and Dynamics 365 administrators have the Power Platform owner role automatically.

To assign Power Platform RBAC roles, see [Tutorial: Assign roles to service principals](https://learn.microsoft.com/en-us/power-platform/admin/programmability-tutorial-rbac-role-assignment).

## Roles for licensing and Copilot Credits

Apps on Copilot Managed Runtime are billed through Copilot Credits. Managing Copilot Credits uses different roles from managing apps. Most of these tasks take place in the Microsoft 365 admin center under **Copilot** > **Cost management**.

| Task | Where | Roles |
| --- | --- | --- |
| Turn on usage-based billing and create spending policies | Microsoft 365 admin center | [Global administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) or [Billing administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#billing-administrator) |
| Edit existing spending policies, limits, and alerts | Microsoft 365 admin center | Global administrator, Billing administrator, [AI administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator), or [License administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#license-administrator) |
| View consumption dashboards and reports | Microsoft 365 admin center | Any of the roles above, or a reader role such as [AI reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-reader) or [Global reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader) |
| Manage Copilot Studio capacity for building apps, for environments still managed in the Power Platform admin center | Power Platform admin center | [Power Platform administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#power-platform-administrator) or Global administrator |
| Manage Copilot Studio costs for environments managed in the Microsoft 365 admin center | Microsoft 365 admin center | The same roles as for spending policies |

The AI administrator and License administrator roles can edit existing spending policies, but they can't create them. The Power Platform administrator role doesn't include Cost management in the Microsoft 365 admin center. Microsoft recommends also giving the Billing administrator role to Power Platform administrators who manage spending policies.

For how to set up billing and spending policies, see [Manage licensing and Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/licensing-credits?view=o365-worldwide).

## Recommended role assignments

Use these guidelines to decide which role to assign:

- Give **Power Platform administrator** or **Global administrator** to the small group of people responsible for configuring and governing apps in Copilot Managed Runtime.
- Give **AI administrator**, **AI reader**, or **Global reader** to people who need to monitor apps or review your setup but shouldn't make changes. If someone should only view Copilot Credits consumption, choose AI reader or Global reader, because the AI administrator role can also edit spending policies.
- Give **Billing administrator** to the people who turn on usage-based billing and create spending policies, including Power Platform administrators who manage those policies.
- Use explicit [Power Platform RBAC](https://learn.microsoft.com/en-us/power-platform/admin/security/role-based-access-control) assignments for service principals and managed identities that automate administration through the Power Platform API, instead of giving them Microsoft Entra admin roles.
- Follow the principle of *least privilege*: start with read-only access and grant Manage access only when someone's job requires it.

To learn how to give someone a role, see [Assign admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/assign-admin-roles) and [About admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Related content

- [Copilot Managed Runtime overview](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/overview?view=o365-worldwide)
- [Review and customize default settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide)
- [Monitor operational health](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide)
- [Manage security and compliance](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/security-compliance?view=o365-worldwide)
- [Manage licensing and Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/licensing-credits?view=o365-worldwide)
- [Role-based access control for Power Platform admin center](https://learn.microsoft.com/en-us/power-platform/admin/security/role-based-access-control)
