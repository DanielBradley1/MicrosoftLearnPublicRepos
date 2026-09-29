<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans-group-policy -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Schedule antivirus scans using Group Policy

This article describes how to configure scheduled scans using Group Policy. Use Group Policy when you manage Windows endpoints in an Active Directory domain and want centralized control over scan timing, frequency, and CPU usage. The settings covered include daily and weekly scan schedules, CPU throttling, randomization, and remediation scans. To learn more about scheduling scans and about scan types, see [About scheduled quick or full Microsoft Defender Antivirus scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans).

## Prerequisites

Before you configure scheduled scans, make sure your environment meets the following requirements.

### Supported operating systems

This feature is supported on the following operating systems:

- Windows

### Additional requirements

- A Group Policy management machine with the Group Policy Editor installed.
- Permission to create or edit Group Policy Objects for the target organizational units.

## Configure antivirus scans using Group Policy

To configure scheduled antivirus scans using Group Policy, follow these steps:

1. On your Group Policy management machine, in the Group Policy Editor, go to **Computer configuration** > **Administrative Templates** > **Windows Components** > **Microsoft Defender Antivirus** > **Scan**.
2. Right-click the Group Policy Object you want to configure, and then select **Edit**.
3. Specify the settings for the Group Policy Object, and then select **OK**.
4. Repeat steps 1-3 for each setting you want to configure.
5. Deploy your Group Policy Object as you normally do. If you need help with Group Policy Objects, see [Create a Group Policy Object](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj717274\(v=ws.11\)).

Note

When configuring scheduled scans, the setting **Start the scheduled scan only when computer is on but not in use** \(which is enabled by default\) can affect the expected scheduled time by requiring the machine to be idle first. For weekly scans, the default behavior on Windows Server and Windows 10 and later, is to scan outside of the automatic maintenance when the machine is idle. To stop weekly scans from waiting for the machine to be idle, disable "Start the scheduled scan only when computer is on but not in use" \(**ScanOnlyIfIdle**\), and then define a schedule.

For more information, see the [Manage when protection updates should be downloaded and applied](https://learn.microsoft.com/en-us/defender-endpoint/manage-protection-update-schedule-microsoft-defender-antivirus) and [Prevent or allow users to locally modify policy settings](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus) articles.

## Group Policy settings for scheduling daily scans \(quick\)

The following table lists the Group Policy settings for scheduling daily quick scans:

| Location | Setting | Description | Default setting \(if not configured\) |
| --- | --- | --- | --- |
| Scan | Specify the daily interval for running quick scans. | Specify the number of hours that should pass before the next quick scan is performed. For example, to run every two hours, enter **2**, for once a day, enter **24**. Enter **0** to never run a daily quick scan. | Never |
| Scan | Specify the time for a daily quick scan | Specify the number of minutes after midnight \(for example, enter **60** for 1 AM.\) If this setting is set to 0, daily quick scans don't run. | 120 \(2 AM\) |

Tip

When scheduling a scan, depending on your environment, if your client devices are shutdown after-hours, you might want to consider setting the daily quick scans during lunch time \(720\).

## Group Policy settings for scheduling weekly scans \(quick or full\)

The following table lists the Group Policy settings for scheduling weekly quick or full scans:

| Location | Setting | Description | Default setting \(if not configured\) |
| --- | --- | --- | --- |
| Scan | Specify the scan type to use for a scheduled scan | Quick scan |  |
| Scan | Specify the day of the week to run a scheduled scan | Specify the day \(or never\) to run a scan. | Never |
| Scan | Specify the time of day to run a scheduled scan | Specify the number of minutes after midnight to run a scan \(for example, enter 60 for 1 AM\). | 2 AM. |

Tip

Our recommendation for scheduled scans is to configure **quick** scan together with always-on [real-time protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) and [cloud protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure), as this combination provides strong coverage against malware that starts with the system and kernel-level malware.

Warning

Generally, there's no need to schedule a full scan, and most users won't need to manually run full scans \(see [Comparing quick scan, full scan, and custom scan](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans)\).

## Group Policy settings for general scheduling scans

The following table describes general Group Policy settings for scan scheduling:

| Location | Setting | Description | Default setting \(if not configured\) |
| :--- | :--- | :--- | :--- |
| Root | Randomize scheduled task times | In Microsoft Defender Antivirus, randomize the start time of the scan to any interval from **0 to 23 hours**. By default, scheduled tasks begin at a random time within four hours of the time specified in Task Scheduler. | Enabled |
| Root | Configure scheduled task times randomization window | - This setting lets you set the start time for scheduled task scans and security updates.  <br>- When enabled, you can choose a randomization window between **1 and 23 hours**.  <br>- When the **Randomize scheduled task times** setting is enabled, scheduled scans use the specified window.  <br>- If disabled or not configured, it randomizes times between **0 and 4 hours**. | Not configured \(Disabled\) |

Tip

Enable randomization for Virtual Machines \(VMs\), Virtual Desktop Infrastructure \(VDI\), and Azure Virtual Desktop \(AVD\) devices to ensure that scheduled scans don't run simultaneously. Randomizing scan times helps prevent CPU and disk I/O bottlenecks on the parent partition \(also known as the Host\).

## Group Policy settings for maximum CPU usage during scans

The following table describes the Group Policy setting for maximum CPU usage during scans:

| Location | Setting | Description | Default setting \(if not configured\) |
| --- | --- | --- | --- |
| Scan | Specify the maximum percentage of CPU utilization during a scan | Set the maximum CPU usage allowed during a scan. Enter a value from 5 to 100 \(percent\). A value of 0 means no CPU limit is applied. | Enabled - 50 |

Note

Setting the maximum CPU usage to between 5% and 30% makes scans take longer. Keep this in mind if you have a maintenance window.

## Group Policy settings for scheduling scans for lowering the CPU priority

This setting controls whether scans run only when the computer is idle. When enabled, it lowers CPU use for other tasks:

| Location | Setting | Description | Default setting \(if not configured\) |
| :--- | :--- | :--- | :--- |
| Scan | Start the scheduled scan only when computer is on but not in use | Scans run only when the computer is on and idle. | Enabled |

Note

When endpoints aren't in use at scan time, the scan skips CPU throttling. It uses all available resources to finish as fast as possible.

## Group Policy settings for scheduling remediation-required scans

The following table lists the Group Policy settings for scheduling remediation-required scans:

| Location | Setting | Description | Default setting \(if not configured\) |
| --- | --- | --- | --- |
| Remediation | Specify the day of the week to run a scheduled full scan to complete remediation | Choose which day to run a scan, or select never. | Never |
| Remediation | Specify the time of day to run a scheduled full scan to complete remediation | Enter the minutes after midnight for the scan time \(for example, **60** means 1 AM\). | 120 \(2 AM\) |

## Group Policy settings for scheduling scans after protection updates

The following table describes the setting for running scans after protection updates:

| Location | Setting | Description | Default setting \(if not configured\) |
| :--- | :--- | :--- | :--- |
| Signature updates | Turn on scan after Security intelligence update | Runs a scan right after a new protection update is downloaded. | Enabled |

## See also

The following articles provide more information about Microsoft Defender Antivirus configuration and troubleshooting:

- [Troubleshoot Microsoft Defender Antivirus scan issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-mdav-scan-issues)
- [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus)
- [Use PowerShell cmdlets to configure and manage Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus)
- [Set the PowerShell cmdlet to configure and manage Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference)
- [Defender Antivirus specific PowerShell functions](https://learn.microsoft.com/en-us/powershell/module/defender)
- [Troubleshoot Microsoft Defender Antivirus settings](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-settings)

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
