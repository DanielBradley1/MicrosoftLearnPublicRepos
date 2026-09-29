<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/activate-defender-rbac -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Activate Microsoft Defender unified role-based access control \(URBAC\)

This article lists the steps to activate Defender workloads available in your environment to use the Microsoft Defender unified role-based access control \(RBAC\). Activate the unified RBAC model for some or all of your workloads for the Microsoft Defender portal to start enforcing the permissions and assignments configured in your new [custom roles](https://learn.microsoft.com/en-us/defender-xdr/create-custom-rbac-roles) or [imported roles](https://learn.microsoft.com/en-us/defender-xdr/import-rbac-roles). Before you begin, review the [prerequisites](#prerequisites) and [considerations](#before-you-begin) for unified RBAC activation.

Important

Starting 2025, the Microsoft Defender unified RBAC model is the default permissions model for new Microsoft Defender Endpoint tenants and Microsoft Defender for Identity tenants. These tenants can't export roles and permissions from the old model. Defender for Endpoint or Defender for Identity tenants with roles and permissions assigned or exported prior to this date maintain their old roles and permissions configuration.

Starting July 2026, the Microsoft Defender unified RBAC model is also the default permissions model for new Microsoft Defender for Office 365 Plan 2 organizations. For more information, see [MC1246006](https://admin.microsoft.com/Adminportal/Home#/MessageCenter/:/messages/MC1246006).

## Prerequisites

You must be at least a Security Administrator in Microsoft Entra ID to activate Microsoft Defender unified RBAC. For more information on permissions, see [Permission prerequisites](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac#permissions-prerequisites).

## Before you begin

Before you activate Microsoft Defender unified RBAC, consider the following:

- The following roles are not supported for unified RBAC: the Microsoft Sentinel *Playbook Operator*, *Automation Contributor* and *Workbook Contributor*. These roles continue to be managed in Azure.
- Assigning permissions to a service principal or to a GDAP user group in Microsoft Sentinel isn't supported in unified RBAC. If you need either capability, don't activate Sentinel in unified RBAC yet. Continue using Azure RBAC for Microsoft Sentinel.
- The Microsoft Defender unified RBAC model only impacts the Microsoft Defender portal. It doesn't impact the [Microsoft Purview portal](https://purview.microsoft.com) or the [Exchange Admin Center](https://admin.exchange.microsoft.com).
- Once unified RBAC is activated for Microsoft Sentinel, use unified RBAC in the Defender portal to manage Sentinel permissions. Making permission changes in the Azure portal after unified RBAC is active for a workspace might lead to sync errors. If a sync error occurs, a notification appears on the **Permissions** page in the Defender portal with instructions on how to resolve it.

## Activate Microsoft Defender unified RBAC

The following steps guide you on how to activate the Microsoft Defender unified RBAC model. You can activate your workloads in the following ways:

- [Activate in the permissions and roles page](#activate-from-the-permissions-and-roles-page)
- [Activate in Microsoft Defender settings](#activate-in-microsoft-365-defender-settings)

### Activate from the Permissions and roles page

Follow these steps to activate unified RBAC from the Permissions and roles page:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. In the navigation pane, select **System** > **Permissions**.
3. Under **Microsoft Defender XDR**, select **Roles**.
4. You can activate your workloads in two ways: either select **Activate workloads** from the banner or select **Workload settings** at the top of the page.

[![Screenshot of the activate workloads page](https://learn.microsoft.com/en-us/defender-xdr/media/activate-defender-rbac/m365-defender-rbac-activate-workloads1.png)](https://learn.microsoft.com/en-us/defender-xdr/media/activate-defender-rbac/m365-defender-rbac-activate-workloads1.png#lightbox)

Note

The **Activate workloads** button is only available when there's at least one workload that's not active for Microsoft Defender unified RBAC. Microsoft Defender for Cloud is active by default with Microsoft Defender unified RBAC. Defender unified RBAC is automatically active for Exposure Management access. Once a custom role with one of the Exposure Management permissions is created, it has an immediate impact on assigned users. There's no need to activate it.

To activate Exchange Online permissions in Microsoft Defender unified RBAC, Defender for Office 365 permissions must be active.

1. Select the toggle for each workload you want to activate or deactivate.
2. Optional: To activate Sentinel's workload, select **View Workspaces** and select which workspaces you'd like to activate.

   ![Screenshot of the page where you can choose workloads to activate.](https://learn.microsoft.com/en-us/defender-xdr/media/activate-defender-rbac/defender-activate-workloads.png)
3. Select **Activate** on the confirmation message.

### Activate in Microsoft Defender settings

Follow these steps to activate your workloads directly in Microsoft Defender XDR settings:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. In the navigation pane, select **System** > **Settings**.
3. Select **Microsoft Defender XDR**.
4. Under **General**, select **Permissions and roles**. This brings you to the **Activate unified role-based access control** page.
5. Select the toggle for the workloads you want to activate or deactivate.
6. Optional: To activate Microsoft Sentinel's workload, select **View Workspaces** and select which workspaces you'd like to activate.
7. Select **Activate** on the confirmation message.

## Deactivate Microsoft Defender unified RBAC

You can deactivate Microsoft Defender unified RBAC and revert to the individual RBAC models from Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Sentinel, and Microsoft Defender for Office 365 \(which includes [the built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about)\).

To deactivate workloads:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. In the navigation pane, select **System** > **Permissions**.
3. Under **Microsoft Defender XDR**, select **Roles**.
4. Select **Workload settings** at the top of the page.
5. Turn off the toggle for each workload you want to deactivate.
6. Select **Activate** on the confirmation message.

The status for deactivated workloads is set to **Not Active**.

If you deactivate a workload, the roles created and edited within Microsoft Defender unified RBAC are no longer in effect, and the previous permissions model is used instead.

## Related content

- [Edit or delete roles](https://learn.microsoft.com/en-us/defender-xdr/edit-delete-rbac-roles)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
