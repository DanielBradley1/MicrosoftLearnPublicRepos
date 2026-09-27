<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2211 -->
<!-- Sitemap-Last-Modified: 2023-03-10 -->

# What's new in version 2211 of Configuration Manager current branch

*Applies to: Configuration Manager \(current branch\)*

Update 2211 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2107 or later.  This article summarizes the changes and new features in Configuration Manager, version 2211.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2211](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2211). After you update a site, also review the [Post-update checklist](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2211#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Cloud-attached management

### Improvements to Cloud Sync \(Collections to Azure Active Directory Group Synchronization\) feature

Starting Configuration Manager version 2211, the scalability of this feature has been improved with better throttling and error handling. Additionally, dedicated dashboards for user collections and device collections are added in Monitoring workspace to show Cloud Sync status. The dashboard displays the Cloud Sync status per collection with the mapped Azure AD group, total member count, synced member count, status \(success, failed, in progress\) and last sync details.

For more information, see [Synchronize collections to Azure Active Directory Group](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/synchronize-collections-aad-group).

## Site infrastructure

### Network Access Account \(NAA\) account usage alert

If your site is configured with NAA account, you see this new prerequisite warning added. To improve the security of distribution points configured with NAA account, review the existing accounts and their relevant permissions. If it has more than minimal required permission, then remove and add a minimal permission account. Don't configure any administrator level permission accounts on the NAA. If the site server is configured with HTTPS / EHTTP, it's recommended to remove the NAA account, which is unused.

For more information, see the description of this [permissions-for-the-network-access-account](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/accounts#permissions-for-the-network-access-account)

### Distribution point content migration

DP content migration support is now available for migrating content from one DP to another DP using PowerShell cmdlets. You can also monitor the DP migration status using these PowerShell cmdlets.

For more information, see the description of this [content migration](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)

## Software Center

### Featured Apps in Software Center

We're now adding the **Featured** tab in Software Center where we are displaying the featured apps. Using this, IT admins can mark apps as "featured" and encourage end users to use the app. Currently, this feature is available only for "User Available" apps. Also, admins can make the **Featured** tab of Software Center as the default tab from Client Settings.

For more information, see the [Software Center in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/software-center).

## Configuration Manager console

### Enhancements in console search experience

When performing a search on any node in the console, the hint text in the search bar will now indicate the scope of the search. Also, search experience related issues have been fixed.

- By default, all subfolders are searched when you perform a search in any node that contains subfolders. You can narrow down the search by selecting the “Current Node” option from the search toolbar.
- If you want to expand the search to include all nodes, then select the “All Objects” button in the ribbon.

For more information, see [Console changes and tips](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console-tips#configuration-manager-console-changes-and-tips).

### Dark theme is now extended to more dashboards

We've extended the dark theme to other components such as buttons, context menus, and hyperlinks. Enable this feature to experience the dark theme.

In this release we've extended the dark theme to more dashboards, which previously didn't display the dark theme correctly. For example, the O365 Updates Dashboard, PCM Dashboard, and Health Attestation dashboard will now display according to the dark theme, when it's enabled. Pop-ups in the Health attestation dashboard will now adhere to the dark theme.

For more information, see [Dark theme for the console](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console#bkmk_dark).

## Other updates

### Resolved duplicate entries for co-managed device in Intune portal

Previously, device entities of the co-managed devices appeared as two separate entries on Intune portal. One entry corresponding to Intune and another corresponding to ConfigMgr appeared after enrollment. The entries were permanent in some cases. Various scenarios like device entity counts and policy targeting were impacted. The entries were duplicated because Intune isn't aware of the AAD ID of devices coming from ConfigMgr. Intune becomes aware only after the daily discovery cycle runs and reports to Intune via CMGS.

The issue is fixed by propagating correct AAD device ID from ConfigMgr during Intune enrollment. This leads to merged entities for co-managed devices in a short period of time \(30-40 mins\). We no longer have to wait for discovery cycle to run.

### Starting with this version, the Configuration Manager client doesn’t support the following operating system

- Windows Server 2008 R2 SP1 Extended Security Updates \(ESU Azure Only\)
- Windows Server 2008 SP2 Extended Security Updates \(ESU Azure Only\)

If you're running this operating system on machines in your environment, they shouldn't be upgraded to the 2211 version of the Configuration Manager client. For more information on supported clients and devices, see [supported-operating-systems-for-clients-and-devices](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).

## Next steps

As of December 19, 2022, version 2211 is globally available for all customers to install.

When you're ready to install this version, see [Installing updates for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates) and [Checklist for installing update 2211](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2211).

Tip

To install a new site, use a baseline version of Configuration Manager.

Learn more about:

- [Installing new sites](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/installing-sites)
- [Baseline and update versions](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates#bkmk_Baselines)

For known significant issues, see the [Release notes](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/release-notes).

After you update a site, also review the [Post-update checklist](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2211#post-update-checklist).
