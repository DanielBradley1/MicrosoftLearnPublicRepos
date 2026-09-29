<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/collect-diagnostic-data -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Collect Microsoft Defender Antivirus diagnostic data

Use `MpCmdRun.exe` to collect Microsoft Defender Antivirus diagnostic data when Microsoft support or engineering teams help you troubleshoot device issues. Save the support package on the affected device, or copy packages from multiple devices to a central location.

Note

To collect a Defender for Endpoint investigation package instead, see [Collect an investigation package from a device](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts#collect-investigation-package-from-devices).

For Microsoft Defender Antivirus performance issues, use [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus).

## Collect diagnostic data by using MpCmdRun

On each affected device, choose whether to keep the diagnostic package on the device or copy it to a central location:

1. Open an elevated Command Prompt \(a Command Prompt window you opened by selecting **Run as administrator**\), and then use one of the following options:

   - **Save the diagnostic log files on the local device**: The following commands change to the latest available Microsoft Defender Antivirus platform folder and create the support package:

     Tip

     The first command changes the directory to the latest version of <antimalware platform version> in `%ProgramData%\Microsoft\Windows Defender\Platform\<antimalware platform version>`. If that path doesn't exist, it goes to `%ProgramFiles%\Windows Defender`.

     ```dos
     (set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

     MpCmdRun.exe -GetFiles
     ```


     By default, `MpCmdRun.exe` generates, compresses, and saves the diagnostic log files to `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.


     The `.cab` filename is the same on every device.

   - **Copy the diagnostic log files to a central location**: The following syntax creates the local support package and copies it to the specified root path:

     ```dos
     (set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

     MpCmdRun.exe -GetFiles -SupportLogLocation <RootPath>
     ```


     The tool creates `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`, and then copies the `.cab` file with a new name into a subfolder of `<RootPath>` \(for example, `P:\Data` or `\\Server01\Data`\). The copied file uses the following path and filename syntax: `<RootPath>\<MMDD>\MpSupport-<Hostname>-<HHMM>.cab`.


     - `<RootPath>` is the value you specified for `-SupportLogLocation`.
     - `<MMDD>` is the month and day when you ran the MpCmdRun command \(for example, 0318 for March 18\).
     - `<Hostname>` is the name of the device where you ran the MpCmdRun command \(for example, LAPTOP01\).
     - `<HHMM>` is the hour and minute when you ran the MpCmdRun command \(for example, `2221` for 22:21\).


   Note


   If the tool can't copy the `.cab` file to the specified location, check the default local location at `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.


   The following example copies the support package from the device named LAPTOP01 on March 18 at 22:21:


   ```dos
   (set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

   MpCmdRun.exe -GetFiles -SupportLogLocation "\\SERVER01\Data"
   ```


   The resulting `.cab` file is available at `\\SERVER01\Data\0318\MpSupport-LAPTOP01-2221.cab`. The hostname and time in the filename distinguish files collected from different devices.

2. Wait a few minutes for `MpCmdRun.exe` to generate and compress the diagnostic log files. The resulting `.cab` file includes:

   - Any trace files from Microsoft Antimalware Service.
   - The Windows Update history log.
   - All Microsoft Antimalware Service events from the System event log.
   - All relevant Microsoft Antimalware Service registry locations.
   - The log file of MpCmdRun.
   - The log file of the signature update helper tool.


   Copy the `.cab` files to a secure location that Microsoft support can access, such as a password-protected OneDrive folder.

## Configure the diagnostic file copy location by using Group Policy

Configure the **Define the directory path to copy support log files** policy to copy diagnostic packages to a central location after `MpCmdRun.exe` creates them on each device. When you configure this policy, you don't need to use the `-SupportLogLocation` option with `MpCmdRun.exe -GetFiles`.

Use the procedure in [Configure Microsoft Defender Antivirus using Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/use-group-policy-microsoft-defender-antivirus#configure-microsoft-defender-antivirus-using-group-policy) to open and edit a Group Policy object \(GPO\) that applies to the target devices. For domain-based Group Policy, you can manage the templates in the [Group Policy Central Store](https://learn.microsoft.com/en-us/troubleshoot/windows-client/group-policy/create-and-manage-central-store#the-central-store).

To configure the diagnostic file copy location:

1. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus**.

   [![Screenshot of Local Group Policy Editor with Microsoft Defender Antivirus selected in the console tree.](https://learn.microsoft.com/en-us/defender-endpoint/media/gpo1-supportloglocationdefender.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/gpo1-supportloglocationdefender.png#lightbox)
2. Open **Define the directory path to copy support log files**.
3. Select **Enabled**. In **Options**, enter the directory path where you want the tool to copy support packages.

   [![Screenshot of Local Group Policy Editor with Enabled selected and a path value entered in the Options section.](https://learn.microsoft.com/en-us/defender-endpoint/media/gpo3-supportloglocationgppageenabledexample.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/gpo3-supportloglocationgppageenabledexample.png#lightbox)
4. Select **OK**.

The policy configures the `SupportLogLocation` value under `HKLM\Software\Policies\Microsoft\Windows Defender`.

## Related content

- [Troubleshoot Microsoft Defender Antivirus scan issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-mdav-scan-issues)
- [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus)
