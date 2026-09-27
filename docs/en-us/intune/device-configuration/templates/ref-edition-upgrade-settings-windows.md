<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-edition-upgrade-settings-windows -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Windows device settings to upgrade editions or enable S mode in Intune

Note

Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/).

Microsoft Intune includes many settings to help manage and protect your devices. This article describes some of the settings to upgrade Windows client editions, or switch out of S mode on Windows devices. Create these settings in an upgrade configuration profile in Intune and assign or deploy the profile to devices.

As part of your mobile device management \(MDM\) solution, use these settings to control the Windows client edition and Windows 10 S mode options for your Windows devices.

For more information on this feature, see [Upgrade Windows editions or enable S mode](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-edition-upgrade-windows).

For information on other options to upgrade Windows editions, see [Windows edition upgrade](https://learn.microsoft.com/en-us/windows/deployment/upgrade/windows-10-edition-upgrades).

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This feature supports the following platform:
> 
> - Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To configure this policy and start collecting inventory data from devices, use an account with at least one of the following roles:
> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> - Create a [Windows edition upgrade and mode switch device configuration profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-edition-upgrade-windows#create-the-profile).

## Edition upgrade

- **Edition to upgrade to**: Select the Windows edition that you want to upgrade to. The devices targeted by this policy upgrade to the edition you choose. When set to **Not configuration**, Intune doesn't change or update this setting.
- **Product Key**: Enter the product key that you received from Microsoft. After you create the policy with the product key, you can't update the key. For security reasons, the key is hidden. To change the product key, enter the entire key again.
- **License File**: For **Windows Holographic for Business**, browse and select the license file you received from Microsoft. This license file includes license information for the editions you're upgrading the devices to.

## Mode switch

- **Switch out of S mode**: Switches the device out of S mode. Your options:

  - **No configuration**: Intune doesn't change or update this setting. By default, the S mode device might stay in S mode. User can switch the device out of S mode.
  - **Keep in S mode**: Prevents users from switching the device out of S mode.
  - **Switch**: Allows users to switch the device out of S mode.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile), and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- Create edition upgrade profiles for [Windows Holographic for Business](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-holographic-upgrade-settings) devices.
