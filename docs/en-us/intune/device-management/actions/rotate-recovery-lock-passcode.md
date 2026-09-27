<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-recovery-lock-passcode -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: rotate Recovery Lock passcode

Note

This feature is gradually rolling out and may not yet be available in your tenant. Full availability is expected by late April 2026.

Recovery Lock protects macOS devices by requiring a password to access recoveryOS. By using Intune, administrators can remotely rotate this passcode to keep access to the recovery environment secure and controlled.

When you use the **Rotate Recovery Lock Passcode** action, Intune creates a new passcode to replace the current one. The new passcode shows up in the admin center and is the only valid credential for accessing the device's recovery options.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - macOS in supervised mode, running macOS 11.5 or later on Apple silicon \(Intel-based Macs aren't supported\).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - Intune administrator
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks / Rotate macOS Recovery Lock password**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To run this action, the device must be configured with a policy setting that enables the Recovery Lock feature.
> 
> For more information, see [Create the Recovery Lock policy](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-recovery-lock-macos#create-the-recovery-lock-policy).

## How to rotate the macOS Recovery Lock passcode from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Rotate Recovery Lock Passcode**.
4. Select **Yes** to confirm the action. Intune generates a new Recovery Lock passcode.

Note

Confirming this action starts the passcode rotation process.  
The new Recovery Lock passcode is applied to the device the next time the device successfully checks in with Intune.  
If the device is offline or not checking in, the existing Recovery Lock passcode remains in effect until the device checks in.

To view the new passcode, select **Passwords and keys** > **View Recovery Lock Passcode**.

## Reference links

- Microsoft Graph API: [managedDevice resource type](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice)
