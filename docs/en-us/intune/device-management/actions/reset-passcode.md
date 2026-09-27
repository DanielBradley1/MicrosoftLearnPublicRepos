<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/reset-passcode -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# Device action: reset passcode

With the *reset passcode* action in Microsoft Intune, you can remotely reset a device passcode to help users regain access to their devices without requiring a full device wipe. this action is especially useful when a user forgets their passcode or is locked out of their device or work profile.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated \(COSU\)
> - Android Enterprise corporate-owned fully managed \(COBO\)
> - Android Enterprise corporate-owned work profile \(COPE\)
> - Android Enterprise personally-owned work profile \(BYOD\)
> - Android Open Source Project \(AOSP\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote Tasks/Reset Passcode**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## Passcode reset types

When working with Android devices, it's important to understand the two types of passcode resets available:

- **Device-level passcode reset**: The action resets the passcode for the entire device.
- **Work profile passcode reset**: The action resets the passcode for the user's work profile only.

The following table summarizes the passcode reset types based on platform:

| Platform | Device-level passcode reset | Work profile passcode reset |
| --- | :---: | :---: |
| Android Enterprise corporate-owned dedicated \(COSU\) | ✅ | ❌ |
| Android Enterprise corporate-owned fully managed \(COBO\) | ❌ | ✅ |
| Android Enterprise corporate-owned work profile \(COPE\) | ❌ | ✅ |
| Android Enterprise personally-owned work profile \(BYOD\) | ❌ | ✅ |
| Android Open Source Project \(AOSP\) | ✅ | ❌ |

Important

Before initiating a passcode reset, ensure that the passcode requirement is enforced via [device configuration policies](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/ref-android-settings)—otherwise, the reset fails.

## How to reset a passcode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Reset passcode**.
4. A new passcode is presented to the admin.

The new passcode must be entered on the device, and it's displayed in the admin center for seven days.

## User experience

For work profile passcode reset, users get notified to activate their reset passcode. After their passcode is entered, the notification is dismissed.

Note

If the remote lock action fails, confirm that you have a device passcode policy assigned to the device. If the device doesn't have a device passcode assigned, the remote lock action doesn't succeed.

## Reference links

- Microsoft Graph API: [resetPasscode action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-resetpasscode)
