<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-filevault-recovery-key -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: rotate FileVault recovery key

The *rotate FileVault recovery key* action in Microsoft Intune allows IT admins to manually generate a new personal recovery key for a macOS device encrypted with FileVault.

This action is useful when the current key is lost, potentially exposed, or needs to be refreshed for compliance or support reasons.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - macOS \(corporate-owned\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To use this action, make sure devices meet the following requirements:
> 
> - Are encrypted with FileVault using an Intune disk encryption policy.
> - Have the FileVault recovery key escrowed to Intune.
> 
> For more information, see Use [FileVault disk encryption for macOS with Intune](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-filevault-macos).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Rotate filevault key**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to rotate the FileVault recovery key from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Secure** > **Rotate FileVault recovery key**.
4. Select **Yes** to confirm the action.

## Reference links

- Microsoft Graph API: [rotateFileVaultKey action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-rotateFileVaultKey)
