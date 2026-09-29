<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-passive-mode -->
<!-- Sitemap-Last-Modified: 2025-07-30 -->

# Defender Antivirus in passive mode

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

Microsoft Defender for Endpoint is a comprehensive security solution designed to protect your devices from evolving threats. One of its key features enables Microsoft Defender Antivirus to coexist with non-Microsoft antimalware solutions while still providing valuable endpoint detection and response capabilities.

Some of the key benefits of Defender Antivirus in passive mode are:

- **EDR Block mode** - Post-breach protection by detecting and remediating threats missed by the active antimalware solution
- **Security intelligence updates** - Microsoft Defender Antivirus continues to receive updates to stay aware of the latest threats.
- **Data Loss Prevention \(DLP\)** - Endpoint DLP functionalities operate normally, ensuring sensitive data is safeguarded.

For more information, see [How Microsoft Defender Antivirus affects Defender for Endpoint functionality](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility#how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality).

Note

Passive mode disables Microsoft Defender Antivirus scheduled scans unless specific configurations are applied.

## Prerequisites

- Operating system

  - Windows 10 or newer
  - Windows Server 2012 R2 or newer

- The device must be onboarded to Microsoft Defender for Endpoint
- Microsoft Defender Antivirus has to be installed and enabled

## Configure passive mode

On Windows 10 or newer, Defender Antivirus automatically enters passive mode when a non-Microsoft antimalware solution is installed and registered.

For Windows Server operating systems, follow the instructions in this section to configure passive mode for Microsoft Defender for Endpoint.

### Set the registry key

To avoid conflicts between Microsoft Defender Antivirus and a third-party antivirus solution, if you're using Windows Server, set the following registry key before onboarding the device to Microsoft Defender for Endpoint:

- **Path** - HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows Advanced Threat Protection
- **Name** - ForceDefenderPassiveMode
- **Type** - REG\_DWORD
- **Value** - 1

### Enable EDR in block mode

When Microsoft Defender Antivirus is in passive mode, EDR in block mode can provide post-breach protection by detecting and remediating threats. Ensure this feature is enabled in Defender for Endpoint.

### Avoid service modifications

Don't disable, stop, or modify associated services such as `wscsvc`, `WinDefend`, or `MsMpEng`. Stopping these services can cause instability and make your device vulnerable to threats.

### Exclude Defender binaries in third-party antivirus

To prevent performance issues or conflicts, add Microsoft Defender Antivirus and Defender for Endpoint binaries to the exclusion list of your third-party antivirus solution.

## Verify that passive mode is enabled

This section describes how to confirm whether Microsoft Defender Antivirus is in passive mode.

### Windows PowerShell

Run the following PowerShell cmdlet:

```powershell
Get-MpComputerStatus | select AMRunningMode
```

The `AMRunningMode` value indicates the current Defender Antivirus state:

- **Normal** - Active mode
- **Passive** - Passive mode
- **EDR Block Mode** - EDR is operating in block mode

### Windows security app

Follow these steps to verify that Microsoft Defender Antivirus is in passive mode \(Windows 10 and later only\).

1. Open the Windows Security app.
2. Select **Virus & threat protection**.
3. Under **Who’s protecting me?**, select **Manage providers**.
4. On the *Security providers* page, verify the antivirus provider and state.

## Additional resources

[Microsoft Defender Antivirus compatibility with other security products](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility)
