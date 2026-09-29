<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-microsoft-defender-antivirus-when-migrating -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Troubleshoot Microsoft Defender Antivirus while migrating from a non-Microsoft solution

**Applies to:**

- [Microsoft Defender for Endpoint Plan 1](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [Microsoft Defender for Endpoint Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [Microsoft Defender Antivirus](https://www.microsoft.com/windows/comprehensive-security)

**Platforms**

- Windows

Use this article to resolve issues while migrating from a non-Microsoft security solution to Microsoft Defender Antivirus.

## Review event logs

1. Open the Event viewer app by selecting the Search icon in the taskbar, and searching for *event viewer*.

   Information about Microsoft Defender Antivirus can be found under **Applications and Services Logs** > **Microsoft** > **Windows** > **Windows Defender**.
2. From there, select **Open** underneath **Operational**.

   Selecting an event from the details pane shows you more information about an event in the lower pane, under the **General** and **Details** tabs.

## Microsoft Defender Antivirus doesn't start.

This issue can manifest in the form of several different event IDs, all of which have the same underlying cause.

### Associated event IDs

#### Event ID 15

- **Log name**: Application
- **Description**: Updated Windows Defender status successfully to SECURITY\_PRODUCT\_STATE\_OFF.
- **Source**: Security Center

#### Event ID 5007

- **Log name**: Microsoft-Windows-Windows Defender/Operational
- **Description**: Microsoft Defender Antivirus Configuration has changed. If this is an unexpected event, you should review the settings as this issue could be due to malware.  
  **Old value:** Default\\IsServiceRunning = 0x0  
  **New value:** HKLM\\SOFTWARE\\Microsoft\\Windows Defender\\IsServiceRunning = 0x1
- **Source**: Windows Defender

#### Event ID 5010

- **Log name**: Microsoft-Windows-Windows Defender/Operational
- **Description**: Microsoft Defender Antivirus scanning for spyware and other potentially unwanted software is disabled.
- **Source**: Windows Defender

### How to tell if Microsoft Defender Antivirus doesn't start because a non-Microsoft antivirus is installed.

On a Windows 10 or Windows 11 device, if you aren't using Microsoft Defender for Endpoint, and you have a non-Microsoft antivirus installed, then Microsoft Defender Antivirus is automatically turned off. If you're using Microsoft Defender for Endpoint with a non-Microsoft antivirus installed, Microsoft Defender Antivirus starts in passive mode, with reduced functionality.

Tip

The scenario described earlier applies only to Windows 10 and Windows 11. Other versions of Windows have [different responses](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility) to Microsoft Defender Antivirus being run alongside non-Microsoft security software.

#### Use Services app to check if Microsoft Defender Antivirus is turned off.

To open the Services app, select the Search icon from the taskbar and search for *services*. You can also open the app from the command-line by typing *services.msc*.

Information about Microsoft Defender Antivirus is listed within the Services app under **Windows Defender** > **Operational**. The antivirus service name is *Microsoft Defender Antivirus Service*.

While checking the app, you might see that *Microsoft Defender Antivirus Service* is set to manual, but when you try to start this service manually, you get a warning. The warning might say, *The Microsoft Defender Antivirus Service service on Local Computer started and then stopped. Some services stop automatically if they aren't in use by other services or programs.*

This issue indicates that Microsoft Defender Antivirus was automatically turned off to preserve compatibility with a non-Microsoft antivirus.

#### Generate a detailed report

You can generate a detailed report about currently active group policies by opening a command prompt in **Run as admin** mode, then entering the following command:

```console
GPresult.exe /h gpresult.html
```

This command generates a report located at *./gpresult.html*. Open this file and you might see the following results, depending on how Microsoft Defender Antivirus was turned off.

##### Group policy results

##### If security settings are implemented via group policy \(GPO\) at the domain or local level, or through System center configuration manager \(SCCM\)

Within the GPResults report, under the heading, *Windows Components/Microsoft Defender Antivirus*, you might see something like the following entry, indicating that Microsoft Defender Antivirus is turned off.

- **Policy**: Turn off Microsoft Defender Antivirus
- **Setting**: Enabled
- **Winning GPO**: Win10-Workstations

###### If security settings are implemented via Group policy preference \(GPP\)

Under the heading, *Registry item \(Key path: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows Defender, Value name: DisableAntiSpyware\)*, you might see something like the following entry, indicating that Microsoft Defender Antivirus is turned off.

- **DisableAntiSpyware**
- Winning GPO: Win10-Workstations
- Result: Success
- **General**
- Action: Update
- **Properties**
- Hive: HKEY\_LOCAL\_MACHINE
- Key path: SOFTWARE\\Policies\\Microsoft\\Windows Defender
- Value name: DisableAntiSpyware
- Value type: REG\_DWORD
- Value data: 0x1 \(1\)

###### If security settings are implemented via registry key

The report might contain the following text, indicating that Microsoft Defender Antivirus is turned off:

> Registry \(regedit.exe\)
> 
> HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows Defender DisableAntiSpyware \(dword\) 1 \(hex\)

###### If security settings are set in Windows or your Windows Server image

Your imagining admin might have set the security policy, [DisableAntiSpyware](https://learn.microsoft.com/en-us/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware), locally via *GPEdit.exe*, *LGPO.exe*, or by modifying the registry in their task sequence. You can [configure a Trusted Image Identifier](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) for Microsoft Defender Antivirus.

### Turn Microsoft Defender Antivirus back on

Microsoft Defender Antivirus automatically turns on if no other antivirus is currently active. You need to turn the non-Microsoft antivirus off to ensure Microsoft Defender Antivirus can run with full functionality.

Warning

Solutions suggesting that you edit the Windows Defender start values for `wdboot`, `wdfilter`, `wdnisdrv`, `wdnissvc`, and `windefend` in `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services` are unsupported, and might force you to reimage your system.

Passive mode is available if you start using Microsoft Defender for Endpoint and a non-Microsoft antivirus together with Microsoft Defender Antivirus. Passive mode allows Microsoft Defender Antivirus to scan files and update itself, but it doesn't remediate threats in passive mode. In addition, behavior monitoring via [Real Time Protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) isn't available in passive mode, unless [Endpoint data loss prevention \(DLP\)](https://learn.microsoft.com/en-us/purview/endpoint-dlp-getting-started) is deployed.

Another feature, known as [limited periodic scanning](https://learn.microsoft.com/en-us/defender-endpoint/limited-periodic-scanning-microsoft-defender-antivirus), is available to end-users when Microsoft Defender Antivirus is set to turn off automatically. This feature allows Microsoft Defender Antivirus to scan files periodically alongside a non-Microsoft antivirus, using a limited number of detections.

Important

Limited periodic scanning isn't recommended in enterprise environments. The detection, management, and reporting capabilities available when running Microsoft Defender Antivirus in this mode are reduced as compared to active mode.

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

## See also

- [Microsoft Defender Antivirus compatibility](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility)
- [Microsoft Defender Antivirus in the Windows Security app](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-security-center-antivirus)
