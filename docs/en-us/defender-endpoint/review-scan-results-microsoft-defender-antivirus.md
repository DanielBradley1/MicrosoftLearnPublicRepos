<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/review-scan-results-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Review Microsoft Defender Antivirus scan results

After a Microsoft Defender Antivirus scan completes, whether it's an [on-demand scan](https://learn.microsoft.com/en-us/defender-endpoint/run-scan-microsoft-defender-antivirus) or [scheduled antivirus scan](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans), the results are recorded and you can view the results. This article explains how to review scan results, including detected threats and their details, using the Microsoft Defender portal, Microsoft Intune, Configuration Manager, PowerShell, or Windows Management Instrumentation \(WMI\).

## Prerequisites

### Supported operating systems

The following operating systems are supported:

- Windows

## Use Microsoft Defender to review scan results

To view the scan results using the Defender portal, follow these steps.

1. Sign in to [Microsoft Defender portal](https://security.microsoft.com)
2. Go to **Incidents & alerts** > **Alerts**.

   You can view the scanned results under **Alerts**.

## Use Microsoft Intune to review scan results

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To view the scan results using Microsoft Intune admin center, see [Antivirus agent status report](https://learn.microsoft.com/en-us/intune/device-management/reports/overview#antivirus-agent-status-report-organizational) \(opens in a new tab in the Intune documentation\).

## Use Configuration Manager to review scan results

To view scan results in Configuration Manager, see [How to monitor Endpoint Protection status](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/monitor-endpoint-protection).

## Use PowerShell cmdlets to review scan results

To review recent threat detections recorded by Microsoft Defender Antivirus, run the following cmdlet. It returns each detection on the endpoint. If there are multiple detections of the same threat, each detection is listed separately, based on the time of each detection:

```PowerShell
Get-MpThreatDetection
```

[![The PowerShell cmdlets and outputs](https://learn.microsoft.com/en-us/defender/media/wdav-get-mpthreatdetection.png)](https://learn.microsoft.com/en-us/defender/media/wdav-get-mpthreatdetection.png#lightbox)

You can specify `-ThreatID` to limit the output to only show the detections for a specific threat.

To list threats currently known to Microsoft Defender Antivirus on the device, with multiple detections of the same threat combined into a single item, use the following cmdlet:

```PowerShell
Get-MpThreat
```

[![The PowerShell code](https://learn.microsoft.com/en-us/defender/media/wdav-get-mpthreat.png)](https://learn.microsoft.com/en-us/defender/media/wdav-get-mpthreat.png#lightbox)

See [Use PowerShell cmdlets to configure and run Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus) and [Defender Antivirus cmdlets](https://learn.microsoft.com/en-us/powershell/module/defender/) for more information on how to use PowerShell with Microsoft Defender Antivirus.

## Use Windows Management Instrumentation \(WMI\) to review scan results

Use the [**Get** method of the **MSFT\_MpThreat** and **MSFT\_MpThreatDetection**](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) classes.

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

## Related articles

- [Customize, initiate, and review the results of Microsoft Defender Antivirus scans and remediation](https://learn.microsoft.com/en-us/defender-endpoint/customize-run-review-remediate-scans-microsoft-defender-antivirus)
- [Address false positives/negatives in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-false-positives-negatives)
- [Microsoft Defender Antivirus in Windows 10](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)
