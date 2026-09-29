<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/use-wmi-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Use Windows Management Instrumentation \(WMI\) to configure and manage Microsoft Defender Antivirus

This article explains how to use Windows Management Instrumentation \(WMI\) classes and scripts to configure and manage Microsoft Defender Antivirus settings on local Windows endpoints.

WMI is a scripting interface that allows you to retrieve, modify, and update settings.

Read more about WMI at the [Microsoft Developer Network System Administration library](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page).

Microsoft Defender Antivirus has a number of specific WMI classes that can be used to perform most of the same functions as Group Policy and other management tools. Many of the classes are analogous to [Defender for Cloud PowerShell cmdlets](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus).

The [MSDN Windows Defender WMIv2 Provider reference library](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) lists the available WMI classes for Microsoft Defender Antivirus, and includes example scripts.

Changes made with WMI affect only local settings on the endpoint where the changes are deployed or made. Because WMI changes affect only local settings, deployments of policy with Group Policy, Microsoft Configuration Manager, or Microsoft Intune can overwrite changes made with WMI.

You can [configure which settings can be overridden locally with local policy overrides](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus).

## Prerequisites

### Supported operating systems

The following operating systems are supported:

- Windows

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

Tip

**Performance tip** Due to a variety of factors \(examples listed below\) Microsoft Defender Antivirus, like other antivirus software, can cause performance issues on endpoint devices. In some cases, you might need to tune the performance of Microsoft Defender Antivirus to alleviate those performance issues. Microsoft's **Performance analyzer** is a PowerShell command-line tool that helps determine which files, file paths, processes, and file extensions might be causing performance issues; some examples are:

- Top paths that impact scan time
- Top files that impact scan time
- Top processes that impact scan time
- Top file extensions that impact scan time
- Combinations – for example:

  - top files per extension
  - top paths per extension
  - top processes per path
  - top scans per file
  - top scans per file per process

You can use the information gathered using Performance analyzer to better assess performance issues and apply remediation actions. See: [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus).

## Related content

- [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus)
- [Reference topics for management and configuration tools](https://learn.microsoft.com/en-us/defender-endpoint/configuration-management-reference-microsoft-defender-antivirus)
- [Microsoft Defender Antivirus in Windows 10](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)
