<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2204 -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Features in Configuration Manager technical preview version 2204

*Applies to: Configuration Manager \(technical preview branch\)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2204. Install this version to update and add new features to your technical preview site.

Review the [technical preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Administration Service Management option

When configuring Azure Services, a new option called **Administration Service Management** is now added for enhanced security. Selecting this option allows administrators to segment their admin privileges between [cloud management gateway \(CMG\)](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/overview) and [administration service](https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/overview). By enabling this option, access is restricted to only administration service endpoints. Configuration Management clients will authenticate to the site using Microsoft Entra ID.

![Screenshot of administration service management option in the Azure Service Wizard.](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/media/12952905-administration-service-management-azure-services.png)

### Try it out!

Try to complete the tasks. Then send [Feedback](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/product-feedback) with your thoughts on the feature.

Generate a Microsoft Entra token and call the administration service by using a PowerShell script. The sample script and details can be found in the [Microsoft/configmgr-hub GitHub repository](https://aka.ms/cmadminservicetokensample).

## Folders for automatic deployment rules \(ADRs\)

Admins can now organize ADRs by using folders. This change allows for better categorization and management of ADRs. Folder management for ADRs is also supported with PowerShell cmdlets.

[![Screenshot of right-click menu displaying folder options for the automatic deployment rules node.](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/media/13507410-sum-adrdeployment.png)](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/media/13507410-sum-adrdeployment.png#lightbox)

### Try it out!

Try to complete the tasks. Then send [Feedback](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/product-feedback) with your thoughts on the feature.

1. Open the Configuration Manager console, go to the **Software Library** workspace, and then go to **Automatic Deployment Rules**.
2. From the ribbon or right-click menu, and in the **Automatic Deployment Rules** select from the following options:

   - **Create Folder**
   - **Delete Folder**
   - **Rename Folder**
   - **Move Folders**
   - **Set Security Scopes**

## Next steps

For more information about installing or updating the technical preview branch, see [Technical preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview).

For more information about the different branches of Configuration Manager, see [Which branch of Configuration Manager should I use?](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/which-branch-should-i-use).
