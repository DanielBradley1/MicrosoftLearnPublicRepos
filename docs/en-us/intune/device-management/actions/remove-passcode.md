<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/remove-passcode -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Device action: remove passcode

By using the *remove passcode* action in Microsoft Intune, you can remotely remove a device passcode. This action helps users regain access to their devices without requiring a full device wipe. this action is especially useful when a user forgets their passcode or is locked out of their device.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - iOS/iPadOS
> - visionOS 1.1+

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote Tasks/Reset Passcode**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to remove a passcode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Secure** > **Remove passcode**.

## User experience

After the passcode is removed, if there's a passcode policy set, the device prompts the user to set a new passcode in Settings.

Important

If the **Remove passcode** action fails, Intune might have stored the wrong unlock token. You need to **Wipe** the device to regain access.

## Reference links

- Microsoft Graph API: [resetPasscode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-resetpasscode)
