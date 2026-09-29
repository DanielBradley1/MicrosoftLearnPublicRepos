<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-np -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Troubleshoot network protection

This article provides troubleshooting information for [network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection), in cases, such as:

- Network protection blocks a website that is safe \(false positive\)
- Network protection fails to block a suspicious or known malicious website \(false negative\)

There are four steps to troubleshoot false positives and false negatives in network protection:

1. Confirm prerequisites
2. Use audit mode to test the rule
3. Add exclusions for the specified rule \(for false positives\)
4. Submit support logs

## Confirm prerequisites

Network protection works on devices with the following conditions:

- Endpoints are running Windows 10 Pro or Enterprise edition, version 1709 or higher.
- Endpoints are using Microsoft Defender Antivirus as the sole antivirus protection app. [See what happens when you're using a non-Microsoft antivirus solution](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility).
- [Real-time protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) is enabled.
- [Behavior Monitoring](https://learn.microsoft.com/en-us/defender-endpoint/behavior-monitor) is enabled.
- [Cloud-delivered protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure) is enabled.
- [Cloud Protection network connectivity](https://learn.microsoft.com/en-us/defender-endpoint/configure-network-connections-microsoft-defender-antivirus) is functional.
- Audit mode isn't enabled. Use [Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection#group-policy) to set the rule to **Disabled** \(value: **0**\).

## Use audit mode

You can enable network protection in audit mode and then visit the [network protection demo site](https://smartscreentestratings2.net) to test the feature. All website connections are allowed by network protection but an event is logged to indicate any connection that would be blocked if network protection were enabled.

1. Set network protection to **Audit mode**. Audit mode allows all connections but logs any connection that would be blocked, so you can test whether blocking is causing the issue.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Perform the connection activity that is causing an issue \(for example, attempt to visit the site, or connect to the IP address you do or don't want to block\).
3. [Review the network protection event logs](https://learn.microsoft.com/en-us/defender-endpoint/network-protection#review-network-protection-events-in-windows-event-viewer) to see if the feature would block the connection if it were set to **Enabled**.

   If network protection isn't blocking a connection that you're expecting it should block, run the following command to re-enable Network Protection in block mode and restore enforcement:

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## Report a false positive or false negative

If you tested the feature with the demo site and audit mode, network protection might work on preset scenarios but not for a specific connection. To report this issue, use the [Windows Defender Security Intelligence web-based submission form](https://www.microsoft.com/wdsi/filesubmission) to submit a false negative or false positive. With an E5 subscription, you can also link to any related alert from the [Alerts queue](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue).

See [Address false positives/negatives in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-false-positives-negatives).

## Add exclusions

The current exclusion options are:

1. Setting up a custom allow indicator.
2. Using IP exclusions: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`.
3. Excluding an entire process. For more information, see [Microsoft Defender Antivirus exclusions](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure).

## Troubleshoot network performance issues

A network protection component might slow down connections to Domain Controllers or Exchange servers. You might also see Event ID 5783 NETLOGON errors. These errors mean the device can't connect to a Domain Controller.

To fix slow network connections or Event ID 5783 NETLOGON errors, switch Network Protection from 'block mode' to '[audit mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-np)' or 'disabled'. If that resolves the problem, disable Network Protection components one at a time to isolate which component causes the issue.

Disable the following components one at a time and test your network speed after each change:

1. [Disable Datagram Processing on Windows Server](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
2. [Disable Network Protection Perf Telemetry](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
3. [Disable FTP parsing](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
4. [Disable SSH parsing](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
5. [Disable RDP parsing](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
6. [Disable HTTP parsing](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
7. [Disable SMTP parsing](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
8. [Disable DNS over TCP parsing](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
9. [Disable DNS parsing](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
10. [Disable inbound connection filtering](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)
11. [Disable TLS parsing](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference?view=windowsserver2022-ps&preserve-view=true)

If your network performance issues persist after disabling each Network Protection component listed earlier, then the issues are probably not related to network protection. Look for other causes of your network performance issues.

## Collect diagnostic data for file submissions

When you report a problem with network protection, you're asked to collect and submit diagnostic data for Microsoft support and engineering teams to help troubleshoot issues. You collect and submit the diagnostic data by running `MpCmdrun.exe -GetFiles`, which saves the data at `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

For detailed instructions, see [Collect Microsoft Defender Antivirus diagnostic data](https://learn.microsoft.com/en-us/defender-endpoint/collect-diagnostic-data).

## Resolve connectivity issues with network protection \(for E5 customers\)

Because network protection can't see your operating system proxy settings, network protection clients might be unable to reach the cloud service in some environments. To resolve these connectivity issues, configure one of the following registry keys so that network protection becomes aware of the proxy configuration. You can configure the registry key by using PowerShell, Microsoft Configuration Manager, or Group Policy.

If your environment uses a fixed proxy endpoint, configure Microsoft Defender to route traffic through that proxy server by setting the address and port:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

If your network routes traffic dynamically through a PAC file instead of a static proxy, use the following command to configure Microsoft Defender to use that PAC URL:

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

You can configure the registry key by using PowerShell, Microsoft Configuration Manager, or Group Policy. Here are some resources to help:

- [Working with Registry Keys](https://learn.microsoft.com/en-us/powershell/scripting/samples/working-with-registry-keys)
- [Configure custom client settings for Endpoint Protection](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Use Group Policy settings to manage Endpoint Protection](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## See also

- [Network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection)
- [Network protection and the TCP three-way handshake](https://learn.microsoft.com/en-us/defender-endpoint/network-protection#network-protection-and-the-tcp-three-way-handshake)
- [Evaluate network protection](https://learn.microsoft.com/en-us/defender-endpoint/evaluate-network-protection)
- [Enable network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection)
- [Address false positives/negatives in Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-false-positives-negatives)
