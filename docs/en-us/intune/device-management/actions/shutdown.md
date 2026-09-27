<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/shutdown -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: shut down

With the *shut down* action, IT administrators can remotely power off managed devices. This action doesn't prompt or warn the user before the device powers down.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - iOS/iPadOS in [Supervised Mode](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-supervised-mode)
> - macOS

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Shut down**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to shut down a device from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Shut down** > **Yes**.

Note

iOS/iPadOS devices that are Passcode-locked will not rejoin a Wi-Fi network after restarting. After restarting, the device might not be able to communicate with the server.

## Reference links

- Microsoft Graph API: [shutDown action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-shutdown)
