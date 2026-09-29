<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/streamlined-device-connectivity-urls-gov -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Microsoft Defender for Endpoint streamlined connectivity URLs - US government environments \(Preview\)

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

This article includes a list of the streamlined connectivity URLs required to onboard and maintain devices in Microsoft Defender for Endpoint in US Government cloud environments \(GCC, GCC High, DoD\). Before you configure these URLs, make sure your environment meets the [prerequisites](#prerequisites).

## Prerequisites

Before using the streamlined connectivity URLs listed in this article, ensure your devices meet the required OS versions, have up-to-date antimalware platform and EDR sensor components, and are onboarded using a supported method. For full details, see the prerequisites for [streamlined connectivity](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity#prerequisites).

### Notes

The following notes describe device versions that still require legacy or expanded URL lists.

- Devices running Defender for Endpoint delivered via the Microsoft Monitoring Agent \(MMA, also known as the Log Analytics Agent - specifically, Windows 7 SP1, Windows 8.1, Windows Server 2008 R2 and those Windows Server 2012 R2, 2016 devices not upgraded to the modern unified solution\) will continue using the associated legacy method. For the list of additional URLs, refer to the Windows 7, 8.1, 2008R2 \(MMA\) tab in [Onboard devices using streamlined connectivity for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity).
- Devices running Windows version 1607, 1703, 1709, 1803 can onboard using the new onboarding package but still require a longer list of URLs. The Windows 1607 to 1803 tab in [Onboard devices using streamlined connectivity for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity) lists the additional URLs required.

## US Gov URLs

The following tables list the required streamlined connectivity endpoints for US Government cloud environments, organized by function.

### General URLs

Note

Make sure your devices meet all component \(app/antimalware platform, engine, EDR sensor\) update versions and OS requirements else onboarding might be unsuccessful. You can re-onboard devices to switch them to streamlined connectivity if they meet these requirements.

| Service | Geography | Category | Port | Endpoint/URL | Description | Required | Win 11/10/Server \(Unified\) | Win 7/8.1 | Server \(MMA\) | Mac | Linux |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Consolidated Defender for Endpoint services | USGov | Streamlined connectivity URL | 443 | \*.endpoint.security.microsoft.us | Streamlined connectivity URL consolidation and future services | Required | Yes | No | Yes | Yes | Yes |
| Microsoft Defender SmartScreen | GCC | Reporting and Notifications | 443 | unitedstates4.ss.wd.microsoft.us | SmartScreen protection, reporting, notifications, Network Protection, custom URL indicators | Required | Yes |  |  | Yes | Yes |
| Microsoft Defender SmartScreen | GCC High | Reporting and Notifications | 443 | unitedstates1.ss.wd.microsoft.us | SmartScreen protection, reporting, notifications, Network Protection, custom URL indicators | Required | Yes |  |  | Yes | Yes |
| Microsoft Defender SmartScreen | DoD | Reporting and Notifications | 443 | unitedstates2.ss.wd.microsoft.us | SmartScreen protection, reporting, notifications, Network Protection, custom URL indicators | Required | Yes |  |  | Yes | Yes |
| Defender for Endpoint | DoD | Internal configuration management | 443 | https://config.ecs.dod.teams.microsoft.us/config/v1 | This URL must be allowed to enable Defender on Linux endpoints to receive internal configurations from the cloud. | Required |  |  |  |  | Yes |
| Defender for Endpoint | GCC High | Internal configuration management | 443 | https://config.ecs.gov.teams.microsoft.us/config/v1 | This URL must be allowed to enable Defender on Linux endpoints to receive internal configurations from the cloud. | Required |  |  |  |  | Yes |
| Defender for Endpoint | GCC Mod | Internal configuration management | 443 | https://gccmod.ecs.office.com/config/v1 | This URL must be allowed to enable Defender on Linux endpoints to receive internal configurations from the cloud. | Required |  |  |  |  | Yes |

### URLs used for updates

Note

Depending on your environment, you may apply updates from a file share or update server and don't need to allow \(all\) direct connections from devices, or these connections are already required and allowed in your environment for other purposes such as Windows updates.

This table lists URL endpoints used by Microsoft Defender Antivirus. These endpoints are optional when updates are managed internally using WSUS, Configuration Manager, or a file share.

| Service | Geography | Category | Port | Endpoint/URL | Description | Required/Optional | Win 11/10/Server \(Unified\) | Win 7/8.1 | Server \(MMA\) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Microsoft Defender Antivirus | US Gov | MU/WU | 443 | \*.update.microsoft.com | Security intelligence and product updates | Optional | Yes | Yes | Yes |
| Microsoft Defender Antivirus | US Gov | MU/WU | 443 | \*.delivery.mp.microsoft.com | Security intelligence and product updates | Optional | Yes | Yes | Yes |
| Microsoft Defender Antivirus | US Gov | MU/WU | 443 | \*.windowsupdate.com | Security intelligence and product updates | Optional | Yes | Yes | Yes |
| Microsoft Defender Antivirus | US Gov | MU \(ADL\) | 443 | \*.download.windowsupdate.com | Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |
| Microsoft Defender Antivirus | US Gov | MU \(ADL\) | 443 | \*.download.microsoft.com | Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |
| Microsoft Defender Antivirus | US Gov | MU \(ADL\) | 443 | fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx | Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |

## URLs used for certificate validation checks

Note

Certificate validation is performed through the Windows operating system, helping to prevent abuse of compromised certificates. This means the operating system must be able to connect to these destinations, or, should be updated with the latest certificate trust lists if they can't retrieve them from Microsoft directly. For more information, see [Configure trusted roots and disallowed certificates in Windows](https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/configure-trusted-roots-disallowed-certificates).

| Service | Geography | Category | Port | Endpoint/URL | Description | Required/Optional | Win 11/10/Server \(Unified\) | Win 7/8.1 | Server \(MMA\) | Mac | Linux |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Microsoft Defender for Endpoint | US Gov | CRL | 80 | crl.microsoft.com/pki/crl/\* | Certificate Revocation Lists - required to validate certificates / Used by Windows when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |
| Microsoft Defender for Endpoint | US Gov | CRL | 80 | ctldl.windowsupdate.com | Expands on the existing automatic root update mechanism technology to let certificates that are compromised or untrusted be specifically flagged as untrusted | Required | Yes |  |  |  |  |
| Microsoft Defender for Endpoint | US Gov | CRL | 80 | www.microsoft.com/pkiops/\* | Used when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |
| Microsoft Defender for Endpoint | US Gov | CRL | 80 | http://www.microsoft.com/pki/certs | Used when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |

### Live Response and notification URLs

Note

The following Live Response performance URLs are required \(Direct Connection/Proxy bypass required\)

| Service | Geography | Category | Port | Endpoint/URL | Description | Required/Optional | Win 11/10/Server \(Unified\) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Microsoft Defender for Endpoint | US Gov | Common | 443 | \*.wns.windows.com | Windows Push Notification Services \(WNS\) - Live Response | Required | Yes |
| Microsoft Defender for Endpoint | US Gov | Common | 443 | login.microsoftonline.us | Windows Push Notification Services \(WNS\) - Live Response | Required | Yes |
| Microsoft Defender for Endpoint | US Gov | Common | 443 | login.live.com | Windows Push Notification Services \(WNS\) - Live Response | Required | Yes |

## Defender portal URLs

Note

The following table lists the required URL endpoints for accessing the Microsoft Defender portal.

| Service | Geography | URL |
| --- | --- | --- |
| Microsoft Defender for Endpoint | US Gov | \*.blob.core.usgovcloudapi.net |
| Microsoft Defender for Endpoint | US Gov | crl.microsoft.com |
| Microsoft Defender for Endpoint | US Gov | https://\*.microsoftonline-p.com |
| Microsoft Defender for Endpoint | US Gov | https://secure.aadcdn.microsoftonline-p.com |
| Microsoft Defender for Endpoint | US Gov | https://static2.sharepointonline.com |
| Microsoft Defender for Endpoint | GCC | https://login.microsoftonline.com |
| Microsoft Defender for Endpoint | GCC | https://\*.gcc.securitycenter.microsoft.us |
| Microsoft Defender for Endpoint | GCC | https://onboardingpckgsusmvprd.blob.core.usgovcloudapi.net |
| Microsoft Defender for Endpoint | GCC High | https://login.microsoftonline.us |
| Microsoft Defender for Endpoint | GCC High | https://\*.securitycenter.microsoft.us |
| Microsoft Defender for Endpoint | GCC High | https://onboardingpckgsusgvprd.blob.core.usgovcloudapi.net |
| Microsoft Defender for Endpoint | DoD | https://login.microsoftonline.us |
| Microsoft Defender for Endpoint | DoD | https://\*.securitycenter.microsoft.us |
| Microsoft Defender for Endpoint | DoD | https://onboardingpckgsusgvprd.blob.core.usgovcloudapi.net |

## Client processes that require network connectivity

The following Microsoft Defender for Endpoint client processes generate network communications. Make sure that communications from each of these processes are not blocked. The included list identifies specific executable processes \(such as `MsSense.exe` and `MsMpEng.exe`\) that must be permitted through firewalls and proxies for Defender for Endpoint to function correctly.

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

| Date | Change log |
| --- | --- |
| 03/23/2026 | Renamed **Microsoft Defender process exclusions** section to **Client processes**, and aligned the content for all URL lists. |
| 03/03/2026 | Added Linux URLs to [General URLs](#general-urls) for internal configuration management: `config.ecs.dod.teams.microsoft.us` \(DoD\), `config.ecs.gov.teams.microsoft.us` \(GCC High\), `gccmod.ecs.office.com` \(GCC Mod\). |
| 10/23/2025 | Initial page published \(Preview\). |
