<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/quick-scan -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: quick scan

The *quick scan* action in Microsoft Intune enables IT administrators to start a targeted malware scan on managed Windows devices by using Microsoft Defender Antivirus. This action scans key system areas where threats commonly appear—such as memory, startup folders, and running processes—without performing a full system sweep.

Quick scans are especially useful for routine health checks, validating recent policy deployments, or responding to low-risk alerts. By triggering a scan remotely from the Intune admin center, IT teams can quickly assess device health and ensure protection is up to date—without waiting for the next scheduled scan or relying on user intervention.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platform:
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

## How to initiate a quick scan from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Quick scan**.

## Reference links

- Microsoft Graph API: [windowsDefenderScan action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-windowsdefenderscan)
- Configuration service provider \(CSP\) used to initiate the action: [Defender CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/defender-csp)
