<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/logout-user -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: logout current user

The *logout current user* device action in Microsoft Intune allows IT administrators to remotely sign out the active user from a Shared iPad. this action is useful in environments where multiple users access the same device throughout the day. Logging out the current user helps maintain privacy, ensures session cleanup, and prepares the device for the next user—supporting secure and efficient device turnover in shared-use scenarios.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - iPadOS \(Shared iPad mode only\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Manage shared device users**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to logout the current user from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Logout current user**.

## Reference links

- Microsoft Graph API: [logoutSharedAppleDeviceActiveUser action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-logoutsharedappledeviceactiveuser)
