<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-protection-features-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-06-02 -->

# Configure behavioral, heuristic, and real-time protection

Microsoft Defender Antivirus uses several methods to provide threat protection:

- Cloud protection for near-instant detection and blocking of new and emerging threats
- Always-on scanning, using file and process behavior monitoring and other heuristics \(also known as "real-time protection"\)
- Dedicated protection updates based on machine learning, human and automated big-data analysis, and in-depth threat resistance research

You can configure how Microsoft Defender Antivirus uses these methods with [Microsoft Defender for Endpoint Security Configuration Management](https://learn.microsoft.com/en-us/intune/intune-service/protect/mde-security-integration), [Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/use-intune-config-manager-microsoft-defender-antivirus), Microsoft Configuration Manager, [Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/use-group-policy-microsoft-defender-antivirus), [PowerShell cmdlets](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus), and [Windows Management Instrumentation \(WMI\)](https://learn.microsoft.com/en-us/defender-endpoint/use-wmi-microsoft-defender-antivirus).

This section covers configuration for always-on scanning, including how to detect and block apps that are deemed unsafe, but might not be detected as malware.

See [Use next-gen Microsoft Defender Antivirus technologies through cloud protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus) for how to enable and configure Microsoft Defender Antivirus cloud protection.

## Prerequisites

### Supported operating systems

- Windows

## In this section

| Article | Description |
| --- | --- |
| [Detect and block potentially unwanted applications](https://learn.microsoft.com/en-us/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) | Detect and block apps that mighty be unwanted in your network, such as adware, browser modifiers and toolbars, and rogue or fake antivirus apps |
| [Enable and configure Microsoft Defender Antivirus protection capabilities](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) | Enable and configure real-time protection, heuristics, and other always-on Microsoft Defender Antivirus monitoring features |
| [AI agent runtime protection with Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/ai-agent-runtime-protection-overview) | Detect and block attacks targeting local AI agents running on your devices |

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

## See also

- [Exclusions for Microsoft Defender for Endpoint and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview)
