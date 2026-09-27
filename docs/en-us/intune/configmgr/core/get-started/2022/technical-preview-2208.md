<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2208 -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Features in Configuration Manager technical preview version 2208

*Applies to: Configuration Manager \(technical preview branch\)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2208. Install this version to update and add new features to your technical preview site.

Review the [technical preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Intune role-based access control \(RBAC\) for tenant attached devices

You can now use Intune role-based access control \(RBAC\) when interacting with tenant attached devices from the Microsoft Intune admin center. For example, when using Intune as the role-based access control authority, a user with Intune's [Help Desk Operator role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview#built-in-roles) doesn't need an assigned security role or additional permissions from Configuration Manager. For more information, see [Intune role-based access control for tenant attached clients.](https://learn.microsoft.com/en-us/intune/configmgr/cloud-attach/use-intune-rbac)

## Dark theme is now extended to more dashboards

In this release, the dark theme has been extended to more dashboards, which previously didn't display the dark theme correctly. For example, the Office 365 Updates Dashboard, PCM Dashboard, and Health Attestation dashboard will now display according to the dark theme, when it's enabled.

Enable this prerelease feature to experience the dark theme. For more information, see [Dark theme for the console.](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console)

## Issues that are fixed

If the osdinjection.xml file is directly modified, it isn't correctly preserved updating to a new Configuration Manager version. Example modifications include adding support for more binaries or for an alternate content provider \(ACP\). When this issue occurs, operating system deployment task sequences fail to resolve required dependencies. The smsts.log file contains the following error.

`Failed to load TSCore.dll Code (0x8007007E).`

## Next steps

For more information about installing or updating the technical preview branch, see [Technical preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview).

For more information about the different branches of Configuration Manager, see [Which branch of Configuration Manager should I use?](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/which-branch-should-i-use).
