<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-microsoft-defender-antivirus-features -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Configure Microsoft Defender Antivirus features

## Prerequisites

### Supported operating systems

- Windows

You can configure Microsoft Defender Antivirus with a number of tools, such as:

- [Microsoft Defender for Endpoint Security Policy Management](https://learn.microsoft.com/en-us/intune/intune-service/protect/mde-security-integration)
- [Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/use-intune-config-manager-microsoft-defender-antivirus)
- [Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/preferences-setup)
- Microsoft Configuration Manager [Tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/)
- [Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/use-group-policy-microsoft-defender-antivirus)
- [PowerShell cmdlets](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus)
- [Windows Management Instrumentation \(WMI\)](https://learn.microsoft.com/en-us/defender-endpoint/use-wmi-microsoft-defender-antivirus)

The following broad categories of features can be configured:

- Cloud-delivered protection. See [Cloud-delivered protection and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus)
- Always-on real-time protection, including behavioral, heuristic, and machine learning-based protection. See [Configure behavioral, heuristic, and real-time protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-protection-features-microsoft-defender-antivirus).
- How end users interact with the client on individual endpoints. See the following resources:

  - [Prevent users from seeing or interacting with the Microsoft Defender Antivirus user interface](https://learn.microsoft.com/en-us/defender-endpoint/prevent-end-user-interaction-microsoft-defender-antivirus)
  - [Prevent or allow users to locally modify Microsoft Defender Antivirus policy settings](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus)

Tip

Review [Reference topics for management and configuration tools](https://learn.microsoft.com/en-us/defender-endpoint/configuration-management-reference-microsoft-defender-antivirus). If you're looking for Antivirus related information for other platforms, see:

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
