<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/configuration-manager-and-windows-as-service -->
<!-- Sitemap-Last-Modified: 2025-03-31 -->

# Configuration Manager and Windows as a service

*Applies to: Configuration Manager \(current branch\)*

Configuration Manager provides comprehensive control over feature updates for Windows. To fully adopt the Windows as a service model, you also must adopt the Configuration Manager current branch model. To stay current with Windows, requires that you stay current with Configuration Manager for the best experience. New versions of Configuration Manager are required to take full advantage of the exciting new enterprise features for Windows. This article is intended to be a landing page for the key articles required to adopt Configuration Manager current branch. Configuration Manager current branch gets you on your way to Windows as a service.

## Configuration Manager current branch

| Article | Description |
| --- | --- |
| [Overview of Configuration Manager current branch](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-incremental-versions) | Provides a brief summary of the key points for the servicing model for Configuration Manager current branch |
| [Support lifecycle](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/current-branch-versions-supported) | Explains the current branch support and servicing model. |
| [Removed and deprecated items](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated) | Provides early notice about future changes that might affect your use of Configuration Manager. |
| [Updates to Configuration Manager current branch](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates) | Explains the easy in-console method of applying feature updates to Configuration Manager. |
| [Get available updates](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/prepare-in-console-updates#get-available-updates) | Explains the two modes available to get new Configuration Manager feature updates. |
| [Update checklist](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/prepare-in-console-updates#before-you-install-an-in-console-update) | Provides update version-specific checklists, if applicable. |
| [Install new Configuration Manager feature updates](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/install-in-console-updates) | Explains the simple installation steps for feature updates. |
| [Support for Windows 11](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-11) | Provides a support matrix for Windows 11 versions. |
| [Support for Windows 10](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-10) | Provides a support matrix for Windows 10 versions. |
| [Support for Windows ADK](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-adk) | Provides a support matrix for the Windows Assessment and Deployment Kit \(Windows ADK\). |
| [Technical Previews for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview) | Provides information about the Configuration Manager technical preview program. |

## Windows as a service

| Article | Description |
| --- | --- |
| [Manage Windows as a service](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/manage-windows-as-a-service) | Explains how to use servicing plans to deploy Windows feature updates. |
| [Upgrade Windows via task sequence](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system) | The details of creating a task sequence to upgrade Windows with additional recommendations. |
| [Phased deployments](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-phased-deployment-for-task-sequence) | Phased deployments automate a coordinated, sequenced rollout of a task sequence across multiple collections. |
| [Optimize Windows update delivery](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/optimize-windows-10-update-delivery) | Use Configuration Manager to manage update content to stay current with Windows. |
| [Integrate Windows Update client policies \(optional\)](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/integrate-windows-update-client-policies) | Explains how to define and deploy Windows Update client policies using Configuration Manager. |
| [Use co-management with Microsoft Intune and Windows Update client policies \(optional\)](https://learn.microsoft.com/en-us/intune/configmgr/comanage/overview) | Provides an overview of co-management. |

## Product lifecycle

Another important aspect of staying current with Windows and Configuration Manager is to monitor product lifecycles. Configuration Manager has built-in features to help:

- Be proactive with dashboards for planning:

  - [Product lifecycle dashboard](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/product-lifecycle-dashboard): View the Microsoft Lifecycle Policy for applicable products.
  - [Windows servicing dashboard](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/manage-windows-as-a-service): Provides you with information about computers in your environment, servicing plans, and compliance information.

- Be reactive with notifications, management insights, and reports:

  - [Configuration Manager console notifications](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console-notifications#new-notifications-in-version-2010): Look for in-console notifications about devices with operating systems that are past the end of support date and that are no longer eligible to receive security updates.
  - Management insights

    - [Security](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/management-insights#security): Identify clients with unsupported antimalware client versions or clients running earlier versions of Windows that don't receive security updates by default.
    - [Simplified management](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/management-insights#simplified-management): Identify clients running an unsupported version of Windows or with an earlier version of the Configuration Manager client.

  - Reports:

    - [Data warehouse historical reporting](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/list-of-reports#data-warehouse): View computers that are missing software updates.
    - [OS reports](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/list-of-reports#operating-system): View computers by OS versions and servicing details.
    - [Software Updates compliance reports](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/list-of-reports#software-updates---a-compliance): View software update compliance details.

  - [Power BI sample reports for software updates](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/powerbi-sample-reports): Use Power BI to view software update compliance status.

## Next steps

- [In-place upgrade to Configuration Manager current branch from System Center 2012 Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/upgrade-to-configuration-manager)
- [Plan for migration to Configuration Manager current branch](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-for-migration)
