<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/play-lost-mode-sound -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: play lost mode sound

Microsoft Intune provides platform-specific device actions to help locate a lost or misplaced device by triggering an audible alert—even if the device is locked or silenced.

- On iOS/iPadOS, use the *play Lost Mode sound* action. This action is available when the device is in [Lost Mode](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode) and supervised.
- On Android Enterprise devices, use the *Play lost device sound* action. This action is supported for corporate-owned devices enrolled with Android Enterprise.

These device actions are especially useful in environments where devices are shared or frequently moved—such as classrooms, labs, or enterprise workspaces. Playing a sound helps users or administrators locate the device quickly and securely, supporting recovery efforts when a device is lost.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated \(COSU\)
> - Android Enterprise corporate-owned fully managed \(COBO\)
> - Android Enterprise corporate-owned work profile \(COPE\)
> - iOS/iPadOS in [Supervised Mode](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/enable-supervised-mode)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To use this action, make sure devices meet the following requirements:
> 
> - Enable [Lost Mode](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode)

> To use this action, make sure devices meet the following requirements:
> 
> - Intune app is installed.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Play sound to locate lost devices**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to play lost mode sound from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.

3. At the top of the device overview pane, locate the row of action icons. Select **Locate** > **Play Lost Mode sound \(supervised only\)**.

3. At the top of the device overview pane, locate the row of action icons. Select **Locate** > **Play lost device sound**.

4. Select the duration for the sound to play on the device, and then select **Yes**.

## User experience

The sound plays until the user disables the sound or the duration you set expires.

If system notifications are enabled, the device displays a notification with a **Stop Sound** button. The alert plays for the configured duration or until a user on the device manually stops it using the notification.

Notification behavior might vary based on system settings. To configure system notifications, see [Android Enterprise device settings to allow or restrict features using Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise).

## Reference links

- Microsoft Graph API: [playLostModeSound action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-playlostmodesound)
