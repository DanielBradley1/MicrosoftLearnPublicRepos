<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2207 -->
<!-- Sitemap-Last-Modified: 2023-02-22 -->

# What's new in version 2207 of Configuration Manager current branch

*Applies to: Configuration Manager \(current branch\)*

Update 2207 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2103 or later.  This article summarizes the changes and new features in Configuration Manager, version 2207.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2207](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2207). After you update a site, also review the [Post-update checklist](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2207#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Cloud-attached management

### Use Intune role-based access control \(RBAC\) for tenant attached devices

You can now use Intune role-based access control \(RBAC\) when interacting with tenant attached devices from the Microsoft Intune admin center. For example, when using Intune as the role-based access control authority, a user with Intune's [Help Desk Operator role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview#built-in-roles) doesn't need an assigned security role or additional permissions from Configuration Manager. For more information, see [Intune role-based access control for tenant attached clients](https://learn.microsoft.com/en-us/intune/configmgr/cloud-attach/use-intune-rbac).

### Enhanced security for Configuration Manager administration service

We're introducing a new cloud application with limited access to the administration service. This feature allows cloud management gateway \(CMG\) to segment the admin privileges between a management point, and the administration service. This enables CMG to restrict access to the administration service. This feature gives admins granular access controls through which users can have access to the administration service and to enforce MFA if necessary.

For more information, see [Configure Azure services for use with Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/azure-services-wizard).

### Simplified application deployment approval

An administrator can now approve or deny the request for deploying an application on a device from anywhere they have internet access by selecting a link in the email notification. This feature requires admins to manually add the CMG URL in the Azure Active Directory app as single page application redirect URI.

For more information, see [Create an app registration in Azure AD for your app service app](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/app-approval#to-take-action-from-internet).

### Include and prefer a cloud source for a management point in a default boundary group

Until 2203 current branch, you didn’t have an option to prefer a CMG as a management point in a default boundary group. The clients falling back to a default boundary group could only communicate to non-cloud-based management points.

When a site is initially installed, there's a default site boundary group created for each site, and all the clients use it by default until they're assigned to a custom boundary group.

Starting in Configuration Manager 2207, you can add options via PowerShell to include and prefer cloud sources. For instance, you can set the CMG as the preferred management point for the clients in the default boundary group.

For more information, see [Default site boundary group behavior supports cloud source selection](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/boundary-groups#default-site-boundary-group-behavior-supports-cloud-source-selection).

## Client management

### Granular control over compliance settings evaluation

You can now define a **Script Execution Timeout \(seconds\)** when configuring client settings for compliance settings. The timeout value can be set from a minimum of 60 seconds to a maximum of 600 seconds. This new setting allows you more flexibility for configuration items when you need to run scripts that may exceed the default of 60 seconds.

For more information, see the [compliance settings group of client settings](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-settings#compliance-settings).

## Software updates

### Improved manageability of automatic deployment rules \(ADRs\)

You'll now be able to organize ADRs with folders. This improvement helps you with better categorization and management of ADRs across your organizational hierarchy by having a structured view across your phased deployments. Folder can also be created with PowerShell cmdlets.

For more information, see [Process to create a folder for automatic deployment rules](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/automatically-deploy-software-updates#process-to-add-a-new-deployment-to-an-existing-adr).

### Enhanced control over monthly maintenance windows

Based upon your feedback, we have enhanced monthly maintenance windows scheduling. You can now set monthly maintenance window schedules to better align deployments with the release of monthly software updates by configuring offsets. For example, using an offset of two days after the second Tuesday of the month, sets the maintenance window for Thursday.

For more information, see [How to use maintenance windows in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/use-maintenance-windows).

## Endpoint Protection

### Improved Microsoft Defender for Endpoint \(MDE\) onboarding for Windows Server 2012 R2 and Windows Server 2016

Configuration Manager version 2207 now supports automatic deployment of modern, unified Microsoft Defender for Endpoint for Windows Server 2012 R2 & 2016. Windows Server 2012 and 2016 devices that are targeted with Microsoft Defender for Endpoint onboarding policy will use the unified agent versus the existing Microsoft Monitoring Agent based solution, if configured through Client Settings.

For more information, see [Microsoft Defender for Endpoint onboarding](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/defender-advanced-threat-protection).

### Enhanced protection for untrusted environments

1. Windows Defender Application Guard is now called Microsoft Defender Application Guard in the console.
2. The **General** settings page in the Microsoft Defender Application Guard now allows you to create policies within Configuration Manager to protect your employees using Microsoft Edge and isolated Windows environments.
3. The **Application Behavior** settings page allows you to enable or disable cameras and microphones, along with certificate matching of the thumbprints to the isolated container.
4. The following items were removed:

   - The Enterprise sites can load non-enterprise content, such as third-party plug-in settings, under the **Host interaction** page.
   - The file trust criteria policy, under the **File Management** page.

For more information, see [Create and deploy Microsoft Defender Application Guard policy](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-deploy-application-guard-policy#create-a-policy-and-to-browse-the-available-settings).

## Configuration Manager console

### Improvements to the console

- When performing a search on any node in the console, the search bar will now include a **Path** criteria to show that subfolders in the node are included in the search.

  - The path criteria is informational and can’t be edited.
  - By default, all subfolders will be searched when you perform a search in any node that contains subfolders. You can narrow down the search by selecting the “Current Node” option from the search toolbar.

### Improvements to the dark theme

The dark theme has been available as a pre-release feature since 2203. In this release we've extended the dark theme to additional components such as buttons, context menus, and hyperlinks. Enable this pre-release feature to experience the dark theme.

For more information, see [Console changes and tips](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console-tips#bkmk_2207).

## Other updates

For more information on changes to the Windows PowerShell cmdlets for Configuration Manager, see [version 2207 release notes](https://learn.microsoft.com/en-us/powershell/sccm/2207-release-notes).

## Next steps

At this time, version 2207 is released for the early update ring. To install this update, you need to opt in. For more information, see [Early update ring](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2207#early-update-ring).

When you're ready to install this version, see [Installing updates for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates) and [Checklist for installing update 2207](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2207).

Tip

To install a new site, use a baseline version of Configuration Manager.

Learn more about:

- [Installing new sites](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/installing-sites)
- [Baseline and update versions](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates#bkmk_Baselines)

For known significant issues, see the [Release notes](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/release-notes).

After you update a site, also review the [Post-update checklist](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/checklist-for-installing-update-2207#post-update-checklist).
