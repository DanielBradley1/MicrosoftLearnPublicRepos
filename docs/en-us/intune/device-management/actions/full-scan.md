<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/full-scan -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: full scan

The *full scan* action in Intune lets IT admins trigger a comprehensive malware scan on managed Windows devices using Microsoft Defender Antivirus. It checks all files and running processes, helping detect threats missed by quick scans.

This action is ideal when a device is suspected of compromise or when validating security baselines. Instead of waiting for scheduled scans or relying on user action, admins can launch a full scan directly from the Intune admin center.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Windows defender**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to initiate a full scan from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Microsoft Defender** > **Run full malware scan**.

## Reference links

- Microsoft Graph API: [windowsDefenderScan action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-windowsdefenderscan)
- Configuration service provider \(CSP\) used to initiate the action: [Defender CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/defender-csp)
