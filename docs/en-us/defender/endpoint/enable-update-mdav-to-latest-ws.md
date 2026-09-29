<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/enable-update-mdav-to-latest-ws -->
<!-- Sitemap-Last-Modified: 2026-07-15 -->

# Enable and update Defender Antivirus to the latest version on Windows Server

This article describes how to enable and update Microsoft Defender Antivirus on Windows Server. You'd use the procedures in this article if Microsoft Defender Antivirus was previously disabled or uninstalled.

## Enable and update Microsoft Defender Antivirus on Windows Server

Perform the following steps to enable and update Microsoft Defender Antivirus on Windows Server:

1. Install the latest [servicing stack updates](https://learn.microsoft.com/en-us/windows/deployment/update/servicing-stack-updates).
2. Install the latest [cumulative update](https://learn.microsoft.com/en-us/windows/deployment/update/catalog-checkpoint-cumulative-updates).
3. Reinstall Microsoft Defender Antivirus or re-enable it. See the following sections \(in this article\):

   - [Re-enable Microsoft Defender Antivirus on Windows Server if it was disabled](#re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-disabled)
   - [Re-enable Microsoft Defender Antivirus on Windows Server if it was uninstalled](#re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-uninstalled)

4. Reboot the system.
5. Install the latest version of the platform update.

   Note

   Re-enabling Microsoft Defender Antivirus doesn't automatically install the platform update. You can download and install the latest platform version using Windows update. Alternatively, you can download the update package from the [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) or from the [Antimalware and cyber security portal](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).

   If you're preparing to install the modern, unified solution on Windows Server 2016, you can leverage the [Installer help script](https://github.com/microsoft/mdefordownlevelserver/blob/main/Install.ps1) to automate the platform update and the subsequent installation and onboarding. This script can also assist in re-enabling Microsoft Defender Antivirus.

## Re-enable Microsoft Defender Antivirus on Windows Server if it was disabled

First, ensure that Microsoft Defender Antivirus is not disabled either through Group Policy or registry. For more information, see [Troubleshoot Microsoft Defender Antivirus while migrating from a third-party solution](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-microsoft-defender-antivirus-when-migrating).

If Microsoft Defender Antivirus features and installation files were previously removed from Windows Server 2016, follow the guidance in [Configure a Windows Repair Source](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-a-windows-repair-source) to restore the feature installation files.

On Windows Server 2016, you might need to use the Microsoft Defender Antivirus command-line utility \(MpCmdRun.exe\) with the `-WdEnable` option to re-enable Microsoft Defender Antivirus.

1. In an elevated Command Prompt \(a Command Prompt window you opened by selecting **Run as administrator**\), run the following commands:

   Tip

   The first command changes the directory to the latest version of <antimalware platform version> in `%ProgramData%\Microsoft\Windows Defender\Platform\<antimalware platform version>`. If that path doesn't exist, it goes to `%ProgramFiles%\Windows Defender`.

   Use the following Command Prompt sequence to switch to the latest Microsoft Defender platform folder and re-enable Windows Defender with MpCmdRun.exe:

   ```dos
   (set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

   MpCmdRun.exe -WdEnable
   ```

2. Restart the device.

## Re-enable Microsoft Defender Antivirus on Windows Server if it was uninstalled

If the Defender feature was uninstalled or removed, you can reinstall the feature.

1. In an elevated Command Prompt, run the following DISM commands to enable the Microsoft Defender Antivirus features on Windows Server:

   ```powershell
   # Windows Server 2016
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Features

   Dism /Online /Enable-Feature /FeatureName:Windows-Defender

   Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Gui

   # Windows Server 1803 or Windows Server 2019 or later
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   ```


   Tip


   You can also use [Server Manager or PowerShell to install the Microsoft Defender Antivirus feature](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows-server-configure#install-microsoft-defender-antivirus-on-windows-server).

2. Reboot the system.

## Related articles

- [Performance analyzer for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus)
