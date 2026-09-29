<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mac-support-perf-overview -->
<!-- Sitemap-Last-Modified: 2025-09-29 -->

# Overview for how to troubleshoot performance issues for Microsoft Defender for Endpoint on macOS

This article provides general guidelines to identify performance issues related to Microsoft Defender for Endpoint on macOS. See [Troubleshoot performance issues for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-perf) for more specific guidance.

Depending on the applications that you're running and your device characteristics, you might experience suboptimal performance when running Microsoft Defender for Endpoint on macOS. In particular, applications or system processes that access many resources over a short timespan can lead to performance issues in Microsoft Defender for Endpoint on macOS.

Tip

As a general best practice, it's recommended to [update the Microsoft Defender for Endpoint agent to latest available version](https://learn.microsoft.com/en-us/defender-endpoint/mac-whatsnew) and confirming that the issue still persists before investigating further.

Caution

Running other non-Microsoft endpoint protection products alongside Microsoft Defender for Endpoint on macOS is likely to lead to performance problems and unpredictable side effects. If non-Microsoft endpoint protection is an absolute requirement in your environment, you can configure Microsoft Defender Antivirus to run in **[Passive mode](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)**. After you configure Passive mode, you can use Defender for Endpoint on macOS EDR functionality.

Warning

Before starting, make sure that other security products aren't currently running on the device. Multiple security products might conflict and affect system performance.

Tip

If you're running other non-Microsoft security products, make sure that the Microsoft Defender for Endpoint on macOS processes and paths are excluded from that non-Microsoft security product and that security product is excluded from Microsoft Defender for Endpoint on macOS. And vice-versa. When troubleshooting performance issues for Microsoft Defender for Endpoint on macOS, you should review the **Activity Monitor** or run **top** to see which of the three \(3\) processes is leading the high cpu utilization

| Daemon name | Component | Troubleshooting guide |
| --- | --- | --- |
| wdavdaemon | Core \(privileged\) | Open a [Microsoft support case](https://learn.microsoft.com/en-us/defender-endpoint/contact-support). |
| wdavdaemon\_unprivileged | Anti-malware \(AV, EPP\) | Review [Troubleshoot performance issues for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-perf). |
| wdavdaemon\_enterprise | Endpoint Detection and Response \(EDR\) | Open a [Microsoft support case](https://learn.microsoft.com/en-us/defender-endpoint/contact-support). |

Additionally, gather [Defender for Endpoint Client Analyzer](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer) files while the issue occurs. This is used by the support team to investigate the issue.
