<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/standard-device-connectivity-urls-gov -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Microsoft Defender for Endpoint standard connectivity URLs - US government

This article lists the standard connectivity URLs required to onboard and maintain devices in Microsoft Defender for Endpoint in US government cloud environments, including GCC, GCC High, and DoD. Network and security administrators should allow these URLs through firewalls and proxy servers to ensure that Defender for Endpoint services can communicate correctly.

## Microsoft Defender URLs

The following table lists the Microsoft Defender URLs required for US government cloud environments, including GCC, GCC High, and DoD.

| Service | Geography | Category | Port | Endpoint/URL | Endpoint/URL Description | Required / Optional | Windows 10/11 / Server 2019 -2022 / Server 2012 R2/Server 2016 \(Unified Agent\) | Windows 7 / 8.1 | Windows Server 2008 R2 / 2012 R2 / 2016 \(MMA Based\) | Mac | Linux | Comments |
| --- | --- | --- | --- | --- | --- | :---: | :---: | :---: | :---: | :---: | :---: | --- |
| Microsoft Defender for Endpoint | US Gov | CRL | 80 | `crl.microsoft.com/pki/crl/*` | Certificate Revocation Lists - required to validate certificates / Used by Windows when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US Gov | CRL | 80 | `ctldl.windowsupdate.com` | Expands on the existing automatic root update mechanism technology to let certificates that are compromised or untrusted be specifically flagged as untrusted | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | US Gov | CRL | 80 | `www.microsoft.com/pkiops/*` | Used when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US Gov | CRL | 80 | `http://www.microsoft.com/pki/certs` | Used when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US Gov | Common | 443 | `events.data.microsoft.com` | Used by the Connected User Experiences and Telemetry component and connects to the Microsoft Data Management service | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US Gov | Common | 443 | `*.wns.windows.com` | Windows Push Notification Services \(WNS\) - Live Response | Required | Yes |  |  |  |  | Required for Live Response Performance \(Direct Connection or proxy bypass required\) |
| Microsoft Defender for Endpoint | US Gov | Common | 443 | `login.microsoftonline.com` | Windows Push Notification Services \(WNS\) - Live Response | Required | Yes |  |  |  |  | Required for Live Response Performance \(Direct Connection or proxy bypass required\) |
| Microsoft Defender for Endpoint | US Gov | Common | 443 | `login.live.com` | Windows Push Notification Services \(WNS\) - Live Response | Required | Yes |  |  |  |  | Required for Live Response Performance \(Direct Connection or proxy bypass required\) |
| Microsoft Defender for Endpoint | US Gov | Common | 443 | `settings-win.data.microsoft.com` | Connected User Experiences and Telemetry Channel | Optional | Yes |  |  |  |  | Not required for Windows 10 1809 \(RS5\) and above / Windows 2019 |
| Microsoft Defender for Endpoint | US Gov | Common \(Mac\) \(Linux\) | 443 | `cdn.x.cp.wd.microsoft.com` | Microsoft Defender Antivirus Content Delivery Network \(CDN\) - Security Intelligence updates | Required |  |  | Yes | Yes |  |  |
| Microsoft Defender for Endpoint | WW | Common \(Mac/Linux\) | 443 | Root URL for public Microsoft CDN endpoints \(referred to as ChannelURL\) - for the updated URL, see [Using Custom channel and ManifestServer to control updates](https://learn.microsoft.com/en-us/microsoft-365-apps/mac/mau-configure-organization-specific-updates) |  |  |  |  |  |  |  |  |
| Microsoft Defender for Endpoint | US Gov | Common \(Mac/Linux\) | 443 | Root URL for public Microsoft CDN endpoints \(referred to as ChannelURL\) - for the updated URL, see [Using Custom channel and ManifestServer to control updates](https://learn.microsoft.com/en-us/microsoft-365-apps/mac/mau-configure-organization-specific-updates) | Microsoft Office Content Delivery Network \(CDN\) - Product Updates | Required |  |  |  | Yes | Yes | New CDN endpoint starting with macOS build 101.26012.0012 |
| Microsoft Defender for Endpoint | US Gov | Microsoft Monitoring Agent \(MMA\) | 443 | `*.ods.opinsights.azure.us` | MMA for Win 7/8.1/2008R2/2012R2/2016 | Optional |  | Yes | Yes |  |  | Refer to steps at [https://aka.ms/mde\_network\_requirements](https://aka.ms/mde_network_requirements) to eliminate wildcards \(\*\) |
| Microsoft Defender for Endpoint | US Gov | Microsoft Monitoring Agent \(MMA\) | 443 | `*.oms.opinsights.azure.us` | MMA for Win 7/8.1/2008R2/2012R2/2016 | Optional |  | Yes | Yes |  |  | Refer to steps at [https://aka.ms/mde\_network\_requirements](https://aka.ms/mde_network_requirements) to eliminate wildcards \(\*\) |
| Microsoft Defender for Endpoint | US Gov | Microsoft Monitoring Agent \(MMA\) | 443 | `*.blob.core.usgovcloudapi.net` | MMA for Win 7/8.1/2008R2/2012R2/2016 | Optional |  | Yes | Yes |  |  | Refer to steps at [https://aka.ms/mde\_network\_requirements](https://aka.ms/mde_network_requirements) to eliminate wildcards \(\*\) |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `unitedstates4.x.cp.wd.microsoft.us` | Used by Microsoft Defender Antivirus to provide cloud-delivered protection and security intelligence updates | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `us4-v20.events.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `winatp-gw-usmt.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `winatp-gw-usmv.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `automatedirstrfmusmt.blob.core.usgovcloudapi.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `automatedirstrfmusmv.blob.core.usgovcloudapi.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `ussusg1virginiaff4.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `ussusg2virginiaff4.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `wsusg1virginiaff4.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `ussusg1texasff4.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `ussusg2texasff4.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC | Microsoft Defender for Endpoint GCC | 443 | `wsusg1texasff4.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `unitedstates1.x.cp.wd.microsoft.us` | Used by Microsoft Defender Antivirus to provide cloud-delivered protection and security intelligence updates | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `us4-v20.events.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `winatp-gw-usgt.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `automatedirstrffusgv.blob.core.usgovcloudapi.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes | Yes | Yes |  |  |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `ussusg1virginiaff0.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `ussusg2virginiaff0.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `wsusg1virginiaff0.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `ussusg1texasff0.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `ussusg2texasff0.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | GCC High | Microsoft Defender for Endpoint GCC High | 443 | `wsusg1texasff0.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `unitedstates2.x.cp.wd.microsoft.us` | Used by Microsoft Defender Antivirus to provide cloud-delivered protection and security intelligence updates | Required | Yes |  |  | Yes | Yes | Yes |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `us4-v20.events.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `winatp-gw-usgt.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `winatp-gw-usgv.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `automatedirstrffusgt.blob.core.usgovcloudapi.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `automatedirstrffusgv.blob.core.usgovcloudapi.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `ussusd1centralff5.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `ussusd2centralff5.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `wsusd1centralff5.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `ussusd1eastff5.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `ussusd2eastff5.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | DoD | Microsoft Defender for Endpoint DoD | 443 | `wsusd1eastff5.blob.core.usgovcloudapi.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender Antivirus | US Gov | MU / WU | 443 | `*.update.microsoft.com` | MU / WU - Security intelligence and product updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | US Gov | MU / WU | 443 | `*.delivery.mp.microsoft.com` | MU / WU - Security intelligence and product updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | US Gov | MU / WU | 443 | `*.windowsupdate.com` | MU / WU - Security intelligence and product updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | US Gov | MU \(ADL\) | 443 | `*.download.windowsupdate.com` | ADL - Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | US Gov | MU \(ADL\) | 443 | `*.download.microsoft.com` | ADL - Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | US Gov | MU \(ADL\) | 443 | `*.definitionupdates.microsoft.com` | ADL - Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | US Gov | MU \(ADL\) | 443 | `fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx` | ADL - Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | GCC | MAPS | 443 | `unitedstates4.cp.wd.microsoft.us` | MAPS - Used by Microsoft Defender Antivirus to provide cloud-delivered protection | Required | Yes |  |  |  |  |  |
| Microsoft Defender Antivirus | GCC High | MAPS | 443 | `unitedstates1.cp.wd.microsoft.us` | MAPS - Used by Microsoft Defender Antivirus to provide cloud-delivered protection | Required | Yes |  |  |  |  |  |
| Microsoft Defender Antivirus | DoD | MAPS | 443 | `unitedstates2.cp.wd.microsoft.us` | MAPS - Used by Microsoft Defender Antivirus to provide cloud-delivered protection | Required | Yes |  |  |  |  |  |
| Microsoft Defender SmartScreen | GCC | Reporting and Notifications | 443 | `unitedstates4.ss.wd.microsoft.us` | Used for Microsoft Defender SmartScreen protection, reporting, and notifications. Microsoft Defender Antivirus Network Protection and custom URL indicators | Required | Yes |  |  | Yes | Yes | Microsoft Defender SmartScreen reporting and notifications. Network Protection and custom URL indicators |
| Microsoft Defender SmartScreen | GCC High | Reporting and Notifications | 443 | `unitedstates1.ss.wd.microsoft.us` | Used for Microsoft Defender SmartScreen protection, reporting, and notifications. Microsoft Defender Antivirus Network Protection and custom URL indicators | Required | Yes |  |  | Yes | Yes | Microsoft Defender SmartScreen reporting and notifications. Network Protection and custom URL indicators |
| Microsoft Defender SmartScreen | DoD | Reporting and Notifications | 443 | `unitedstates2.ss.wd.microsoft.us` | Used for Microsoft Defender SmartScreen protection, reporting, and notifications. Microsoft Defender Antivirus Network Protection and custom URL indicators | Required | Yes |  |  | Yes | Yes | Microsoft Defender SmartScreen reporting and notifications. Network Protection and custom URL indicators |
| Consolidated Defender for Endpoint services | WW | Streamlined connectivity new URL pattern | 443 | `*.endpoint.security.microsoft.com` | Used for streamlined connectivity URL consolidation as well as for future services | Required | Yes | No | Yes | Yes | Yes | Only required for streamlined connectivity initially. New services also follow this new pattern. |

## Defender portal URLs

Note

All URLs in this table are required to have access to the Microsoft Defender Security Center Portal URL.

| Service | Geography | URL |
| --- | --- | --- |
| Microsoft Defender for Endpoint | US Gov | `*.blob.core.usgovcloudapi.net` |
| Microsoft Defender for Endpoint | US Gov | `crl.microsoft.com` |
| Microsoft Defender for Endpoint | US Gov | `https://*.microsoftonline-p.com` |
| Microsoft Defender for Endpoint | US Gov | `https://secure.aadcdn.microsoftonline-p.com` |
| Microsoft Defender for Endpoint | US Gov | `https://static2.sharepointonline.com` |
| Microsoft Defender for Endpoint | GCC | `https://login.microsoftonline.com` |
| Microsoft Defender for Endpoint | GCC | `https://*.gcc.securitycenter.microsoft.us` |
| Microsoft Defender for Endpoint | GCC | `https://onboardingpckgsusmvprd.blob.core.usgovcloudapi.net` |
| Microsoft Defender for Endpoint | GCC High | `https://login.microsoftonline.us` |
| Microsoft Defender for Endpoint | GCC High | `https://*.securitycenter.microsoft.us` |
| Microsoft Defender for Endpoint | GCC High | `https://onboardingpckgsusgvprd.blob.core.usgovcloudapi.net` |
| Microsoft Defender for Endpoint | DoD | `https://login.microsoftonline.us` |
| Microsoft Defender for Endpoint | DoD | `https://onboardingpckgsusgvprd.blob.core.usgovcloudapi.net` |

## Required client processes

The following Defender for Endpoint-related client processes generate network communications. Make sure that communications from these processes are not blocked.

Select the tab for information about exclusions for that operating system.

The processes in this section are exclusively for Microsoft Defender for Endpoint for Windows platforms, including down-level OS. This list doesn't account for any other Windows communications requirements.

- [**Windows**](#tabpanel_1_Windows)
- [**macOS**](#tabpanel_1_macOS)
- [**Linux**](#tabpanel_1_Linux)

The specific exclusions to configure depend on which version of Windows your endpoints or devices are running, and are listed in the following table.

| OS | Exclusions |
| --- | --- |
| Windows 11  <br>Windows 10, version 1803 or later \(See Windows 10 release information\)  <br>Windows 10, version 1703 or 1709 with KB4493441 installed  <br>Windows Server 2025  <br>Azure Stack HCI OS, version 23H2 and later  <br>Windows Server 2022  <br>Windows Server 2019  <br>Windows Server, version 1803  <br>Windows Server 2016 running the modern unified solution  <br>Windows Server 2012 R2 running the modern unified solution | **EDR exclusions**:  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\MsSense.exe`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\SenseCncProxy.exe`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\SenseSampleUploader.exe`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\SenseIR.exe`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\SenseCM.exe`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\SenseNdr.exe`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\Classification\\SenseCE.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\DataCollection`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\SenseTVM.exe`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\SenseTracer.exe`  <br>`C:\\Program Files\\Windows Defender Advanced Threat Protection\\SenseDlpProcessor.exe`  <br>  <br>**Registry path**:  <br>`HKLM\\SOFTWARE\\Microsoft\\Windows Advanced Threat Protection\*`  <br>  <br>**Antivirus exclusions**:  <br>`C:\\Program Files\\Windows Defender\\MsMpEng.exe`  <br>`C:\\Program Files\\Windows Defender\\NisSrv.exe`  <br>`C:\\Program Files\\Windows Defender\\ConfigSecurityPolicy.exe`  <br>`C:\\Program Files\\Windows Defender\\MpCmdRun.exe`  <br>`C:\\Program Files\\Windows Defender\\MpDefenderCoreService.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\MsMpEng.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\NisSrv.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\ConfigSecurityPolicy.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\MpCopyAccelerator.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\MpCmdRun.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\MpDefenderCoreService.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\mpextms.exe`  <br>  <br>**Endpoint Data Loss Prevention \(Endpoint DLP\) exclusions**:  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\MpDlpService.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\MpDlpCmd.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\MipDlp.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender\\Platform\\4.18.*\\DlpUserAgent.exe` |
| Windows Server 2016 or Windows Server 2012 R2 running the [modern unified solution](https://learn.microsoft.com/en-us/editor/MicrosoftDocs/defender-docs-pr/defender-endpoint%2Fswitch-to-mde-phase-2.md/main/76b249d7-f914-4c03-3eaf-48aa43b2fa4a/onboard-server.md) | The following **additional** exclusions are required after updating the Sense EDR component using [KB5005292](https://support.microsoft.com/servicing/Management-Tools/microsoft-defender/update/microsoft-defender-for-endpoint-update-for-edr-sensor):  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Platform\*\\MsSense.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Platform\*\\SenseCnCProxy.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Platform\*\\SenseIR.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Platform\*\\SenseCE.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Platform\*\\SenseSampleUploader.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Platform\*\\SenseCM.exe`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\DataCollection`  <br>`C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Platform\*\\SenseTVM.exe` |
| [Windows 8.1](https://learn.microsoft.com/en-us/windows/release-health/status-windows-8.1-and-windows-server-2012-r2) [Windows 7](https://learn.microsoft.com/en-us/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) [Windows Server 2008 R2 SP1](https://learn.microsoft.com/en-us/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) | `C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\Health Service State\\Monitoring Host Temporary Files 6\\45\\MsSenseS.exe`  <br>\( Monitoring Host Temporary Files 6\\45 can be different numbered subfolders.\)  <br>`C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\AgentControlPanel.exe`  <br>`C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\HealthService.exe`  <br>`C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\HSLockdown.exe`  <br>`C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\MOMPerfSnapshotHelper.exe`  <br>`C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\MonitoringHost.exe`  <br>`C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\TestCloudConnection.exe` |

For macOS devices, the following table lists processes to exclude in your non-Microsoft antivirus/antimalware solution:

| Process | Location |
| --- | --- |
| `wdavdaemon_enterprise`  <br>EDR engine | `/Library/Application Support/Microsoft/Defender/` |
| `wdavdaemon_unprivileged`  <br>Antivirus engine | `/Library/Application Support/Microsoft/Defender/` |
| `telemetryd_v1`  <br>Telemetry daemon for EDR | `/Library/Application Support/Microsoft/Defender/` |
| `Netext`  <br>Network extension | `/Library/SystemExtensions/*/com.microsoft.wdav.netext.systemextension/Contents/MacOS/` |
| `Epsext`  <br>Endpoint security extension | `/Library/SystemExtensions/*/com.microsoft.wdav.epsext.systemextension/Contents/MacOS/` |
| `msupdate`  <br>Microsoft AutoUpdate update tool | `/Library/Application\\ Support/Microsoft/MAU2.0/Microsoft\\ AutoUpdate.app/Contents/MacOS` |

For Linux servers, the following table lists processes to exclude in your non-Microsoft antivirus/antimalware solution:

| Process | Location |
| --- | --- |
| `wdavdaemon`  <br>Core daemon \(service\). Uses FANotify for both antimalware and EDR purposes \(TALPA on older RHEL\). | `/opt/microsoft/mdatp/sbin/` |
| `wdavdaemon enterprise`  <br>EDR engine. Used for enrichment. | `/opt/microsoft/mdatp/sbin/` |
| `wdavdaemon unprivileged`  <br>Antivirus engine | `/opt/microsoft/mdatp/sbin/` |
| `crashpad_handler`  <br>Collects crash dumps | `/opt/microsoft/mdatp/sbin/` |
| `mdatp`  <br>Command line utility | `/opt/microsoft/mdatp/sbin/Wdavdaemonclient` |
| `mde_netfilter`  <br>Packet filter for Network protection, also used for response capabilities | `/opt/microsoft/mde_netfilter/sbin` |

## Changelog

The following table summarizes recent changes to this article.

| Date | Change log |
| --- | --- |
| 04/14/2026 | Replaced `officecdn-microsoft-com.akamaized.net` with new CDN ChannelURL reference for Mac/Linux product updates. New CDN endpoint starting with macOS build 101.26012.0012. |
| 03/23/2026 | Renamed **Microsoft Defender processes** section to **Client processes**, and aligned the content for all URL lists. |
| 15/08/2023 | Removed URL: `https://msdl.microsoft.com/download/symbols`. |
| 05/12/2022 | URL details updated:  <br>Updated line 58: Updated from required to optional.  <br>Updated line 62: Changed from optional to required. Guidance text updated. Added Mac and Linux.  <br>Updated line 63: Changed from optional to required. Guidance text updated. Added Mac and Linux.  <br>Updated line 64: Changed from optional to required. Guidance text updated. Added Mac and Linux. |
| 27/05/2022 | Removed preview status from Server 2012 R2 and Server 2016 Unified Agent references.  <br>Updated line 4: URL required for Mac and Linux platforms.  <br>Updated line 5: URL required for Mac and Linux platforms. |
| 25/01/2022 | Duplicate URLs consolidated.  <br>Optional field added.  <br>US Gov, GCC, and GCC High guidance moved to separate spreadsheet.  <br>URLs removed:  <br>`eu-cdn.x.cp.wd.microsoft.com`; `wu-cdn.x.cp.wd.microsoft.com`; `*.azure-automation.net`; `*.notify.windows.com` |
