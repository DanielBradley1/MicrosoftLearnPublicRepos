<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/suspend-managed-home-screen -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Device action: suspend Managed Home Screen

The *suspend Managed Home Screen* device action in Intune temporarily disables the Managed Home Screen on a device. When the Managed Home Screen is suspended, the device will no longer enforce the Managed Home Screen policies, and the user will have access to the standard home screen and apps.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Android Enterprise corporate-owned Fully Managed \(COBO\)
> - Android Enterprise corporate-owned Dedicated \(COSU\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Temporarily Suspend Managed Home Screen**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To run this action, the **Alarms & Reminders** permission must be granted to the Managed Home Screen.
> 
> For more information, see [Configure permissions for the Managed Home Screen \(MHS\) on Android Enterprise devices using Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-managed-home-screen-permissions-android).

## How to suspend the managed home screen from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Suspend Managed Home Screen**.

## User experience

Once the Managed Home Screen is suspended, the device will no longer enforce the Managed Home Screen policies, and the user will have access to the standard home screen and apps.

## Reference links

- Microsoft Graph API: [managedDevice resource type](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice)
- Microsoft Graph API: [suspendManagedHomeScreen action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-suspendmanagedhomescreen)
