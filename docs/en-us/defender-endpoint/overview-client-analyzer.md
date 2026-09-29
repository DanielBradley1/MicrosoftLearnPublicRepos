<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Troubleshoot sensor health using Microsoft Defender for Endpoint Client Analyzer

The [Microsoft Defender for Endpoint Client Analyzer](https://aka.ms/MDEClientAnalyzer) \(MDECA\) can be useful when diagnosing sensor health or reliability issues on [onboarded devices](https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure) running either Windows, Linux, or macOS. For example, you might want to run the analyzer on a machine that appears to be unhealthy according to the displayed [sensor health status](https://learn.microsoft.com/en-us/defender-endpoint/fix-unhealthy-sensors) \(Inactive, No Sensor Data or Impaired Communications\) in the security portal.

Besides obvious sensor health issues, MDECA can collect other traces, logs, and diagnostic information for troubleshooting complex scenarios such as:

- Application compatibility \(AppCompat\), performance, network connectivity, or
- Unexpected behavior related to [Endpoint Data Loss Prevention](https://learn.microsoft.com/en-us/purview/endpoint-dlp-learn-about).

## Use the client analyzer on devices running Windows, Linux, or macOS

- [Run the client analyzer on Windows](https://learn.microsoft.com/en-us/defender-endpoint/run-analyzer-windows)
- [Run the client analyzer on Linux](https://learn.microsoft.com/en-us/defender-endpoint/run-analyzer-linux)
- [Run the client analyzer on macOS](https://learn.microsoft.com/en-us/defender-endpoint/run-analyzer-macos)

Tip

Watch this video to get an overview of the client analyzer: [Defender for Endpoint client analyzer overview](https://www.youtube.com/watch?v=GnqDsvYYL6w)

## Privacy notice

- The Microsoft Defender for Endpoint Client Analyzer tool is regularly used by Microsoft Customer Support Services \(CSS\) to collect information that will help troubleshoot issues you might be experiencing with Microsoft Defender for Endpoint.
- The collected data might contain Personally Identifiable Information \(PII\) and/or sensitive data, such as \(but not limited to\) IP addresses, PC names, and usernames.
- Once data collection is complete, the tool saves the data locally on the machine within a subfolder and compressed zip file.
- No data is automatically sent to Microsoft. If you're using the tool during collaboration on a support issue, you might be asked to send the compressed data to Microsoft CSS using Secure File Exchange to facilitate the investigation of the issue.

For more information about Secure File Exchange, see [How to use Secure File Exchange to exchange files with Microsoft Support](https://learn.microsoft.com/en-us/troubleshoot/azure/general/secure-file-exchange-transfer-files)

For more information about our privacy statement, see [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

## Requirements

- Before running the analyzer, we recommend ensuring your proxy or firewall configuration allows access to [Microsoft Defender for Endpoint service URLs](https://learn.microsoft.com/en-us/defender-endpoint/configure-environment#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).
- The analyzer can run on supported editions of [Windows](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements#windows-versions-supported-by-defender-for-endpoint), [Linux](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites), or [macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites#system-requirements) either before of after onboarding to Microsoft Defender for Endpoint.
- For Windows devices, if you're running the analyzer directly on specific machines and not remotely via [Live Response](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-collect-support-log), then SysInternals [PsExec.exe](https://learn.microsoft.com/en-us/sysinternals/downloads/psexec) should be allowed \(at least temporarily\) to run. The analyzer calls into PsExec.exe tool to run cloud connectivity checks as Local System and emulate the behavior of the SENSE service.

  Note

  On Windows devices, if you use the attack surface reduction \(ASR\) rule [Block process creations originating from PSExec and WMI commands](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-process-creations-originating-from-psexec-and-wmi-commands), you might want to take one of the following actions to temporarily allow the analyzer to run cloud connectivity checks without being blocked:

  - [Configure an exclusion to the ASR rule](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#file-and-folder-exclusions-for-asr-rules).
  - Set the rule to **Audit** mode.
  - Disable the rule.
