<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/fresh-start -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: Fresh Start

The *Fresh Start* action removes apps from managed Windows devices, helping you remove preinstalled \(OEM\) apps that typically ship with a new PC.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Clean PC**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to run Fresh Start from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Fresh Start**.
4. Select **Retain user data on this device** to:

   - Keep the device Microsoft Entra joined.
   - Automatically re-enroll the device in mobile device management when a Microsoft Entra ID-enabled user signs in.
   - Preserve the contents of the user's Home folder, while removing apps and settings.


   Important


   If you don't retain user data, the device is restored to the default out-of-box experience \(OOBE\) completed state retaining the built-in administrator account. BYOD devices are removed from Microsoft Entra ID and mobile device management.

5. Select **OK**.

## Reference links

- Configuration service provider \(CSP\) used to initiate the action: [CleanPC CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/cleanpc-csp)
- Microsoft Graph API: [cleanWindowsDevice action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-cleanwindowsdevice)
