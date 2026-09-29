<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-protection-update-schedule-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# Manage the schedule for when protection updates should be downloaded and applied

Important

Customers who applied the March 2022 Microsoft Defender engine update \(**1.1.19100.5**\) might have encountered high resource utilization \(CPU and/or memory\). Microsoft has released an update \(**1.1.19200.5**\) that resolves the bugs introduced in the earlier version. Customers are recommended to update to Microsoft Defender Antivirus Engine build **1.1.19200.5**. To ensure any performance issues are fully fixed, it's recommended to reboot machines after applying Microsoft Defender Antivirus Engine update 1.1.19200.5. For more information, see [Monthly platform and engine versions](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-releases#microsoft-defender-antivirus-releases).

This article explains how to configure scheduled protection updates for Microsoft Defender Antivirus using Configuration Manager, Group Policy, PowerShell, or WMI. Microsoft Defender Antivirus lets you determine when it should look for and download updates.

You can schedule updates for your endpoints by:

- Specifying the day of the week to check for protection updates
- Specifying the interval to check for protection updates
- Specifying the time to check for protection updates

You can also randomize the times when each endpoint checks and downloads protection updates. For more information, see [About schedule scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans).

## Prerequisites

Before you configure scheduled protection updates, make sure the following requirements are met.

### Supported operating systems

The following operating systems are supported:

- Windows

## Use Configuration Manager to schedule protection updates

To schedule protection updates by using Configuration Manager, perform the following steps:

1. On your Microsoft Configuration Manager console, open the antimalware policy you want to change \(select **Assets and Compliance** in the navigation pane on the left, then expand the tree to **Overview** > **Endpoint Protection** > **Antimalware Policies**\)
2. Go to the **Security intelligence updates** section.
3. To check and download updates at a certain time:

   - Set **Check for Endpoint Protection security intelligence updates at a specific interval...** to **0**.
   - Set **Check for Endpoint Protection security intelligence updates daily at...** to the time when updates should be checked.

4. To check and download updates on a continual interval, Set **Check for Endpoint Protection security intelligence updates at a specific interval...** to the number of hours that should occur between updates.
5. [Deploy the updated policy as usual](https://learn.microsoft.com/en-us/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## Use Group Policy to schedule protection updates

Important

By default, the update schedule day \(`SignatureScheduleDay`\) is set to "8" \(no day specified\) and the update check interval \(`SignatureUpdateInterval`\) is set to "0" \(disabled\), so Microsoft Defender Antivirus doesn't schedule protection updates automatically. Enabling `SignatureScheduleDay` or `SignatureUpdateInterval` overrides that default.

To schedule protection updates by using Group Policy, perform the following steps:

1. In Centralized Group Policy, open the [Group Policy Management Console \(GPMC\)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console) on your Group Policy management computer.
2. In the GPMC console tree, expand Group Policy Objects in the forest and domain containing the GPO you want to edit.
3. Right-click the GPO, and then select **Edit**.
4. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Security Intelligence Updates**.

   Note

   Group Policy paths before Windows 10, version 2004 \(May 2020\) might use *Windows* Defender Antivirus instead of *Microsoft* Defender Antivirus. Group Policy paths before Windows 10, version 1909 \(November 2019\) might use *Signature Updates* instead of *Security Intelligence Updates*. The older and newer names refer to the same policy locations.
5. In the details pane of **Security Intelligence Updates**, the available settings are:

   - [Specify the day of the week to check for security intelligence updates](#enable-and-configure-the-security-intelligence-update-day)
   - [Specify the interval to check for security intelligence updates](#enable-and-configure-the-security-intelligence-update-interval)
   - [Specify the time to check for security intelligence updates](#enable-and-configure-the-security-intelligence-update-time)


   To open and configure a security intelligence update schedule setting, use any of the following methods:


   - Double-click the setting.
   - Right-click the setting, and then select **Edit**.
   - Select the setting, and then select **Action** > **Edit**.

Tip

You can also configure Group Policy locally on individual devices by using the Local Group Policy Editor \(`gpedit.msc`\). Navigate to the same path: **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Security Intelligence Updates**.

### Enable and configure the security intelligence update day

1. In the details pane of **Security Intelligence Updates**, open the **Specify the day of the week to check for security intelligence updates** setting.
2. In the setting window that opens, configure the following options:

   1. Select **Enabled**.
   2. **Specify the day of the week to check for security intelligence updates** in the **Options** section: Select the day of the week to check for updates.


   When you're finished, select **OK**.

### Enable and configure the security intelligence update interval

1. In the details pane of **Security Intelligence Updates**, open the **Specify the interval to check for security intelligence updates** setting.
2. In the setting window that opens, configure the following options:

   1. Select **Enabled**.
   2. **Specify the interval to check for security intelligence updates** in the **Options** section: Enter a value from `1` to `24` for the number of hours between updates.


   When you're finished, select **OK**.

### Enable and configure the security intelligence update time

1. In the details pane of **Security Intelligence Updates**, open the **Specify the time to check for security intelligence updates** setting.
2. In the setting window that opens, configure the following options:

   1. Select **Enabled**.
   2. **Specify the time to check for security intelligence updates** in the **Options** section: Enter the number of minutes after midnight when updates should be checked. For example, enter `120` for 2:00 AM. The schedule is based on the local time of the endpoint.


   When you're finished, select **OK**.

## Use PowerShell cmdlets to schedule protection updates

Use the following cmdlets to set the day, time, and interval for protection update checks:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

See [Use PowerShell cmdlets to configure and run Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus) and [Defender Antivirus cmdlets](https://learn.microsoft.com/en-us/powershell/module/defender/) for more information on how to use PowerShell with Microsoft Defender Antivirus.

## Use Windows Management Instrumentation \(WMI\) to schedule protection updates

Use the [**Set** method of the **MSFT\_MpPreference**](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/legacy/dn455323\(v=vs.85\)) class for the following properties to configure the signature update schedule day, time, and interval:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

See the following for more information and allowed parameters:

- [Windows Defender WMIv2 APIs](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)

## Related content

- [Deploy Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/deploy-manage-report-microsoft-defender-antivirus)
- [Manage Microsoft Defender Antivirus updates and apply baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates)
- [Manage updates for endpoints that are out of date](https://learn.microsoft.com/en-us/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus)
- [Manage event-based forced updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-event-based-updates-microsoft-defender-antivirus)
- [Manage updates for mobile devices and virtual machines \(VMs\)](https://learn.microsoft.com/en-us/defender-endpoint/manage-updates-mobile-devices-vms-microsoft-defender-antivirus)
- [Microsoft Defender Antivirus in Windows 10 and 11](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)
