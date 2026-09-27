<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/create-app-groups -->
<!-- Sitemap-Last-Modified: 2023-02-22 -->

# Create application groups

*Applies to: Configuration Manager \(current branch\)*

Create a group of applications that you can send to a user or device collection as a single deployment. The metadata you specify about the app group is seen in Software Center as a single entity. You can order the apps in the group so that the client installs them in a specific order.

Tip

This feature was first introduced in version 1906 as a [pre-release feature](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/pre-release-features). Beginning with version 2111, it's no longer a pre-release feature.

This feature is optional in Configuration Manager, and enabled by default. For more information, see [Enable optional features from updates](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/optional-features).

## Process

1. In the Configuration Manager console, go to the **Software Library** workspace. Expand **Application Management** and select the **Application Group** node.
2. In the Create group in the ribbon, select **Create Application Group**.
3. On the **General Information** page, specify information about the app group.
4. On the **Software Center** page, include information that shows in Software Center.
5. On the **Application Group** page, select **Add**. Select one or more apps for this group. Reorder them using the **Move Up** and **Move Down** actions.
6. Complete the wizard.

Tip

To manage app groups, you need permissions on the **Application Groups** object. The permissions for most administrative operations are the same as on applications.

## Deploy

Deploy the app group using the same process as for an application. For more information, see [Deploy applications](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/deploy-applications). You can deploy an app group to device or user collections. Starting in version 2111, when you deploy an app group as required to a device or user collection, you can specify that it automatically uninstalls when the resource is removed from the collection. For more information, see [Implicit uninstall](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/uninstall-applications#implicit-uninstall).

After you deploy the group:

- If you add a new app to the group, you have to separately distribute the new app content to distribution points.
- If you modify an app in the app group, redistribute the content.

To troubleshoot an app group deployment, use the following log files on the client:

- **AppGroupHandler.log**
- **AppEnforce.log**
- **SettingsAgent.log**

## App approval

Starting in version 2111, you can use the following [app approval](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/app-approval) behaviors:

- Deploy an app group to a user collection and require approval.

  - A user can then request the app group in Software Center.
  - You can approve or deny the user's request for the app group.

- Deploy an app group to a device collection and require approval. The deployment is suspended on the device until you trigger installation via automation. For example, use the [Approve-CMApprovalRequest](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/approve-cmapprovalrequest) PowerShell cmdlet.
- From the Configuration Manager console, when you select a device, there's a new action in the **Device** group of the ribbon to **Install Application Group**. For more information, see [Install applications for a device](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/install-app-for-device).
- When you enable tenant attach, you can view status and take actions on app groups from the Microsoft Intune admin center. For more information, see [Install an application from the admin center](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/applications).

## Known issues

- The following deployment options may not work: alerts, phased deployment, repair.
- You can't use application groups with the **Install Application** task sequence step.
- You can't export or import app groups.
- In version 2103 and earlier, don't include in the group any apps that require restart, or the group deployment may fail.
- In version 2107 and earlier, if you delete an app that's a part of an app group, you'll see the following warning when you next view the properties of the app group: "Unable to load information about all applications in the group." Make a small change to the app group and save it. For example, add a space to the **Administrator comments**. When you save the change, it removes the deleted app from the group. Starting in version 2111, you can't delete an app that's part of an app group.
- In most scenarios, user categories on the app group don't display as filters in Software Center. If the app group is deployed as available to a user collection, the categories display.

## PowerShell

You can create and deploy app groups using Windows PowerShell. For more information, see the following cmdlet articles:

- [Get-CMApplicationGroup](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmapplicationgroup)
- [New-CMApplicationGroup](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/new-cmapplicationgroup)
- [Remove-CMApplicationGroup](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmapplicationgroup)
- [Set-CMApplicationGroup](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/set-cmapplicationgroup)
- [Get-CMApplicationGroupDeployment](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/get-cmapplicationgroupdeployment)
- [New-CMApplicationGroupDeployment](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/new-cmapplicationgroupdeployment)
- [Remove-CMApplicationGroupDeployment](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/remove-cmapplicationgroupdeployment)
- [Set-CMApplicationGroupDeployment](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/set-cmapplicationgroupdeployment)

## Next steps

[Deploy applications](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/deploy-applications)
