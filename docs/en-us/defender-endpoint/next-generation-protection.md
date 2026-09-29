<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/next-generation-protection -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Next-generation protection overview

Microsoft Defender for Endpoint includes next-generation protection to catch and block all types of emerging threats. The majority of modern malware is polymorphic, meaning it constantly mutates to evade detection. As soon as one variant is identified, another takes its place. This rapid evolution underscores the need for agile and innovative security solutions.

Next-generation protections, such as [Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows) blocks malware using local and cloud-based machine learning models, behavior analysis, and heuristics. Microsoft Defender Antivirus uses predictive technologies, machine learning, applied science, and artificial intelligence to detect and block malware at the first sign of abnormal behavior.

In addition to Microsoft Defender Antivirus, your next-generation protection services include the following capabilities:

- [Behavior-based, heuristic, and real-time antivirus protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-protection-features-microsoft-defender-antivirus), which includes always-on scanning using file and process behavior monitoring and other heuristics \(also known as *real-time protection*\). It also includes detecting and blocking apps that are deemed unsafe, but might not be detected as malware.
- [Cloud-delivered protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus), which includes near-instant detection and blocking of new and emerging threats.
- [AI agent runtime protection](https://learn.microsoft.com/en-us/defender-endpoint/ai-agent-runtime-protection-overview), which monitors activity in the agentic loop and blocks attacks targeting local AI agents running on your devices.
- [Dedicated protection and product updates](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates), which includes updates related to keeping Microsoft Defender Antivirus up to date.

Next-generation protection is included in both [Defender for Endpoint Plan 1 and Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint). Next-generation protection is also included in [Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview) and [Microsoft 365 Business Premium](https://learn.microsoft.com/en-us/microsoft-365/business-premium/m365bp-overview).

To configure next-generation protection services, see [Configure Microsoft Defender Antivirus features](https://learn.microsoft.com/en-us/defender-endpoint/configure-microsoft-defender-antivirus-features).

If you're looking for Microsoft Defender Antivirus-related information for other platforms, see one of the following articles:

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

You can use the information gathered using Performance analyzer to better assess performance issues and apply remediation actions. See [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus).
