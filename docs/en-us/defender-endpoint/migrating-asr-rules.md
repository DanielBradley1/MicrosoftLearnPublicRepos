<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/migrating-asr-rules -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Migrating from a non-Microsoft HIPS to attack surface reduction rules

This article helps you map common rules to Microsoft Defender for Endpoint. For more information about ASR rules, see [Attack surface reduction \(ASR\) rules overview](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview).

## Scenarios when migrating from a non-Microsoft HIPS product to attack surface reduction rules

### Block creation of specific files

- **Applies to**: All processes
- **Processes**: N/A
- **Operation**: File Creation
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `.jaff`
  - `.krab`
  - `.locky`
  - `.lukitus`
  - `.odin`
  - `.wnry`
  - `.zepto`

- **Attack surface reduction rules**:

  - ASR rules block attack techniques, not indicators of compromise \(IOC\).
  - Blocking a specific file extension isn't always useful, because it doesn't prevent a device from compromise. It only partially thwarts an attack until attackers create a new type of extension for the payload.

- **Other recommended features**:

  - Microsoft highly recommends enabling Microsoft Defender Antivirus, [cloud protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus) and [behavioral blocking](https://learn.microsoft.com/en-us/defender-endpoint/client-behavioral-blocking).
  - Microsoft recommends other prevention measures, such as the ASR rule [Use advanced protection against ransomware](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#use-advanced-protection-against-ransomware) \(`c1db55ab-c21a-4637-bb3f-a12568109d35`\), which provides a greater level of protection against ransomware attacks.
  - Microsoft Defender for Endpoint monitors many of these registry keys, such as Autostart Extension Points \(ASEP\) techniques, which trigger specific alerts. The registry keys used require a minimum of Local Admin or Trusted Installer privileges. Microsoft recommends using a locked-down environment with minimum administrative accounts or rights. You can enable other system configurations, including disabling the `SeDebugPrivilege` as part of wider security recommendations.

### Block creation of specific registry keys

- **Applies to**: All Processes
- **Processes**: N/A
- **Operation**: Registry Modifications
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `HKCU\Environment\UserInitMprLogonScript`
  - `HKCU\Software\Microsoft\HtmlHelp Author\location`
  - `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Accessibility\ATs*\StartExe`
  - `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options*\Debugger`
  - `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SilentProcessExit*\MonitorProcess`

- **Attack surface reduction rules**:

  - ASR rules block attack techniques, not indicators of compromise \(IOC\).
  - Blocking a specific file extension isn't always useful, because it doesn't prevent a device from compromise. It only partially thwarts an attack until attackers create a new type of extension for the payload.

- **Other recommended features**:

  - Microsoft highly recommends enabling Microsoft Defender Antivirus, [cloud protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus) and [behavioral blocking](https://learn.microsoft.com/en-us/defender-endpoint/client-behavioral-blocking).
  - Microsoft recommends other prevention measures, including the ASR rule [Use advanced protection against ransomware](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#use-advanced-protection-against-ransomware) \(`c1db55ab-c21a-4637-bb3f-a12568109d35`\), which provides a greater level of protection against ransomware attacks.
  - Microsoft Defender for Endpoint monitors many of these registry keys, such as Autostart Extension Points \(ASEP\) techniques, which trigger specific alerts. The registry keys used require a minimum of Local Admin or Trusted Installer privileges. Microsoft recommends using a locked-down environment with minimum administrative accounts or rights. You can enable other system configurations, including disabling the `SeDebugPrivilege` as part of wider security recommendations.

### Block untrusted programs from running from removable drives

- **Applies to**: Untrusted Programs from USB
- **Processes**:

  - `*`

- **Operation**: Process Execution
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:
- **Attack surface reduction rules**:

  - Use the ASR rule named [Block untrusted and unsigned processes that run from USB](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-untrusted-and-unsigned-processes-that-run-from-usb) \(`b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`\)

- **Other recommended features**:

  - For more information about controls for USB devices and other removable media using Defender for Endpoint, see [Device control in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/device-control-overview).

### Block Mshta from launching certain child processes

- **Applies to**: Mshta
- **Processes**:

  - `mshta.exe`

- **Operation**: Process Execution
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `cmd.exe`
  - `powershell.exe`
  - `regsvr32.exe`

- **Attack surface reduction rules**: There are no specific ASR rules to prevent child processes from mshta.exe. This type of control is available in [exploit protection](https://learn.microsoft.com/en-us/defender-endpoint/exploit-protection) or [Application Control for Windows](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/appcontrol).
- **Other recommended features**:

  - Enable application control to prevent mshta.exe from running at all. If your organization requires *mshta.exe* for line of business apps, configure a specific exploit protection rule to prevent mshta.exe from launching child processes.

### Block Outlook from launching child processes

- **Applies to**: Outlook
- **Processes**:

  - `outlook.exe`

- **Operation**: Process Execution
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `powershell.exe`

- **Attack surface reduction rules**:

  - The ASR rule [Block Office communication application from creating child processes](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-office-communication-application-from-creating-child-processes) \(`26190899-1602-49e8-8b27-eb1d0a1ce869`\) prevents Office communication apps \(Outlook, Skype, and Teams\) from launching child processes.

- **Other recommended features**:

  - Microsoft recommends enabling [PowerShell constrained language mode](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/) to minimize the attack surface from PowerShell.

### Block Office apps from launching child processes

- **Applies to**: Office
- **Processes**:

  - `excel.exe`
  - `powerpnt.exe`
  - `winword.exe`

- **Operation**: Process Execution
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `EQNEDT32.EXE`
  - `cmd.exe`
  - `mshta.exe`
  - `powershell.exe`
  - `regsrv32.exe`
  - `wscript.exe`

- **Attack surface reduction rules**:

  - The ASR rule [Block all Office applications from creating child processes](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-all-office-applications-from-creating-child-processes) \(`d4f940ab-401b-4efc-aadc-ad5f3c50688a`\) prevents Office apps from launching child processes.

- **Other recommended features**: N/A

### Block Office apps from creating executable content

- **Applies to**: Office
- **Processes**:

  - `winword.exe`
  - `powerpnt.exe`
  - `excel.exe`

- **Operation**: File Creation
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `C:\ProgramData**.com`
  - `C:\ProgramData**.exe`
  - `C:\ProgramData**.scf`
  - `C:\Users*AppData\Local\Temp**.com`
  - `C:\Users*\AppData**.exe`
  - `C:\Users*\AppData**.scf`
  - `C:\Users*\Desktop**.exe`
  - `C:\Users*\Downloads**.exe`
  - `C:\Users\Public**.exe`

- **Attack surface reduction rules**:

  - The ASR rule [Block Office applications from creating executable content](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-office-applications-from-creating-executable-content) \(`3b576869-a4ec-4529-8536-b80a7769e899`\) prevents Office apps from saving malicious executable content to disk.

### Block Wscript from reading certain types of files

- **Applies to**: Wscript
- **Processes**:

  - `wscript.exe`

- **Operation**: File Read
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:
- `C:\Users*\AppData**.js`
- `C:\Users*\Downloads**.js`
- **Attack surface reduction rules**:

  - Due to reliability and performance issues, ASR rules can't prevent a process from reading specific types of script files. But the following ASR rules can help prevent attack vectors that might originate from these scenarios:

    - [Block JavaScript or VBScript from launching downloaded executable content](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-javascript-or-vbscript-from-launching-downloaded-executable-content) \(`d3e037e1-3eb8-44c8-a917-57927947596d`\)
    - [Block execution of potentially obfuscated scripts](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-execution-of-potentially-obfuscated-scripts) \(`5beb7efe-fd9a-4556-801d-275e5ffc04cc`\)

- **Other recommended features**:

  - By default, the Antimalware Scan Interface \(AMSI\) can inspect various scripts in real time \(for example, PowerShell, Windows Script Host, JavaScript, VBScript, and more\). For more information, see [Antimalware Scan Interface \(AMSI\)](https://learn.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal).

### Block launch of child processes

- **Applies to**: Adobe Acrobat
- **Processes**:

  - `AcroRd32.exe`
  - `Acrobat.exe`

- **Operation**: Process Execution
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `cmd.exe`
  - `powershell.exe`
  - `wscript.exe`

- **Attack surface reduction rules**:

  - The ASR rule [Block Adobe Reader from creating child processes](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-adobe-reader-from-creating-child-processes) \(`7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`\) prevents Adobe Reader from launching child processes.

- **Other recommended features**: N/A

### Block download or creation of executable content

- **Applies to**: CertUtil
- **Processes**:

  - `certutil.exe`

- **Operation**: File Creation
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `*.exe`

- **Attack surface reduction rules**:

  - ASR rules don't support these scenarios because they're included in Microsoft Defender Antivirus protection.

- **Other recommended features**:

  - Microsoft Defender Antivirus prevents CertUtil from creating or downloading executable content.

### Block processes from stopping critical System components

- **Applies to**: All Processes
- **Processes**:

  - `*`

- **Operation**: Process Termination
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `MsMpEng.exe`
  - `MsSense.exe`
  - `NisSrv.exe`
  - `csrss.exe`
  - `services.exe`
  - `smss.exe`
  - `svchost.exe`
  - `wininit.exe`
  - and more

- **Attack surface reduction rules**: ASR rules don't support these scenarios because they're included in Windows built-in security protections.
- **Other recommended features**:

  - [Early Launch AntiMalware \(ELAM\)](https://learn.microsoft.com/en-us/defender-endpoint/elam-on-mdav)
  - [Protection Process Light \(PPL\) and PPL AntiMalware Light](https://learn.microsoft.com/en-us/windows/win32/services/protecting-anti-malware-services-)
  - [System Guard](https://learn.microsoft.com/en-us/windows/security/hardware-security/how-hardware-based-root-of-trust-helps-protect-windows)

### Block specific launch Process Attempt

- **Applies to**: Specific processes
- **Processes**: Specific processes
- **Operation**: Process Execution
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `tor.exe`
  - `bittorrent.exe`
  - `cmd.exe`
  - `powershell.exe`
  - and more

- **Attack surface reduction rules**:

  - Overall, ASR rules aren't designed to act as an application manager.

- **Other recommended features**:

  - To prevent users from launching specific processes or programs, use [Application Control for Windows](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/appcontrol).
  - Although it isn't an application control mechanism, you can use Microsoft Defender for Endpoint indicators of compromise \(IOCs\) for [files](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file) and [certificates](https://learn.microsoft.com/en-us/defender-endpoint/indicator-certificates) in incident response scenarios.

### Block unauthorized changes to Microsoft Defender Antivirus configurations

- **Applies to**: All Processes
- **Processes**:

  - `*`

- **Operation**: Registry Modifications
- **Examples of Files/Folders, Registry Keys/Values, Processes, or Services**:

  - `HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware`
  - `HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Policy Manager\AllowRealTimeMonitoring`
  - and more

- **Attack surface reduction rules**: ASR rules don't support these scenarios because they're included in Microsoft Defender for Endpoint built-in protection.
- **Other recommended features**:

  - [Tamper protection in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview) prevents unauthorized changes to the registry keys associated with Microsoft Defender Antivirus. For example:
  - DisableAntiVirus
  - DisableAntiSpyware
  - DisableRealtimeMonitoring
  - DisableOnAccessProtection
  - DisableBehaviorMonitoring
  - DisableIOAVProtection
  - and more

## Related content

- [Attack surface reduction FAQ](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-faq)
- [Configure attack surface reduction \(ASR\) rules and exclusions](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure)
