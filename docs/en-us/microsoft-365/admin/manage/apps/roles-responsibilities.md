<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/roles-responsibilities?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# Roles and responsibilities \(preview\)

\[This article is prerelease documentation and is subject to change.\]

This article explains who can manage apps in Copilot Managed Runtime and who can only view them. If you're new to administering apps in Copilot Managed Runtime, start here to understand the access model before you change settings or assign roles to other people.

Important

- This is a preview feature.
- These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?LinkId=2373139), and are available before an official release so that customers can get early access and provide feedback.

## What is Copilot Managed Runtime?

Copilot Managed Runtime is a platform for business applications that your organization deploys and governs centrally. The apps are built on Microsoft Power Platform, and you administer them from two places:

- The [Microsoft 365 admin center](https://admin.microsoft365.com/Adminportal/Home#/homepage), where you find apps built with Copilot Managed Runtime under the **Apps** section.
- The [Power Platform admin center](https://admin.preview.powerplatform.microsoft.com/home), where apps built with Copilot Managed Runtime appear alongside your other Power Platform resources.

The role you're assigned determines which admin center you use and what you can do there.

Note

- The **Power Platform administrator** \(and the other *manage* roles, such as Global administrator and Dynamics 365 administrator\) can work from **either** admin center and change settings in both.
- The read-only roles—**AI administrator**, **AI reader**, and **Global reader**—use the **Microsoft 365 admin center** to view the Copilot Managed Runtime experience. Reading app details from the Power Platform admin center isn't supported for these roles yet.

## Two kinds of access: Manage and Read only

Every administrator role falls into one of two groups:

- **Manage \(read and write\)** — You can view apps in Copilot Managed Runtime *and* make changes. This access includes updating settings, adjusting governance and security policies, and creating alerts.
- **Read only** — You can view apps in Copilot Managed Runtime, their components, and their health, but you can't make changes.

This split lets you give people the visibility they need without giving everyone the ability to change your configuration.

## Roles at a glance

The following table lists the most common roles and the kind of access each one has.

| Role | Access | Where it applies |
| --- | --- | --- |
| [Power Platform administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#power-platform-administrator) | **Manage** \(read/write\) | Microsoft 365 admin center and Power Platform admin center |
| [Global administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) | **Manage** \(read/write\) | Microsoft 365 admin center and Power Platform admin center |
| [Dynamics 365 administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#dynamics-365-administrator) | **Manage** \(read/write\) | Power Platform admin center |
| [AI administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) | **Read only** | Microsoft 365 admin center |
| [AI reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-reader) | **Read only** | Microsoft 365 admin center |
| [Global reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader) | **Read only** | Microsoft 365 admin center |

For more information about these roles and their permissions, note the following details:

- The **Power Platform administrator** is the primary role for managing apps in Copilot Managed Runtime. It has full read and write access to every Copilot Managed Runtime capability.
- A **Global administrator** has the same kind of management access as a Power Platform administrator for Copilot Managed Runtime. If you already use Global administrator to run Microsoft 365, you already have what you need to manage these apps.
- The **AI administrator** and **AI reader** roles in the Microsoft 365 admin center are read-only for Copilot Managed Runtime. They can see apps and their health, but they can't change settings.
- A **Global reader** has the same read-only access as an AI reader. It's the read-only counterpart to the Global administrator role.

## What a Manage role can do

If you have a Manage role, you can do everything a read-only role can do, plus make changes. For example, you can:

- **Update app settings** and adjust how governance is applied. See [Customizing governance](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide).
- **Apply security and compliance policies**, such as advanced connector policies \(ACP\) and access controls. See [Security and compliance for Copilot Managed Runtime](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/security-compliance?view=o365-worldwide).
- **Create and manage alerts** on app health metrics. See [Visibility and monitoring](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide).
- **Onboard and remove apps in Copilot Managed Runtime**, and decide how they're shared across your organization.

## What a read-only role can do

If you have a read-only role, you can see what's happening without the risk of changing your configuration. For example, you can:

- **View the list of apps in Copilot Managed Runtime** and open any app to see its components and details. The **All apps** list is under **Apps** in the Microsoft 365 admin center. See [Visibility and monitoring](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide).
- **View app health metrics** on the **Monitor** tab of an app, including success rates and performance.
- **View existing alert rules and triggered alerts**, even though you can't create or change them.

Read-only access is a good fit for people who need visibility for reporting, auditing, or support, but who shouldn't change settings. For example, help-desk staff or compliance reviewers.

## Recommended role assignments

Use these guidelines to decide which role to assign:

- Give **Power Platform administrator** or **Global administrator** to the small group of people responsible for configuring and governing apps in Copilot Managed Runtime.
- Give **AI administrator**, **AI reader**, or **Global reader** to people who need to monitor apps or review your setup but shouldn't make changes.
- Follow the principle of *least privilege*: start with read-only access and grant Manage access only when someone's job requires it.

To learn how to give someone a role, see [Assign admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/assign-admin-roles) and [About admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Related content

- [Copilot Managed Runtime overview \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/?view=o365-worldwide)
- [Review and customize default settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide)
- [Monitor operational health](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide)
- [Manage security and compliance](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/security-compliance?view=o365-worldwide)
