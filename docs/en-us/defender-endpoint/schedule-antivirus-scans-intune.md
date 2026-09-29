<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans-intune -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# Schedule antivirus scans using Microsoft Intune

Security administrators can use Microsoft Intune to schedule Microsoft Defender Antivirus scans on managed Windows devices. This article explains how to create an antivirus policy, schedule daily and weekly scans, and configure CPU usage and catch-up scan settings. For guidance on choosing a scan type, see [About scheduled quick or full Microsoft Defender Antivirus scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans).

## Prerequisites

Before you configure scheduled antivirus scans in Intune, verify that your devices use a supported operating system.

### Supported operating systems

Intune supports scheduled antivirus scans on the following operating systems:

- Windows
- Windows Server

## Configure antivirus scans using Intune

The procedures in this article require Microsoft Intune. Intune is a separate product that isn't part of Microsoft Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, see [Schedule Microsoft Defender Antivirus scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans) for other configuration methods. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To configure scheduled antivirus scans in Microsoft Intune, use an endpoint security **Antivirus** policy. For detailed instructions, see [Create endpoint security policies](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#create-endpoint-security-policies) or [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: Go to **Manage** > **Antivirus** on the **Endpoint security \| Overview** page at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/overview](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), and then select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Create policy**.
- **Platform**: Select **Windows**.
- **Profile**: Select **Microsoft Defender Antivirus**.

When you create or modify the policy, use the settings described in this article on the **Configuration settings** tab. For descriptions of all available settings, see [Configure Microsoft Defender Antivirus using Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/use-intune-config-manager-microsoft-defender-antivirus).

For more information, see [Antivirus policy for endpoint security in Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-antivirus-policy).

### Schedule daily quick scans using Intune

Use the following Intune setting to schedule a daily quick scan on Windows devices:

- **Setting**: **Schedule Quick Scan Time**
- **Values**:

  - ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-off.png) **Not Configured**
  - ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **Configured**

    - Enter a time of day from **0** \(12:00 AM\) through **1380** \(11:00 PM\). The default value is **120** \(2:00 AM\).

For example, a value of **720** schedules the daily quick scan for 12:00 PM.

### Schedule weekly quick or full scans using Intune

Use the following Intune settings to schedule a weekly quick or full scan on Windows devices:

- **Setting**: **Scan parameter**
- **Values**:

  - **Not configured**
  - **Quick scan \(Default\)**
  - **Full scan**

- **Setting**: **Schedule Scan Day**
- **Values**:

  - **Not configured**
  - **Every day \(Default\)**
  - **Sunday** to **Saturday**
  - **No scheduled scan**

- **Setting**: **Schedule Scan Time**
- **Values**:

  - ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-off.png) **Not Configured**
  - ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **Configured**

    - Enter a time of day from **0** \(12:00 AM\) through **1380** \(11:00 PM\). The default value is **120** \(2:00 AM\).

The following example schedules a quick scan on Windows devices every Wednesday at 5:00 PM \(**1020**\):

| Setting | Value |
| --- | --- |
| Scan parameter | Quick scan \(Default\) |
| Schedule Scan Day | Wednesday |
| Schedule Scan Time | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **Configured**  <br>**1020** |

Tip

Microsoft recommends using quick scans with always-on real-time protection and [cloud protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus). This combination provides strong coverage against malware that starts with the system and kernel-level malware. Quick scans with always-on real-time protection and cloud protection are the default configuration.

In general, you don't need to schedule a full scan, and most users never need to run full scans manually. For more information, see [Comparing quick scan, full scan, and custom scan](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans).

### Configure general settings for scheduled scans

Review the following general scheduled-scan settings when you configure the policy:

- **Setting**: **Check For Signatures Before Running Scan**
- **Values**:

  - **Not configured**
  - **Disabled \(Default\)**
  - **Enabled** \(recommended\)

- **Setting**: **Randomize Schedule Task Times**
- **Values**:

  - **Not configured**
  - **Widen or narrow the randomization period for scheduled scans \(Default\)** \(use **Scheduler Randomization Time** to set the randomization window\)
  - **Scheduled tasks will not be randomized** \(recommended\)

- **Setting**: **Scheduler Randomization Time**
- **Values**:

  - ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-off.png) **Not Configured** \(recommended\)
  - ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **Configured**

    - Enter a value between **1** and **23** hours. The default value is **4** hours.

- **Setting**: **Avg CPU Load Factor**
- **Values**:

  - ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-off.png) **Not Configured** \(recommended\)
  - ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **Configured**

    - Enter a percentage from **0** to **100**. The default value is **50**.

- **Setting**: **Enable Low CPU Priority**
- **Values**:

  - **Not configured**
  - **Disabled \(Default\)** \(recommended\)
  - **Enabled**

- **Setting**: **Disable Catchup Full Scan**
- **Values**:

  - **Not configured**
  - **Disabled** \(enables catch-up full scans\)
  - **Enabled \(Default\)** \(disables catch-up full scans and matches the Microsoft Defender Antivirus client default\)

- **Setting**: **Disable Catchup Quick Scan**
- **Values**:

  - **Not configured**
  - **Disabled** \(enables catch-up quick scans\)
  - **Enabled \(Default\)** \(disables catch-up quick scans and matches the Microsoft Defender Antivirus client default\)

## Related content

- [Troubleshoot Microsoft Defender Antivirus scan issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-mdav-scan-issues)
- [Troubleshoot Microsoft Defender Antivirus settings](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-settings)
- [Troubleshoot performance issues related to real-time protection](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-performance-issues)
- [Run the client analyzer on Windows](https://learn.microsoft.com/en-us/defender-endpoint/run-analyzer-windows)
- [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus)
- [Microsoft Defender Antivirus full scan considerations and best practices](https://learn.microsoft.com/en-us/defender-endpoint/mdav-scan-best-practices)
