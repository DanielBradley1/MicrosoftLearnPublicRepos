<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/command-line-arguments-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-06-09 -->

# Configure and manage Microsoft Defender Antivirus with the MpCmdRun command-line tool

Use the MpCmdRun.exe command-line tool to run scans, manage security intelligence updates, and configure Microsoft Defender Antivirus. MpCmdRun is useful for automation in scripts and scheduled tasks.

- You need to run MpCmdRun in an elevated Command Prompt \(a Command Prompt window you opened by selecting **Run as administrator**\). For example:

  1. Open the **Start** menu, and then type **cmd**.
  2. Right-click on the **Command Prompt** result, and then select **Run as administrator**.

- By default, the folder that contains MpCmdRun isn't in the PATH environment variable, so you need to navigate to the folder before you run it. MpCmdRun.exe is in the following locations on Windows x64 devices:

  - `C:\Program Files\Windows Defender`
  - `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`


  The latest version of MpCmdRun is always in the `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>` folder if it's available. To go to the best available location without knowing versions or availability, use the following enhanced change directory \(cd\) command:


  ```dos
  (set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1
  ```


  For more information about the antimalware platform, see [Microsoft Defender Antivirus updates and baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates).

MpCmdRun uses the following syntax:

```dos
MpCmdRun.exe -Command [-CommandOptions]
```

In the following example, MpCmdRun starts a full antivirus scan on the device.

```dos
MpCmdRun.exe -Scan -ScanType 2
```

The [Commands and options](#commands) and [Common MpCmdRun errors](#common-errors-in-running-commands-via-mpcmdrunexe) sections describe the available switches and troubleshooting information.

## Prerequisites

- Windows

## Commands and options in MpCmdRun

The commands and their available options are described in the following table.

| Command | Option | Description |
| --- | --- | --- |
| `-?` or `-h` |  | Displays all available commands and their options. |
| `-AddDynamicSignature -Path <path>` |  | Loads dynamic security intelligence from the specified location. |
| `-CaptureNetworkTrace -Path <path>` |  | Captures network input from the Network Protection service, and saves it to the specified location. To stop tracing, use `-Path` without a value.  <br>  <br>**Note**: NT AUTHORITY\\LocalService must have write access to the specified path \(for example, `C:\\Windows\\Temp\\MpCmdRun`\). |
| `-CheckExclusion -Path <PathAndFilename or Path>` |  | Verifies whether the specified file or path is excluded from scanning. For more information, see [Verify whether a file or folder is excluded by using MpCmdRun](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure#verify-whether-a-file-or-folder-is-excluded-by-using-mpcmdrun). |
| `-DeviceControl -TestPolicyXml <PathAndFilename> -Groups or -Rules` |  | Validates the specified Device Control rules XML policy file. |
|  | `-Groups` | Identifies the specified file as a groups policy file. |
|  | `-Rules` | Identifies the specified file as a rules policy file. |
| `-DisplayECSConnection` |  | Displays the URLs used by the Defender Core service to connect to the Experimentation and Configuration Service \(ECS\). |
| `-GetFiles` \[Options\] |  | Generates, compresses, and saves Microsoft Defender Antivirus-related log files into the default file `C:\\ProgramData\\Microsoft\\Windows Defender\\Support\\MpSupportFiles.cab`. For more information, see [Collect Microsoft Defender Antivirus diagnostic data](https://learn.microsoft.com/en-us/defender-endpoint/collect-diagnostic-data). |
|  | `-DlpTrace` | Includes the data loss prevention \(DLP\) trace files in the .cab file. |
|  | `-SupportLogLocation <RootPath>` | Specifies the root folder of a central location where the local MpSupportFiles.cab file is copied. The file is copied with a unique filename into a date-based subfolder path: `<RootPath>\\<MMDD>\\MpSupport-<Hostname>-<HHMM>.cab`. For more information, see [Collect Microsoft Defender Antivirus diagnostic data](https://learn.microsoft.com/en-us/defender-endpoint/collect-diagnostic-data). |
| `-GetFilesDiagTrack` |  | Generates, compresses, and saves Microsoft Defender Antivirus-related log files into the file `%TEMP%\\DiagOutputDir\\MpSupportFiles.cab`. |
| `-HeapSnapshotConfig -Enable or -Disable -Pid <ProcessID> or -Name <ProcessName.exe>` |  | Enables or disables heap snapshot \(tracing\) configuration for the specified process ID or process name. |
|  | `-Pid <ProcessID>` | The process ID value of the process. Valid values are:<br><br>- **0 \(Default\)**: MsMpEng.exe<br>- **1**: MpDefenderCoreService.exe<br>- **2**: NisSrv.exe<br>- **3**: MpDlpService.exe<br>- **A custom value**: The specified process ID. |
|  | `-Name <ProcessName.exe>` | The name of the process. |
| `-ListAllDynamicSignatures` |  | Lists the SignatureSet IDs of all loaded dynamic security intelligence updates. |
| `-ListCustomASR` |  | Lists any custom attack surface reduction \(ASR\) rules configured on the device. |
| `-OSCA` |  | Verifies whether the OS Copy Acceleration feature is enabled. |
| `-RegisterWmiSchema` |  | Re-registers the MpProtection MOF schema if it doesn't match the latest installed schema. |
| `-RemoveDefinitions [Options]` |  | Restores the previous set of signature definitions. |
|  | `-All` | Restores the installed security intelligence to a previous backup copy or to the original default set. |
|  | `-DynamicSignatures` | Removes only dynamically downloaded security intelligence updates. |
|  | `-Engine` | Restores the previously installed engine. |
| `-RemoveDynamicSignature -SignatureSetID <SignatureSetID>` |  | Removes the specified dynamic security intelligence update. |
| `-ResetPlatform` |  | Resets platform binaries back to `%ProgramFiles%\\Windows Defender`. |
| `-Restore [Options]` |  | Restores or lists quarantined items. |
|  | `-ListAll` | Lists all quarantined items. |
|  | `-Name <name> [-All]` | Restores the most recently quarantined item based on the specified threat name. If you use `-All`, all quarantined items are restored based on the specified threat name. A threat can map to multiple files. |
|  | `-FilePath <QuarantinedFilePath>` | Restores a quarantined item based on the file path of the quarantined item. |
|  | `-Path <path>` | Specifies where to restore the quarantined items.<br><br>- If you don't use `-Path`, the item is restored to its original location and is removed from quarantine.<br>- If you use `-Path`, the item is restored to the specified path, but the item isn't removed from quarantine. |
|  | `-Output <filename>` | Writes all quarantined item names to the specified file with UTF-8 encoding. |
| `-RevertEdr -ToVersion <value>` |  | Reverts the endpoint detection and response \(EDR\) binaries to the specified version. Available in platform version 4.18.26030.3011 or later. Valid values are:<br><br>- **Inbox**: Reverts EDR to the inbox version stored in `%ProgramFiles%\\Windows Defender Advanced Threat Protection`.<br>- **Previous**: Reverts EDR to the previously installed \(N-1\) version, if a backup is available in `%ProgramData%\\Microsoft\\Windows Defender Advanced Threat Protection\\Platform`. |
| `-RevertPlatform` |  | Reverts platform binaries back to the previously installed version of the Defender platform. |
| `-Scan [Options]` |  | Scans for malicious software. Typically, `-Scan` with no options runs a quick scan, unless a different default scan type is configured on the device.  <br>  <br>Quick scans and full scans have default timeouts. The scan automatically stops after the time passes:<br><br>- **Quick scans**: One day<br>- **Full scans**: Seven days |
|  | `-ScanType <value>` | Specifies the type of antimalware scan to run. Valid values are:<br><br>- **0**: Default, according to the device configuration.<br>- **1**: Quick scan.<br>- **2**: Full scan<br>- **3**: Custom scan<br><br>  <br>The return code is one of the following values:<br><br>- **0**: One of the following results:<br><br>  - No malware found.<br>  - Malware found and successfully remediated.<br><br>- **2**: One of the following results:<br><br>  - Malware found and not remediated.<br>  - Malware found and user action required to complete remediation.<br>  - Scanning errors. |
|  | `-BootSectorScan` | Valid only for custom scans. Enables boot sector scanning. |
|  | `-Cancel` | Tries to cancel active quick scans or full scans. |
|  | `-CpuThrottling` | Specifies the maximum CPU usage percentage. The default value is 50. |
|  | `-DisableRemediation` | Valid only for custom scans.<br><br>- File exclusions are ignored.<br>- Archive files are scanned.<br>- Actions aren't applied after detection.<br>- Event log entries aren't written after detection.<br>- Detections from the custom scan aren't displayed in the user interface.<br>- Detections from the custom scan are displayed in the command output. |
|  | `-File <PathAndFilename or Path>` | Valid only for custom scans. Specifies the file or folder to scan. |
|  | `-ReturnHR` | Instead of returning 0 or 2, return the actual HRESULT of the scan command. |
|  | `-Timeout <days>` | Default value is 7 for full scans and 1 for all other scan types. The maximum value is 30. |
| `-SignatureUpdate [Options]` |  | Checks for new security intelligence updates. |
|  | `-UNC <path>` | Downloads updates directly from the specified UNC file share. If you don't specify a path value, the update is done directly from the preconfigured UNC location. |
|  | `-MMPC` | Downloads updates directly from the Microsoft Malware Protection Center. |
| `-Trace [Options]` |  | Starts a trace of actions by the Microsoft Antimalware Service. By default all Error, Warning, and Informational events for all components are logged. The results are stored in `C:\\ProgramData\\Microsoft\\Windows Defender\\Support\\MPTrace-<YYYMMDD>-<UTC HHMMSS>-<GUID>.bin`. |
|  | `-Grouping <value>` | Specifies the component to include in the trace. Valid values are:<br><br>- **0x1**: Service<br>- **0x2**: Malware Protection Engine<br>- **0x4**: User Interface<br>- **0x8**: Real-Time Protection<br>- **0x10**: Scheduled actions<br>- **0x20**: WMI<br>- **0x40**: NIS/GAPA<br>- **0x80**: Windows Security Center<br>- **0x100**: DLP external<br>- **0x200**: Browser Protection |
|  | `-Level <value>` | Specifies the event severity levels to include in the trace. Valid values are:<br><br>- **0x1**: Errors<br>- **0x2**: Warnings<br>- **0x4**: Informational messages<br>- **0x8**: Function calls<br>- **0x10**: Verbose<br>- **0x20**: Performance |
| `-TrustCheck -File <PathAndFilename>` |  | Checks the trust status of the specified file. Benign files might not be trusted. Only known, good files are trusted. |
| `-ValidateMapsConnection` |  | Verifies the device can communicate with the Microsoft Defender Antivirus cloud service. Available in Windows 10 version 1703 \(April 2017\) or later. |
| `-WdEnable` |  | Re-enables Microsoft Defender Antivirus on the device. |

## Common MpCmdRun errors

The following table lists common errors that you might encounter using MpCmdRun.

| Error message | Possible reason |
| --- | --- |
| **ValidateMapsConnection failed \(800106BA\)** or **0x800106BA** | The Microsoft Defender Antivirus service is disabled. Enable the service and try again. If you need help re-enabling Microsoft Defender Antivirus, see [Reinstall/enable Microsoft Defender Antivirus on your endpoints](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-1-reinstallenable-microsoft-defender-antivirus-on-your-endpoints).  <br>  <br>In Windows 10 version 1909 \(November 2019\) or earlier and Windows Server 2019 or earlier, the service was formerly named *Windows Defender Antivirus*. |
| **0x80070667** | You ran the `MpCmdRun.exe -ValidateMapsConnection` command on an unsupported version of Windows. Run the command on supported versions of Windows:<br><br>- Windows 10 version 1703 \(April 2017\) or later.<br>- Windows Server 2019 or later. |
| **MpCmdRun is not recognized as an internal or external command, operable program, or batch file.** | By default, the folder that contains MpCmdRun isn't in the PATH environment variable. You need to run MpCmdRun.exe from `%ProgramFiles%\\Windows Defender` or `%ProgramData%\\Microsoft\\Windows Defender\\Platform\\<antimalware platform version>` \(recommended\).  <br>  <br>To go to the best available directory in a Command Prompt window, use the following enhanced change directory \(cd\) command: `(set "_done=" & if exist "%ProgramData%\\Microsoft\\Windows Defender\\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\\Microsoft\\Windows Defender\\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\\Microsoft\\Windows Defender\\Platform\\%d" & set _done=1)) else (cd /d "%ProgramFiles%\\Windows Defender")) >nul 2>&1`. |
| **ValidateMapsConnection failed to establish a connection to MAPS \(hr=80070005 httpcode=450\)** | You need to run MpCmdRun in an elevated Command Prompt. For example:<br><br>1. Open the **Start** menu, and then type **cmd**.<br>2. Right-click on the **Command Prompt** result, and then select **Run as administrator**. |
| **ValidateMapsConnection failed to establish a connection to MAPS \(hr=80070006 httpcode=451\)** | A firewall is blocking the connection or doing TLS inspection. |
| **ValidateMapsConnection failed to establish a connection to MAPS \(hr=80004005 httpcode=450\)** | Possible network-related issues. For example, name resolution problems. |
| **ValidateMapsConnection failed to establish a connection to MAPS \(hr=0x80508015**\) | A firewall is blocking the connection or doing TLS inspection. |
| **ValidateMapsConnection failed to establish a connection to MAPS \(hr=800722F0D**\) | A firewall is blocking the connection or doing TLS inspection. |
| **ValidateMapsConnection failed to establish a connection to MAPS \(hr=80072EE7 httpcode=451\)** | A firewall is blocking the connection or doing TLS inspection. |

## See also

- [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus)
- [Configure Microsoft Defender Antivirus features](https://learn.microsoft.com/en-us/defender-endpoint/configure-microsoft-defender-antivirus-features)
- [Configure and validate Microsoft Defender Antivirus network connections](https://learn.microsoft.com/en-us/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)
- [Reference articles for management and configuration tools](https://learn.microsoft.com/en-us/defender-endpoint/configuration-management-reference-microsoft-defender-antivirus)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
