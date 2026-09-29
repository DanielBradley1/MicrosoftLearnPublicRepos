<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans-wmi -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Schedule antivirus scans using Windows Management Instrumentation \(WMI\)

This article describes how to configure scheduled Microsoft Defender Antivirus scans using Windows Management Instrumentation \(WMI\). WMI is useful for administrators who manage scan schedules programmatically or in environments where Group Policy isn't available. You'll learn how to set scan timing, configure idle-only scans, schedule remediation, and define daily quick scan times. To learn more about scheduling scans and about scan types, see [Configure scheduled quick or full Microsoft Defender Antivirus scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans).

## Prerequisites

### Supported operating systems

WMI-based scan scheduling is supported on the following operating systems:

- Windows
- Windows Server

## Use Windows Management Instrumentation \(WMI\) to schedule scans

**MSFT\_MpPreference** is the WMI class used to configure Microsoft Defender Antivirus preferences. Use the [**Set** method of the **MSFT\_MpPreference**](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/legacy/dn455323\(v=vs.85\)) class for the following properties:

The following WMI properties control scan scheduling and behavior in the Defender configuration class:

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

For more information and allowed parameters, see [Windows Defender WMIv2 APIs](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## WMI for scheduling scans when an endpoint isn't in use

Caution

When you schedule scans for times when endpoints aren't in use, scans don't honor the CPU throttling configuration and will take full advantage of the resources available to complete the scan as fast as possible.

Use the [Set method of the MSFT\_MpPreference class](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/legacy/dn455323\(v=vs.85\)) for the following properties:

The following WMI property controls whether scans run only when the device is idle:

```WMI
ScanOnlyIfIdleEnabled
```

For more information about APIs and allowed parameters, see [Windows Defender WMIv2 APIs](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## WMI for scheduling scans to complete remediation

Remediation is the follow-up action that Microsoft Defender Antivirus takes to address detected threats after a scan, such as quarantining or removing malicious files. You can schedule when remediation occurs by using the [**Set** method of the **MSFT\_MpPreference**](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/legacy/dn455323\(v=vs.85\)) class for the following properties:

The following WMI properties define the remediation schedule day and time:

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

For more information and allowed parameters, see [Windows Defender WMIv2 APIs](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## WMI for scheduling daily scans

Use the [**Set** method of the **MSFT\_MpPreference**](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/legacy/dn455323\(v=vs.85\)) class for the following properties:

Use this WMI property to specify the scheduled daily quick scan time:

```WMI
ScanScheduleQuickScanTime
```

For more information and allowed parameters, see [Windows Defender WMIv2 APIs](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
