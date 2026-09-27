<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2409 -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# What's new in version 2409 of Configuration Manager current branch

*Applies to: Configuration Manager \(current branch\)*

Update 2409 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2309 or later.  This article summarizes the changes and new features in Configuration Manager, version 2409.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2409](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2409). After you update a site, also review the [Post-update checklist](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2409#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Site infrastructure

### Configuration Manager now supports SQL Extended Protection for Authentication

Configuration Manager now supports SQL extended protection for authentication. It's a security feature that enhances protection against MITM attacks, making SQL server more secure when connections are made using extended protection. These enhancements collectively reduce the risk of unauthorized access and protect sensitive data managed by the SQL Server database engine.

For more information, see [Connect to the Database Engine Using Extended Protection](https://learn.microsoft.com/en-us/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection).

### Introducing Centralized Search - Desired Workspace Selection

The centralized search box now enables the option to select the desired workspace for searching. Users can easily refine their search results by selecting the desired workspace from the dropdown menu.

[![Screenshot of centralized search workspace selection in console.](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/media/27679763-search-workspace.png)](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/media/27679763-search-workspace.png#lightbox)

### Configuration Manager does not support SQL Server 2012 and 2014

Starting with version 2409, Configuration Manager no longer supports SQL Server 2012 and 2014. Upgrade to the latest SQL Server version or at least SQL Server 2016. If you don't upgrade, CM upgrades are blocked, and you see an error during the prereq check. For more information, see [Supported SQL Server versions for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-sql-server-versions).

### Operating System support added for Windows 11 24H2 and Windows Server 2025

With this version of Configuration Manager, support is added for Windows 11 24H2 and Windows Server 2025.

- Windows 11 24H2 & Windows Server 2025 are added to the Product lifecycle dashboard and supported platform.
- Windows 11 24H2 & Windows Server 2025 client support is added.
- Boot image creation in CM on Windows Server 2025 now supports latest Windows ADK.
- Windows upgrade readiness dashboard now supports Windows 11 24H2 for upgrading clients.

Note

Windows Server and Windows 11 24H2 do not support Firewall Rules. This will result in a non-compliant status in the Configuration Manager applet.

### Software metering support in Arm64 devices

The Configuration Manager now supports Software metering for Arm64 devices. Software metering is used to monitor Windows PC desktop apps with a filename ending in .exe. For more information, see [Software metering in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/monitor-app-usage-with-software-metering).

## OS deployment

### BitLocker support in Arm64 devices

Configuration Manager now supports BitLocker task sequence steps for Arm64 devices. In BitLocker Management, policies that include OS drive encryption with a TPM protector and fixed drive encryption with the Auto-Unlock option are supported on Arm64 devices.

For more information, see [Bitlocker Supported configurations](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/bitlocker-management#supported-configurations).

## Cloud-attached management

### CMG Entra Application secret key renewal

The 'Renew Secret Key' feature now opens a dialog with four options for the validity period. This update also prevents applications older than 800 days \(approximately two years\) from renewing their secret keys. The same options are available when creating a new app.

![Screenshot of secret window selection in console.](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/media/27297018-secret-window.png)

Sign in using the tenant [Microsoft Entra Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) credentials and then click on the **Renew** button.

Important

The [Microsoft Entra Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/fundamentals-of-role-based-administration).

### CMG Enhanced security option

CMG Setup now uses managed Identities and third-party **Server App** to interact with CMG's Azure Storage account, instead of storage account keys.

- Hence storage account key access is disabled for new CMG setup.
- For sessions upgrading from earlier versions to 2409, the 'CMG enhanced security' button is shown as enabled.

  [![Screenshot of Cmg enhanced window selection in console.](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/media/27297018-cmg-enhanced.png)](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/media/27297018-cmg-enhanced.png#lightbox)

## Known Issues

- Upgrade SQL 2012 or 2014 Express, Standard, Enterprise edition to SQl 2016 or latest version. **VC++ Redistributable Version** need to be upgraded to latest version on **Secondary sites**. [Download Latest Microsoft Visual C++ Redistributable Version](https://aka.ms/vs/17/release/vc_redist.x64.exe).

## Other Updates

### Performance Enhancement of policy processing and collection evaluation

The performance of policy processing and collection evaluation has been enhanced. Previously, blocking chains from sp\_ProcessPolicyChanges, called by PolicyPv, would run for hours, disrupting multiple workloads including collection management and policy processing.

## Deprecated features

Learn about support changes before they're implemented in [removed and deprecated items](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated).

- MDT Integration with CM and Standalone is no longer supported with Configuration Manager deprecation first announced in December 2024 and planned end of support the first release after Oct 10, 2025. Customers should remove MDT Task sequence steps, followed by removing MDT integration, to avoid TS corruption and modification failures.

For more information, see [Removed and deprecated features for Configuration Manager.](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

## Next steps

As of December 16, 2024, version 2409 is globally available for all customers to install.

Note

For exisiting Fast ring current branch 2409 customers, you will see Slow ring upgrade package in console. Install 2409 Slow ring package to be in production current branch.

When you're ready to install this version, see [Installing updates for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates) and [Checklist for installing update 2409](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2409).

Tip

To install a new site, use a baseline version of Configuration Manager.

Learn more about:

- [Installing new sites](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/installing-sites)
- [Baseline and update versions](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates#bkmk_Baselines)

For known significant issues, see the [Release notes](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/release-notes).

After you update a site, also review the [Post-update checklist](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2409#post-update-checklist).
