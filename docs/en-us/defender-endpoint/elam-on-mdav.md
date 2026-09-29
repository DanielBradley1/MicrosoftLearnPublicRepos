<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/elam-on-mdav -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Early Launch Antimalware \(ELAM\) and Microsoft Defender Antivirus

Detecting malware that starts early in the boot cycle was a challenge before Windows 8. Starting with Windows 8 and Windows Server 2012, Windows introduced the [Early Launch Antimalware \(ELAM\)](https://learn.microsoft.com/en-us/windows/compatibility/early-launch-antimalware) driver. Microsoft Defender Antivirus uses the ELAM driver \(Wdboot.sys\) to combat early boot threats \(for example, rootkits or malicious drivers that can hide from detection\). The Wdboot.sys driver starts before other boot-start drivers. ELAM evaluates other drivers and helps the Windows kernel decide whether to initialize them.

## Supported operating systems

- Windows 8 or later
- Windows Server 2012 or later

## ELAM detection logging

ELAM detections are logged in the same location as other Microsoft Defender Antivirus detections, for example, [Event ID 1006](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-microsoft-defender-antivirus).

## Keep the ELAM driver up to date

The ELAM driver is included in the monthly [platform update](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates).

## Modify the ELAM policy

To modify the ELAM policy, use Group Policy:

**Computer Configuration** > **Administrative Templates** > **System** > **Early Launch Antimalware** > **Boot-Start Driver Initialization Policy**

## Verify the ELAM driver is loaded

Open **Registry Editor** and go to **HKEY\_LOCAL\_MACHINE** > **SYSTEM** > **CurrentControlSet** > **Control** > **EarlyLaunch**.

The string key named **BackupPath** should have the value `C:\Windows\ELAMBKUP`.

For more information, see [ELAM Driver Requirements](https://learn.microsoft.com/en-us/windows-hardware/drivers/install/elam-driver-requirements).

## Revert the ELAM driver to a previous version

In an elevated Command Prompt \(a Command Prompt window you opened by selecting **Run as administrator**\), run the following commands:

Tip

The first command changes the directory to the latest version of <antimalware platform version> in `%ProgramData%\Microsoft\Windows Defender\Platform\<antimalware platform version>`. If that path doesn't exist, it goes to `%ProgramFiles%\Microsoft Defender`.

```dos
(set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

MpCmdRun.exe -RevertPlatform
```

For more information, see [Manage the sources for Microsoft Defender Antivirus protection updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-protection-updates-microsoft-defender-antivirus).
