<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/evaluate-network-protection -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Evaluate network protection

## Overview

[Network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection) helps prevent employees from using any application to access dangerous domains that might host phishing scams, exploits, and other malicious content on the Internet.

Use the following steps to evaluate network protection by enabling the feature and visiting a testing site. The sites referenced in this evaluation aren't malicious. They're specially created websites that pretend to be malicious. Each test site replicates the behavior that would happen if a user visited a malicious site or domain.

## Enable network protection in audit mode

Enable network protection in audit mode to see which IP addresses and domains might be blocked. You can make sure it doesn't affect line-of-business apps, or get an idea of how often blocks occur.

1. Type **powershell** in the Start menu, right-click **Windows PowerShell** and select **Run as administrator**.
2. Run the following cmdlet:

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

### Visit a \(fake\) malicious domain

To verify audit mode behavior, visit a simulated malicious site and confirm that the connection is allowed with a test message.

1. Open Internet Explorer, Google Chrome, or any other browser of your choice.
2. Go to the [SmartScreen test ratings site](https://smartscreentestratings2.net).

   The network connection is allowed and a test message displays.

   [![The connection blockage notification](https://learn.microsoft.com/en-us/defender-endpoint/media/np-notif.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/np-notif.png#lightbox)

Note

Network connections can be successful even though a site is blocked by network protection. To learn more, see [Network protection and the TCP three-way handshake](https://learn.microsoft.com/en-us/defender-endpoint/network-protection#network-protection-and-the-tcp-three-way-handshake).

## Review network protection events in Windows Event Viewer

To review blocked apps, open Event Viewer. Filter for Event ID 1125 in the Microsoft-Windows-Windows Defender/Operational log. The following table lists all network protection events.

| Event ID | Provide/Source | Description |
| --- | --- | --- |
| 5007 | Windows Defender \(Operational\) | Event when settings are changed |
| 1125 | Windows Defender \(Operational\) | Event when a network connection is audited |
| 1126 | Windows Defender \(Operational\) | Event when a network connection is blocked |

### Troubleshooting Network Protection

If network protection fails to detect malicious sites, make sure that the following prerequisites are enabled:

1. Microsoft Defender Antivirus is the primary antivirus app \(active mode\)
2. [Behavior Monitoring is enabled](https://learn.microsoft.com/en-us/defender-endpoint/behavior-monitor)
3. [Cloud Protection is enabled](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure)
4. [Cloud Protection network connectivity is functional](https://learn.microsoft.com/en-us/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## Related articles

- [Network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection)
- [Network protection and the TCP three-way handshake](https://learn.microsoft.com/en-us/defender-endpoint/network-protection#network-protection-and-the-tcp-three-way-handshake)
- [Enable network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection)
- [Troubleshoot network protection](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-np)
