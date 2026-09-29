<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Use PowerShell cmdlets to configure and manage Microsoft Defender Antivirus

You can use PowerShell to perform various functions in Microsoft Defender Antivirus. Similar to the command prompt or command line, PowerShell is a task-based command-line shell and scripting language designed especially for system administration. You can read more about it in the [PowerShell documentation](https://learn.microsoft.com/en-us/powershell/scripting/overview).

For a list of the cmdlets and their functions and available parameters, see the [Microsoft Defender Antivirus cmdlets](https://learn.microsoft.com/en-us/powershell/module/defender) topic.

PowerShell cmdlets are most useful in Windows Server environments that don't rely on a graphical user interface \(GUI\) to configure software.

Note

PowerShell cmdlets should not be used as a replacement for a full network policy management infrastructure, such as [Microsoft Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr), [Group Policy Management Console](https://learn.microsoft.com/en-us/defender-endpoint/use-group-policy-microsoft-defender-antivirus), or [Microsoft Defender Antivirus Group Policy ADMX templates](https://learn.microsoft.com/en-us/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

Changes made with PowerShell will affect local settings on the endpoint where the changes are deployed or made. Because PowerShell changes only local settings on the endpoint, deployments of policy with Microsoft Defender for Endpoint security settings management, Microsoft Intune, Microsoft Configuration Manager Tenant Attach, or Group Policy can overwrite changes made with PowerShell.

You can [configure which settings can be overridden locally with local policy overrides](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus).

PowerShell is typically installed under the folder `%SystemRoot%\system32\WindowsPowerShell`.

## Prerequisites

### Supported operating systems

The following operating systems are supported:

- Windows

## Use Microsoft Defender Antivirus PowerShell cmdlets

Use the following steps to run Microsoft Defender Antivirus PowerShell cmdlets:

1. In the Windows search bar, type **powershell**.
2. Select **Windows PowerShell** from the results to open the interface.
3. Enter the PowerShell command and any parameters.

Note

You may need to open PowerShell in administrator mode. Right-click the item in the Start menu, click **Run as administrator** and click **Yes** at the permissions prompt.

To view the full online documentation for any Defender PowerShell cmdlet, including additional parameters and examples, use the following command:

```PowerShell
Get-Help <cmdlet> -Online
```

Omit the `-online` parameter to get locally cached help.

### Common Microsoft Defender Antivirus PowerShell cmdlets

Microsoft Defender Antivirus can be configured using PowerShell cmdlets. These are task-based commands for configuration and management. Common cmdlets include:

- [Get-MpComputerStatus](https://learn.microsoft.com/en-us/powershell/module/defender/get-mpcomputerstatus): Check Microsoft Defender Antivirus status and protection settings.
- [Set-MpPreference](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference): Configure preferences, such as exclusions, scan schedules, and cloud-delivered protection.
- [Update-MpSignature](https://learn.microsoft.com/en-us/powershell/module/defender/update-mpsignature): Update security intelligence.
- [Start-MpScan](https://learn.microsoft.com/en-us/powershell/module/defender/start-mpscan): Trigger quick, full, or custom scans.
- [Get-MpThreat](https://learn.microsoft.com/en-us/powershell/module/defender/get-mpthreat) or [Get-MpThreatDetection](https://learn.microsoft.com/en-us/powershell/module/defender/get-mpthreatdetection): Review detected and remediated threats.

For full syntax and parameter options, see [Microsoft Defender Antivirus cmdlets](https://learn.microsoft.com/en-us/powershell/module/defender).

Tip

- If you're looking for Antivirus related information for other platforms, see:

  - [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
  - [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
  - [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
  - [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
  - [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
  - [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
  - [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

- **Performance tip**: Due to a variety of factors, anti-virus software \(including Microsoft Defender Antivirus\) can cause performance issues on endpoint devices. In some cases, you might need to tune the performance of Microsoft Defender Antivirus to alleviate those performance issues. Microsoft's **Performance analyzer** is a PowerShell command-line tool that helps determine which files, file paths, processes, and file extensions might be causing performance issues. For example:

  - Top paths that impact scan time.
  - Top files that impact scan time.
  - Top processes that impact scan time.
  - Top file extensions that impact scan time.
  - Combinations. For example:

    - Top files per extension.
    - Top paths per extension.
    - Top processes per path.
    - Top scans per file.
    - Top scans per file per process.


  You can use this information to better assess performance issues and apply remediation actions. For more information, see [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus).

## Related articles

The following resources provide additional information about managing and configuring Microsoft Defender Antivirus:

- [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus)
- [Reference topics for management and configuration tools](https://learn.microsoft.com/en-us/defender-endpoint/configuration-management-reference-microsoft-defender-antivirus)
- [Microsoft Defender Antivirus in Windows 10](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)
- [Microsoft Defender Antivirus Cmdlets](https://learn.microsoft.com/en-us/powershell/module/defender)
