<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/run-scan-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Configure and run on-demand Microsoft Defender Antivirus scans

You can run an on-demand scan on individual endpoints. These scans will start immediately, and you can define parameters for the scan, such as the location or type. When you run a scan, you can choose from among three types: Quick scan, full scan, and custom scan. In most cases, use a quick scan. A quick scan looks at all the locations where there could be malware registered to start with the system, such as registry keys and known Windows startup folders.

Combined with always-on, real-time protection, which reviews files when they are opened and closed, and whenever a user navigates to a folder, a quick scan helps provide strong protection against malware that starts with the system and kernel-level malware. In most cases, a quick scan is sufficient and is the recommended option for scheduled or on-demand scans. [Compare quick, full, and custom scan types](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans#comparing-the-quick-scan-full-scan-and-custom-scan).

Important

Microsoft Defender Antivirus runs in the context of the [LocalSystem account](https://learn.microsoft.com/en-us/windows/win32/services/localsystem-account) when performing a local scan. For network scans, it uses the context of the device account. If the domain device account doesn't have appropriate permissions to access the share, the scan won't work. Ensure that the device has permissions to access the network share.

## Use Microsoft Defender portal to run a scan

To run a scan from the Microsoft Defender portal, perform the following steps:

1. Go to the [Microsoft Defender portal](https://security.microsoft.com/) and sign-in.
2. Go to the **device page** that you would like to run a remote scan.
3. Click on the ellipses **\(...\)**.
4. Click on **Run Antivirus Scan**.
5. Under **Select scan type**, select the radio button for **Quick Scan** or **Full Scan**.
6. Add a comment.
7. Click on **Confirm**.

To check on the status:

1. Under **Actions & submissions**, select **Action Center** and then select **History** tab.
2. Click on **Filters**.
3. Under the **Action Type**, check the box for **Start antivirus scan**.
4. Click on **Apply**.
5. Select one of the **radio button**.
6. Under **Action Status**, you'll see the status such as **Completed**.

To check on the detections, see [Review the results of Microsoft Defender Antivirus scans](https://learn.microsoft.com/en-us/defender-endpoint/review-scan-results-microsoft-defender-antivirus)

## Use Microsoft Intune to run a scan

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

### Use endpoint security to run a scan on Windows devices

Too run a scan from Endpoint security in Intune, see [Antimalware and firewall tasks: How to perform an on-demand scan](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers) \(opens in a new tab in the Intune documentation\).

### Use devices to run a scan on a single device

To run a scan on a single device, complete the following steps:

1. Go to the [Microsoft Intune admin center](https://intune.microsoft.com) and sign-in.
2. From the sidebar, select **Devices** > **All Devices** and choose the device you want to scan.
3. Select **...More** and select **Quick Scan** \(recommended\) or **Full Scan** from the options.

## Use the Windows Security app to run a scan

For instructions on running a scan on individual Windows devices, see [Run a scan in the Windows Security app](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-security-center-antivirus).

## Use PowerShell to run a scan

Run the following command:

```powershell
Start-MpScan
```

For detailed syntax and parameter information, see [Start-MpScan](https://learn.microsoft.com/en-us/powershell/module/defender/start-mpscan).

## Use PowerShell to run a quick scan without exclusions

Important

Including very large directories in quick scans might significantly increase the time it takes for the quick scan to complete.

Run the following command:

```PowerShell
Set-MpPreference -QuickScanIncludeExclusions ScanRtpExclusions
```

The value ScanRtpExclusions or 1 includes paths that are excluded from antivirus using contextual exclusions with the following restrictions: `ScanTrigger:OnAccess`, `ScanTrigger:BM`, and `Process:`. For more information on how to set these exclusions, see [Contextual file and folder exclusions](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-overview#contextual-exclusions).

The default value Disabled or 0 disables the inclusion of the contextually excluded paths.

For more information on how to use PowerShell with Microsoft Defender Antivirus, see [Use PowerShell cmdlets to configure and run Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/use-powershell-cmdlets-microsoft-defender-antivirus) and [Defender Antivirus cmdlets](https://learn.microsoft.com/en-us/powershell/module/defender/).

## Use the MpCmdRun command-line tool to run a quick scan

To run a quick scan from the command-line utility, first switch to the current Defender platform folder and then invoke `MpCmdRun.exe`. In an elevated Command Prompt \(a Command Prompt window you opened by selecting **Run as administrator**\), run the following commands:

Tip

The first command changes the directory to the latest version of <antimalware platform version> in `%ProgramData%\Microsoft\Windows Defender\Platform\<antimalware platform version>`. If that path doesn't exist, the command changes to `%ProgramFiles%\Windows Defender`.

```dos
(set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

MpCmdRun.exe -Scan -ScanType 1
```

For more information about MpCmdRun and the different `-ScanType` values, see [Configure and manage Microsoft Defender Antivirus with the MpCmdRun command-line tool](https://learn.microsoft.com/en-us/defender-endpoint/command-line-arguments-microsoft-defender-antivirus).

## Use Windows Management Instrumentation \(WMI\) to run a scan

Use the [**Start** method](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/start-msft-mpscan) of the **MSFT\_MpScan** class.

For more information about which parameters are allowed, see [Windows Defender WMIv2 APIs](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
