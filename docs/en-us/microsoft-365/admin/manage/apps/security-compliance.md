<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/security-compliance?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-14 -->

# Manage security and compliance for Copilot Managed Runtime \(preview\)

\[This article is prerelease documentation and is subject to change.\]

This article covers security and compliance for Copilot Managed Runtime in the Power Platform admin center and the Microsoft 365 admin center. It explains how to apply data protection policies, configure access controls, and monitor compliance for Copilot Managed Runtime in your tenant.

Important

- This is a preview feature.
- These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?LinkId=2373139), and are available before an official release so that customers can get early access and provide feedback.

## Overview

Apps in Copilot Managed Runtime are line-of-business applications built with the Copilot Managed Runtime SDK. You configure security settings primarily in the **Microsoft 365 admin center**, with additional environment-level controls available in the **Power Platform admin center**.

This article focuses on security capabilities that are specific to apps in Copilot Managed Runtime. For general Power Platform security, see [Security overview](https://learn.microsoft.com/en-us/power-platform/admin/security/security-overview).

## Prerequisites

To manage security settings for Copilot Managed Runtime, you need one of the following Microsoft Entra ID roles:

| Role | Access level |
| --- | --- |
| [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) | Read and write |
| [Power Platform Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#power-platform-administrator) | Read and write |
| [AI Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-reader) | Read-only access to Copilot Managed Runtime configuration and security settings |

The environment where you deploy apps built with Copilot Managed Runtime must be a [Managed Environment](https://learn.microsoft.com/en-us/power-platform/admin/managed-environment-overview).

## Where to configure Copilot Managed Runtime

You can view and configure Copilot Managed Runtime in two admin centers:

| Admin center | What you can do |
| --- | --- |
| **Microsoft 365 admin center \(MAC\)** | Primary surface for Copilot Managed Runtime governance. View app inventory, configure sharing controls, manage app settings, and apply environment group rules. |
| **Power Platform admin center \(PPAC\)** | View environment groups, configure environment-level security settings, and manage advanced connector policies. |

Microsoft 365 admin center is the primary admin experience for Copilot Managed Runtime. Settings you configure in Microsoft 365 admin center appear in Power Platform admin center. Administrators can use either surface, but Copilot Managed Runtime-specific configuration starts in Microsoft 365 admin center.

## Sharing controls

Configure sharing for apps in Copilot Managed Runtime at the environment group level. These controls are specific to Copilot Managed Runtime and operate separately from general Power Platform sharing settings.

To configure sharing for apps in Copilot Managed Runtime:

1. In the **Microsoft 365 admin center**, go to **Settings** > **App settings**.
2. Go to the environment group rules.
3. Find the Copilot Managed Runtime sharing rule to set sharing limits.

Sharing controls let administrators restrict how broadly makers can share apps built with Copilot Managed Runtime within the organization. The sharing limit applies to all apps built with Copilot Managed Runtime within the environment group.

Note

Configure Copilot Managed Runtime sharing at the environment group level, not at the individual app or environment level. This setting is specific to Copilot Managed Runtime and doesn't affect sharing for other Power Platform resources in the same environment.

For more information about environment groups and governance configuration, see [Governance for Copilot Managed Runtime](https://learn.microsoft.com/en-us/power-platform/admin/managed-governance).

## Control access with a security group

Apps in Copilot Managed Runtime use the security group associated with their environment to control access. Associate a Microsoft Entra security group with the environment to restrict who can run apps in that environment. The restriction applies automatically to all apps in the environment, so you don’t need to configure each app separately.

Environment access and app sharing are separate controls. To run an app, a user must be a member of the environment’s security group and have access to the app. Sharing an app doesn’t bypass the environment’s security group restriction. Adding a user to the security group doesn’t grant access to individual apps.

To associate a security group with an environment, follow these steps:

1. In Power Platform admin center, select **Manage** > **Environments**.
2. Select the environment, and then select **Edit**.
3. In **Edit details**, under **Security group**, select the edit icon.
4. Find and select the group, select **Done**, and then select **Save**.

Important

Before you associate a security group with an existing environment, review the group’s membership. Users who aren’t members of the group lose access to managed apps in the environment. To revoke a user’s environment access later, remove the user from the security group.

For more information about configuration, supported group types, and environment access requirements, see [Control user access to environments with security groups and licenses](https://learn.microsoft.com/en-us/power-platform/admin/control-user-access).

## Content Security Policy \(CSP\)

Apps built with Copilot Managed Runtime enforce Content Security Policy headers to protect against cross-site scripting and other injection attacks. Each app has its own CSP configuration, which the platform applies.

For the default directives and instructions to review and customize the policy, see [Content security policy](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#content-security-policy).

## Advanced connector policies \(ACP\)

Advanced connector policies control which connectors and connector actions apps built with Copilot Managed Runtime can use. ACP applies to all resources in the environment, including apps, flows, and agents. Apps built with Copilot Managed Runtime don't require any extra configuration.

Policies configured for the environment or environment group apply automatically to apps built with Copilot Managed Runtime deployed there.

For details on configuring advanced connector policies, see [Advanced connector policies](https://learn.microsoft.com/en-us/power-platform/admin/advanced-connector-policies).

## Related content

For more information about governance, security, and connector policies, see the following resources:

- [Managed governance](https://learn.microsoft.com/en-us/power-platform/admin/managed-governance)
- [Managed Environments overview](https://learn.microsoft.com/en-us/power-platform/admin/managed-environment-overview)
- [Security overview - Power Platform](https://learn.microsoft.com/en-us/power-platform/admin/security/security-overview)
- [Advanced connector policies](https://learn.microsoft.com/en-us/power-platform/admin/advanced-connector-policies)
