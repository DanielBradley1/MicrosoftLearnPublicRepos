<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans-powershell -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# Schedule antivirus scans using PowerShell

This article describes how to use the [Set-MpPreference](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference) PowerShell cmdlet to configure scheduled scans on Windows devices. Security administrators can use these parameters to control scan type, timing, frequency, CPU usage, and catch-up behavior for Microsoft Defender Antivirus. To learn more about scheduling scans and about scan types, see [About scheduled quick or full Microsoft Defender Antivirus scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans).

## Prerequisites

The procedures in this article have the following requirements:

**Supported operating systems**:

- Windows
- Windows Server

## Important PowerShell parameters for scheduled scans

The following **Set-MpPreference** parameters are important for scheduled scans:

- *ScanParameters*: Specifies the scan type to use for scheduled scans. Valid values are:

  - 1 or QuickScan \(default\)
  - 2 or FullScan

- *ScanScheduleDay*: Specifies the day of the week to run scheduled scans. Valid values are:

  - 0 or Everyday \(default\)
  - 1 or Sunday
  - 2 or Monday
  - 3 or Tuesday
  - 4 or Wednesday
  - 5 or Thursday
  - 6 or Friday
  - 7 or Saturday
  - 8 or Never

- *ScanScheduleQuickScanTime*: Specifies the time on the local computer to run scheduled **quick scans**. To specify a value, enter it as a time span: `hh:mm:ss` where `hh` = hours, `mm` = minutes and `ss` = seconds. For example, `13:30:00` indicates 1:30 PM. The default value is 02:00:00 \(2:00 AM\).
- *ScanScheduleTime*: Specifies the time on the local computer to run scheduled **full scans**. To specify a value, enter it as a time span: `hh:mm:ss` where `hh` = hours, `mm` = minutes and `ss` = seconds. For example, `13:30:00` indicates 1:30 PM. The default value is 02:00:00 \(2:00 AM\).
- *ScanScheduleOffset*: Specifies the fixed number of minutes to delay scheduled scan start times on the device. The default value is 120, which means scheduled scans start 2 hours after the times specified by the *ScanScheduleTime* and *ScanScheduleQuickScanTime* parameters.
- *RandomizeScheduleTaskTimes*: Specifies whether to select a random time for the scheduled tasks \(including scheduled scans\). Valid values are:

  - $true: Scheduled tasks begin within 30 minutes before or after the scheduled time. This value is the default.
  - $false: Scheduled tasks begin on the scheduled time.


  Randomized start times can distribute the effects of scanning. For example, if several virtual machines share the same host, randomized start times prevent all virtual machines from starting the scheduled tasks at the same time.

- *SchedulerRandomizationTime*: Specifies the time window, in minutes, within which scheduled tasks in Microsoft Defender \(including scheduled scans\) can randomly start. Scheduled tasks can start within the specified number of minutes before or after the time of the scheduled task. A valid value is an integer from 0 to 4294967295.

  The randomization time window is used around specific start time values \(for example, *ScanScheduleTime* and *ScanScheduleQuickScanTime* parameters\) or around the number of minutes specified by the *ScanScheduleOffset* parameter.
- *ScanOnlyIfIdleEnabled*: Specifies whether to start scheduled scans only when the computer isn't in use. Valid values are:

  - $true: Windows Defender runs schedules scans when the computer is on, but not in use. This value is the default.
  - $false: Windows Defender runs schedules scans when the computer is in use.

Tip

We recommend the following settings for scheduled quick scans:

- Real-time protection enabled \(`-DisableRealtimeMonitoring $false`, which is the default value\).
- Cloud Protection enabled.
- Network connectivity to the Cloud Protection backend.

## Use PowerShell to schedule daily quick scans

This `Set-MpPreference` command sets the daily scheduled quick scan to ±4 minutes of 12:30 PM. The device is likely on, but activity on the device is likely minimal \(lunch\).

```powershell
Set-MpPreference -ScanScheduleQuickScanTime 12:30:00 -ScanScheduleOffset 0 -RandomizeScheduleTaskTimes $false -ScanOnlyIfIdleEnabled $false
```

The preceding **Set-MpPreference** command doesn't require the following parameters because their default values already match the desired behavior:

- *ScanParameters*: The default value is 0 \(QuickScan\).
- *ScanScheduleDay*: The default value is 0 \(Everyday\).

## Use PowerShell to schedule weekly full scans

This `Set-MpPreference` command schedules a weekly full scan every Wednesday at ±4 minutes of 12:30 PM.

```powershell
Set-MpPreference -ScanParameters FullScan -ScanScheduleDay Wednesday -ScanScheduleTime 12:30:00 -ScanScheduleOffset 0 -RandomizeScheduleTaskTimes $false
```

## General PowerShell parameters for scheduled scans

The following **Set-MpPreference** parameters are also available for scheduled scans:

- *CheckForSignaturesBeforeRunningScan*: Specifies whether to check for new virus and spyware definitions before Windows Defender runs **scheduled** scans. Valid values are:

  - $true: Windows Defender checks for new definitions before running a scheduled scan.
  - $false: The scheduled scan begins with the existing definitions. This value is the default.

- *ScanAvgCPULoadFactor*: Specifies the maximum percentage CPU usage for a scan. A valid value is an integer from 5 to 100. The default value is 50. The value 0 disables CPU throttling. This value isn't a hard limit, but rather guidance for the scanning engine to not exceed the specified value on average.

  The value of this parameter is ignored if both of the following conditions are true:

  - The value of the *ScanOnlyIfIdleEnabled* parameter is $true \(scan only when the computer isn't in use\).
  - The value of the *DisableCpuThrottleOnIdleScans* parameter is $true \(disable CPU throttling on idle scans\).

- *DisableCpuThrottleOnIdleScans*: Specifies whether to disable CPU throttling for scheduled scans while the device is idle \(less than 90% CPU utilization\). Valid values are:

  - $true: The CPU isn't throttled for scheduled scans, regardless of the value of the *ScanAvgCPULoadFactor* parameter. This value is the default.
  - $false: The CPU is throttled for scheduled scans.

- *EnableLowCpuPriority*: Specifies whether to enable using low CPU priority for scheduled scans. Valid values are:

  - $true: Windows Defender uses low CPU priority for scheduled scans. This value is the default.
  - $false: Windows Defender doesn't use low CPU priority for scheduled scans.

- *DisableCatchupFullScan*: Specifies whether to disable catch-up scans for missed scheduled full scans. Valid values are:

  - $true: Windows Defender doesn't run catch-up scans for missed scheduled full scans. This value is the default.
  - $false: After two missed scheduled full scans, Windows Defender runs a catch-up scan the next time someone signs in to the computer.

- *DisableCatchupQuickScan*: Specifies whether to disable catch-up scans for missed scheduled quick scans. Valid values are:

  - $true: Windows Defender doesn't run catch-up scans for missed scheduled quick scans. This value is the default.
  - $false: After two missed scheduled quick scans, Windows Defender runs a catch-up scan the next time the device powers on or resumes from sleep or hibernation.

- *EnableFullScanOnBatteryPower*: Specifies whether to enable full scans while on battery power. Valid values are:

  - $true: Windows Defender does full scans while on battery power.
  - $false: Windows Defender doesn't do full scans while on battery power. This value is the default

For more information, see [Use PowerShell cmdlets to configure and manage Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus) and [Defender Antivirus cmdlets](https://learn.microsoft.com/en-us/powershell/module/defender/).

## PowerShell parameters for scheduled scans to complete remediation

Scheduled full scans to complete remediation use the following parameters:

- *RemediationScheduleDay*: Specifies the day of the week to run the scan. Valid values are:

  - 0 or Everyday \(default\)
  - 1 or Sunday
  - 2 or Monday
  - 3 or Tuesday
  - 4 or Wednesday
  - 5 or Thursday
  - 6 or Friday
  - 7 or Saturday
  - 8 or Never

- *RemediationScheduleTime*: Specifies the time on the local computer to run the scan. To specify a value, enter it as a time span: `hh:mm:ss` where `hh` = hours, `mm` = minutes and `ss` = seconds. For example, `13:30:00` indicates 1:30 PM. The default value is 02:00:00 \(2:00 AM\).

## See also

- [Troubleshoot Microsoft Defender Antivirus scan issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-mdav-scan-issues) - Fix common scan problems.
- [Use PowerShell cmdlets to configure and manage Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus) - General PowerShell guidance.
- [Set-MpPreference cmdlet reference](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference) - Full parameter details.
- [Defender Antivirus cmdlets](https://learn.microsoft.com/en-us/powershell/module/defender) - All available cmdlets.

Tip

If you're looking for Antivirus related information for other platforms, see the following resources:

> - [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
> - [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
> - [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
> - [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
> - [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
> - [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
> - [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
