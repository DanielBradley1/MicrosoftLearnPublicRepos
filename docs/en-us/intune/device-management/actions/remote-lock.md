<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/remote-lock -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Device action: remote lock

The *remote lock* device action locks a managed device so the user must enter the existing passcode or PIN to continue. Use this action when a device is misplaced, left unattended, or suspected of unauthorized use without wiping data or removing enrollment.

Important

Remote lock is only effective if a passcode or PIN is already set:

- If no passcode exists, the screen may just turn off and the user can still access the device.
- Enforce a passcode policy before relying on this action.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned dedicated \(COSU\)
> - Android Enterprise corporate-owned fully managed \(COBO\)
> - Android Enterprise corporate-owned work profile \(COPE\)
> - Android Open Source Project \(AOSP\)
> - iOS/iPadOS
> - macOS
> - visionOS 2.0+

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, at a minimum, use an account that has one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Remote lock**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to remote lock a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Remote lock**.

3. Set a six-digit recovery PIN.

Note

The recovery PIN is shown on the device overview pane for up to 30 days, or until another device action is sent. Record it securely; it can't be retrieved afterward. Don't resend remote lock to the same macOS device until that PIN is used—additional attempts show a **Failed** status in reporting.

## Reference links

- Microsoft Graph API: [remoteLock action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-remotelock)
