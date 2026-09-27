<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/autopilot-reset -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: Autopilot Reset

Use the *Autopilot Reset* action in Intune to prepare a Windows device for reuse while maintaining its Microsoft Entra ID and Intune enrollment. Autopilot Reset removes user data, settings, and apps, and reapplies the original device configuration.

The reset preserves key settings, including Wi-Fi profiles and credentials, allowing the device to reconnect automatically after the reset. Region, language, and keyboard settings are also retained.

Autopilot Reset is designed for scenarios where a device needs to be repurposed or reassigned. It returns the device to a fully configured, IT-approved state without requiring a full reimage.

For more information, see [Windows Autopilot Reset](https://learn.microsoft.com/en-us/autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset).

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
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Wipe**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to use Autopilot reset from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Autopilot reset**.
4. To confirm, select **Yes**.

## Reference links

- Configuration service provider \(CSP\) used to initiate the action: [RemoteWipe CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/remotewipe-csp)
- Microsoft Graph API: [wipe action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-wipe)
