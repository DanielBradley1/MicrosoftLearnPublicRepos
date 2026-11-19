<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-getting-started -->
<!-- Sitemap-Last-Modified: 2026-04-23 -->

# Start using Privileged Identity Management

## Overview

Use Privileged Identity Management \(PIM\) to manage, control, and monitor access within your Microsoft Entra organization. With PIM you can provide as-needed and just-in-time access to Azure resources, Microsoft Entra resources, and other Microsoft online services like Microsoft 365 or Microsoft Intune.

This article describes how to enable Privileged Identity Management \(PIM\) and get started using it.

## Prerequisites

To use Privileged Identity Management, you must have a Microsoft Entra ID P2 or Microsoft Entra ID Governance license. For more information on licensing, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals).

PIM for app roles \(preview\) requires Microsoft Entra ID Governance licenses.

License coverage is required for users with eligible or time-bound app role assignments and for request approvers.

At preview launch, licensed tenants receive access to PIM for app roles automatically. No tenant enrollment or enablement step is required.

PIM for app roles \(preview\) is available in all clouds. There are no additional tenant prerequisites or exclusions beyond the licensing requirement.

## Activation of role assignments

When a Microsoft Entra tenant has a Microsoft Entra ID P2 or Microsoft Entra ID Governance license, users with active role assignments can do the following:

- Open the **Roles and administrators** page in Microsoft Entra ID and select a role.
- Open the **Privileged Identity Management** page.
- Make calls to PIM using the [Microsoft Entra roles API](https://learn.microsoft.com/en-us/graph/identity-network-access-overview/).

Microsoft Entra enables PIM for the tenant in the following ways:

- Starting immediately, you can create eligible or time-bound assignments for Microsoft Entra roles;
- Global Administrators or Privileged Role Administrators may start receiving other emails, such as the PIM weekly digest;
- The PIM service principal name \(MS–PIM\) may get mentioned in audit log events related to role assignment management.

These behaviors are expected and shouldn't affect your workflows.

## Prepare PIM for Microsoft Entra roles

Here are the recommended tasks to prepare Privileged Identity Management to manage Microsoft Entra roles:

1. [Configure Microsoft Entra role settings](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-change-default-settings)
2. [Give eligible assignments](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-add-role-to-user)
3. [Allow eligible users to activate their Microsoft Entra role just-in-time](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-activate-role)

## Prepare PIM for Azure roles

Here are the recommended tasks to prepare Privileged Identity Management to manage Azure roles for a subscription:

1. [Discover Azure resources](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-discover-resources)
2. [Configure Azure role settings](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-configure-role-settings)
3. [Give eligible assignments](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-assign-roles)
4. [Allow eligible users to activate their Azure roles just-in-time](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-activate-your-roles)

## Prepare PIM for app roles \(preview\)

Use PIM for app roles to give users eligible assignments to roles defined by an application. Users activate those assignments when they need access and deactivate them when they finish. For background, see [PIM for app roles \(preview\)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/concept-pim-for-app-roles).

Applications with existing app roles can be managed directly in PIM. No application onboarding or bring-under-management step is required.

Here are the recommended tasks to prepare Privileged Identity Management to manage app roles:

1. [Configure app role settings](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/app-roles-settings).
2. [Give eligible app role assignments](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/app-roles-assign).
3. [Allow eligible users to activate their app roles just-in-time](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/app-roles-activate).

To open the app role experience, sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) and browse to **ID Governance** > **Privileged Identity Management** > **App Roles \(Preview\)**.

## Navigate to your tasks

Once Privileged Identity Management is set up, you can learn your way around.

[![Screenshot showing the navigation window in Privileged Identity Management showing Tasks, Manage, Activity, and Troubleshooting + Support options.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-getting-started/pim-quickstart-tasks.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-getting-started/pim-quickstart-tasks.png#lightbox)

| Menu item | Description |
| --- | --- |
| **My roles** | Displays a list of eligible and active roles assigned to you. **My roles** is where you can activate any assigned eligible roles. |
| **My requests** | Displays your pending requests to activate eligible role assignments. |
| **Approve requests** | Displays a list of requests to activate eligible roles by users in your directory that you can approve. |
| **Review access** | Lists active access reviews you're assigned to complete, whether you're reviewing access for yourself or someone else. |
| **Microsoft Entra roles** | Displays a dashboard and settings for Privileged Role Administrators to manage Microsoft Entra role assignments. This dashboard is disabled for anyone who isn't a Privileged Role Administrator. These users have access to a special dashboard titled **My view**. The **My view** dashboard only displays information about the user accessing the dashboard, not the entire organization. |
| **Groups** | Manage just-in-time membership in the group or just-in-time ownership of the group. Groups can be used to provide access to Microsoft Entra roles, Azure roles, and various other scenarios. To manage a Microsoft Entra group in PIM, you must bring it under management in PIM. |
| **Azure resources** | Displays a dashboard and settings for Privileged Role Administrators to manage Azure resource role assignments. This dashboard is disabled for anyone who isn't a Privileged Role Administrator. These users have access to a special dashboard titled **My view**. The **My view** dashboard only displays information about the user accessing the dashboard, not the entire organization. |
| **App Roles \(Preview\)** | Displays a list of applications. Select an application to work with its app roles. Available management and self-service tasks depend on your permissions and assignments. |
| **My audit history** | View your PIM audit history, including all role activations and assignments. |
| **Troubleshoot** | Get help diagnosing and resolving common PIM issues. |
| **New support request** | Create a support request for PIM-related issues. |

## Next steps

- [Assign Microsoft Entra roles in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-add-role-to-user)
- [Manage Azure resource access in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-discover-resources)
- [Learn about PIM for app roles \(preview\)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/concept-pim-for-app-roles).
