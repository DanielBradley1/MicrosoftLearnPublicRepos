<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/overview -->
<!-- Sitemap-Last-Modified: 2026-09-28 -->

# Device management in Microsoft Intune

After devices enroll in Microsoft Intune, you manage them from the **Devices** area of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). From one place, you can review the devices in your organization, inspect the information Intune collects from each one, run remote actions, deploy scripts, monitor health through reports, and connect Intune to other services.

This article introduces the **Devices** area and explains how its sections are organized, so you know where to go for a given task. For step-by-step guidance, follow the links to the detailed articles in each section.

## Find your managed devices

To view the devices you manage, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices). The **All devices** list shows every enrolled device, along with key columns such as operating system, ownership, compliance state, and last check-in. You can filter and sort the list, or select a platform-specific view \(for example, [**Windows**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesWindowsMenu/%7E/windowsDevices)\) to narrow the results.

Select any device in the list to open its device details page.

## Understand the device page

When you select a device, its **Overview** page opens with a command bar of [device actions](https://learn.microsoft.com/en-us/intune/device-management/actions/), an **Essentials** summary of key identifiers \(compliance state, ownership, model, OS, serial number, Intune device name, scope tags, and primary user\), and these tabs:

- **Monitor** — the status of the device's configuration policies, compliance, managed apps, and Endpoint Analytics score.
- **Properties** — the settings you can edit. See [Edit device properties](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/edit-device-properties).
- **Device details** — read-only hardware and inventory information. See [View device details](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/device-details).
- **Device action status** — the requested, in-progress, and recently completed [device actions](https://learn.microsoft.com/en-us/intune/device-management/actions/) for the device.

A navigation pane provides more views, grouped under **Tools** \(such as device inventory, device query, BitLocker recovery keys, and remediations\) and **Reports** \(such as discovered apps, app configuration, device compliance, device configuration, and managed apps\).

## Sections of the Devices area

The **Devices** area organizes device management into the following sections.

### Device actions

Respond to devices remotely, without physical access—wipe or retire a lost device, sync policies, restart, run a malware scan, rotate recovery keys, and more. Available actions depend on the platform and ownership. For the full list, see [Device actions](https://learn.microsoft.com/en-us/intune/device-management/actions/).

### Device inventory and organization

Review the data Intune collects from each device, and organize your devices for management:

- [View device details](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/device-details) and hardware inventory.
- [View ChromeOS device information](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/chrome-enterprise-details).
- [Edit device properties](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/edit-device-properties), such as ownership, notes, and scope tags.
- [Rename a device](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/rename-device).
- [Change a device's primary user](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/find-primary-user).
- [Create and assign device categories](https://learn.microsoft.com/en-us/intune/device-management/create-device-categories).
- [Manage specialty devices](https://learn.microsoft.com/en-us/intune/device-management/specialty-devices).

### Scripts and remediations

Extend management beyond built-in settings by running your own code on managed devices. Use the [Intune Management Extension](https://learn.microsoft.com/en-us/intune/device-management/tools/management-extension-windows) to add [PowerShell scripts for Windows](https://learn.microsoft.com/en-us/intune/device-management/tools/run-powershell-scripts-windows) or [shell scripts for macOS](https://learn.microsoft.com/en-us/intune/device-management/tools/run-shell-scripts-macos), and use [remediations](https://learn.microsoft.com/en-us/intune/device-management/tools/deploy-remediations) to detect and fix issues at scale.

### Reports

Monitor the health, compliance, and activity of your devices. Start with the [reports overview](https://learn.microsoft.com/en-us/intune/device-management/reports/overview) or [export report data by using Graph APIs](https://learn.microsoft.com/en-us/intune/device-management/reports/export-graph-apis).

### Integrations

Connect Intune to other services and tools, including the [Surface Management Portal](https://learn.microsoft.com/en-us/intune/device-management/tools/surface-management-portal), [ServiceNow](https://learn.microsoft.com/en-us/intune/device-management/tools/setup-servicenow), and [TeamViewer](https://learn.microsoft.com/en-us/intune/device-management/tools/setup-teamviewer).

## Next steps

- [View device details](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/device-details)
- [Device actions](https://learn.microsoft.com/en-us/intune/device-management/actions/)
- [Microsoft Intune reports](https://learn.microsoft.com/en-us/intune/device-management/reports/overview)
