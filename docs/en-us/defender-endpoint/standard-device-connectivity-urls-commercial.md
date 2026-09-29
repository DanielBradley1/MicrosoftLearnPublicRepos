<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/standard-device-connectivity-urls-commercial -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Microsoft Defender for Endpoint standard connectivity URLs - commercial

This article lists the URLs needed to onboard and maintain devices in Microsoft Defender for Endpoint in commercial cloud environments. Use this list to set up firewall or proxy allow rules so devices can reach the required services.

## Microsoft Defender URLs

This section lists the Microsoft Defender service URLs organized by geography and category. Allow these endpoints in your firewall or proxy to ensure proper device connectivity.

| Service | Geography | Category | Port | Endpoint/URL | Endpoint/URL Description | Required or Optional | Windows 10, 11; Server 2022, 2019, 2016 \(Unified Agent\); Server 2012 R2 \(Unified Agent\) | Windows 7, 8.1 | Windows Server 2008 R2, 2012 R2, 2016 \(MMA Based\) | Mac | Linux | Comments |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Microsoft Defender for Endpoint | WW | CRL | 80 | `crl.microsoft.com` | Certificate Revocation Lists - required to validate certificates / Used by Windows when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | WW | CRL | 80 | `ctldl.windowsupdate.com` | Expands on the existing automatic root update mechanism technology to let certificates that are compromised or untrusted be specifically flagged as untrusted | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | WW | CRL | 80 | `www.microsoft.com/pkiops/*` | Used when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | WW | CRL | 80 | `www.microsoft.com/pki/*` | Used when creating the SSL connection to MAPS for updating the CRL | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | WW | Common | 443 | `events.data.microsoft.com` | Used by the Connected User Experiences and Telemetry component and connects to the Microsoft Data Management service | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | WW | Common | 443 | `*.wns.windows.com` | Windows Push Notification Services \(WNS\) - Live Response | Optional | Yes |  |  |  |  | Required for Live Response Performance \(Direct Connection or proxy bypass required\) |
| Microsoft Defender for Endpoint | WW | Common | 443 | `login.microsoftonline.com` | Windows Push Notification Services \(WNS\) - Live Response / Vulnerability assessment for network devices / Security Management for Microsoft Defender for Endpoint - Azure Registration | Optional | Yes | Yes | Yes |  |  | Required for Live Response Performance \(Direct Connection or proxy bypass required\). Required when using Security Management for Microsoft Defender for Endpoint |
| Microsoft Defender for Endpoint | WW | Common | 443 | `login.live.com` | Windows Push Notification Services \(WNS\) - Live Response | Optional | Yes |  |  |  |  | Required for Live Response Performance \(Direct Connection or proxy bypass required\) |
| Microsoft Defender for Endpoint | WW | Common | 443 | `settings-win.data.microsoft.com` | Connected User Experiences and Telemetry Channel | Optional | Yes |  |  |  |  | Only required for Windows 10 1703 and below. Not required on Windows Server. |
| Microsoft Defender for Endpoint | WW | Common \(Mac/Linux\) | 443 | `x.cp.wd.microsoft.com` | Used by Microsoft Defender Antivirus to provide cloud-delivered protection and security intelligence updates | Required |  |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | WW | Common \(Mac/Linux\) | 443 | `cdn.x.cp.wd.microsoft.com` | Microsoft Defender Antivirus Content Delivery Network \(CDN\) - Security Intelligence updates | Required |  |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | WW | Mac | 443 | Root URL for public Microsoft CDN endpoints \(referred to as ChannelURL\) - for the updated URL, see [Using Custom channel and ManifestServer to control updates](https://learn.microsoft.com/en-us/microsoft-365-apps/mac/mau-configure-organization-specific-updates) | Microsoft Office Content Delivery Network \(CDN\) - Product Updates | Required |  |  |  | Yes |  | New CDN endpoint starting with macOS build 101.26012.0012 |
| Microsoft Defender for Endpoint | WW | Common \(Linux\) | 443 | `packages.microsoft.com` | Required to download and update the MDE Linux agent | Required |  |  |  |  | Yes |  |
| Microsoft Defender for Endpoint | WW | Microsoft Defender for Endpoint | 443 | `login.windows.net` | Microsoft Defender for Endpoint Vulnerability assessment for network devices \(network scanner\) | Optional | Yes | Yes | Yes |  |  | Supported on Windows 8 and above and Windows Server 2012 and above |
| Microsoft Defender for Endpoint | WW | Microsoft Defender for Endpoint | 443 | `*.security.microsoft.com` | Microsoft Defender for Endpoint Vulnerability assessment for network devices \(network scanner\) | Optional | Yes | Yes | Yes |  |  | Supported on Windows 8 and above and Windows Server 2012 and above |
| Microsoft Defender for Endpoint | WW | Microsoft Defender for Endpoint | 443 | `reflector.defender.microsoft.com` | Used to probe IPv6 connectivity | Optional | Yes | Yes | Yes | Yes | Yes | Helps Microsoft Security Intelligence detect attacker activity |
| Microsoft Defender for Endpoint | WW | Microsoft Defender for Endpoint | 443 | `*.blob.core.windows.net/networkscannerstable/*` | Microsoft Defender for Endpoint Vulnerability assessment for network devices \(network scanner\) | Optional | Yes | Yes | Yes |  |  | Supported on Windows 8 and above and Windows Server 2012 and above |
| Microsoft Defender for Endpoint | WW | Security Management | 443 | `enterpriseregistration.windows.net` | Security Management for Microsoft Defender for Endpoint - Azure Registration | Optional | Yes |  |  |  |  | Only required when using Security Management for Microsoft Defender for Endpoint |
| Microsoft Defender for Endpoint | WW | Security Management | 443 | `*.dm.microsoft.com` | Security Management for Microsoft Defender for Endpoint - Enrollment, check-in, and reporting | Optional | Yes |  |  |  |  | Only required when using Security Management for Microsoft Defender for Endpoint |
| Microsoft Defender for Endpoint | WW | Microsoft Monitoring Agent \(MMA\) | 443 | `*.ods.opinsights.azure.com` | MMA for Win 7/8.1/2008R2/2012R2/2016 | Optional |  | Yes | Yes |  |  | Required when using MMA. For Windows Server 2012 R2 and 2016, consider migrating to the [Microsoft Defender for Endpoint unified agent](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server). Refer to steps at [https://aka.ms/mde\_network\_requirements](https://aka.ms/mde_network_requirements) to eliminate wildcards \(\*\) |
| Microsoft Defender for Endpoint | WW | Microsoft Monitoring Agent \(MMA\) | 443 | `*.oms.opinsights.azure.com` | MMA for Win 7/8.1/2008R2/2012R2/2016 | Optional |  | Yes | Yes |  |  | Required when using MMA. For Windows Server 2012 R2 and 2016, see the [Microsoft Defender for Endpoint unified agent](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server). Refer to steps at [https://aka.ms/mde\_network\_requirements](https://aka.ms/mde_network_requirements) to eliminate wildcards \(\*\) |
| Microsoft Defender for Endpoint | WW | Microsoft Monitoring Agent \(MMA\) | 443 | `*.blob.core.windows.net` | MMA for Win 7/8.1/2008R2/2012R2/2016 | Optional |  | Yes | Yes |  |  | Required when using MMA. For Windows Server 2012 R2 and 2016, see the [Microsoft Defender for Endpoint unified agent](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server). Refer to steps at [https://aka.ms/mde\_network\_requirements](https://aka.ms/mde_network_requirements) to eliminate wildcards \(\*\) |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `unitedstates.x.cp.wd.microsoft.com` | Used by Microsoft Defender Antivirus to provide cloud-delivered protection and security intelligence updates | Required |  |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `us.vortex-win.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Optional | Yes |  |  |  |  | Not required for Windows 10 1803 \(RS4\) and above / Windows Server 2019 and above |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `us-v20.events.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `winatp-gw-cus.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `winatp-gw-eus.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `winatp-gw-cus3.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `winatp-gw-eus3.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | Azure UAE Central \(AEC\) | Microsoft Defender for Endpoint AEC | 443 | `winatp-gw-aec0a.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | Azure UAE North \(AEN\) | Microsoft Defender for Endpoint AEN | 443 | `winatp-gw-aen0a.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `automatedirstrprdcus.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `automatedirstrprdeus.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `automatedirstrprdcus3.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `automatedirstrprdeus3.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `automatedirstrprdaen0a.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `automatedirstrprdaec0a.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `ussus1eastprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `ussus2eastprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `ussus3eastprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `ussus4eastprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `wsus1eastprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `wsus2eastprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `ussus1westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `ussus2westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `ussus3westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `ussus4westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `wsus1westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | US | Microsoft Defender for Endpoint US | 443 | `wsus2westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `europe.x.cp.wd.microsoft.com` | Used by Microsoft Defender Antivirus to provide cloud-delivered protection and security intelligence updates | Required |  |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `eu.vortex-win.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Optional | Yes |  |  |  |  | Not required for Windows 10 1803 \(RS4\) and above / Windows Server 2019 and above |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `eu-v20.events.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `winatp-gw-neu.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `winatp-gw-weu.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `winatp-gw-neu3.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `winatp-gw-weu3.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `automatedirstrprdneu.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `automatedirstrprdweu.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `automatedirstrprdneu3.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `automatedirstrprdweu3.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `usseu1northprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `wseu1northprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `usseu1westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | EU | Microsoft Defender for Endpoint EU | 443 | `wseu1westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `unitedkingdom.x.cp.wd.microsoft.com` | Used by Microsoft Defender Antivirus to provide cloud-delivered protection and security intelligence updates | Required |  |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `uk.vortex-win.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Optional | Yes |  |  |  |  | Not required for Windows 10 1803 \(RS4\) and above / Windows Server 2019 and above |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `uk-v20.events.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `winatp-gw-uks.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `winatp-gw-ukw.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `automatedirstrprduks.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `automatedirstrprdukw.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `ussuk1southprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `wsuk1southprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `ussuk1westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | UK | Microsoft Defender for Endpoint UK | 443 | `wsuk1westprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `australia.x.cp.wd.microsoft.com` | Used by Microsoft Defender Antivirus to provide cloud-delivered protection and security intelligence updates | Required |  |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `au.vortex-win.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Optional | Yes |  |  |  |  | Not required for Windows 10 1803 \(RS4\) and above / Windows Server 2019 and above |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `au-v20.events.data.microsoft.com` | Microsoft Defender for Endpoint EDR Cyber Data | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `winatp-gw-aue.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `winatp-gw-aus.microsoft.com` | Microsoft Defender for Endpoint Command and Control | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `automatedirstrprdaue.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `automatedirstrprdaus.blob.core.windows.net` | Microsoft Defender for Endpoint AutoIR Sample Storage | Required | Yes |  |  | Yes | Yes |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `ussau1southeastprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender for Endpoint | AU | Microsoft Defender for Endpoint AU | 443 | `ussau1eastprod.blob.core.windows.net` | Malware Sample Submission Storage | Required | Yes |  |  |  |  |  |
| Microsoft Defender Antivirus | WW | UTC | 443 | `vortex-win.data.microsoft.com` | Used by Windows to send client diagnostic data; Microsoft Defender Antivirus uses this for product quality monitoring purposes | Optional | Yes |  |  |  |  | Not required for Windows 10 1803 \(RS4\) and above / Windows Server 2019 |
| Microsoft Defender Antivirus | WW | MU / WU | 443 | `*.update.microsoft.com` | MU / WU - Security intelligence and product updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | WW | MU / WU | 443 | `*.delivery.mp.microsoft.com` | MU / WU - Security intelligence and product updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | WW | MU / WU | 443 | `*.windowsupdate.com` | MU / WU - Security intelligence and product updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | WW | MU / WU | 443 | `go.microsoft.com` | MU / WU - Security intelligence and product updates | Required | Yes\* | Yes\* | Yes\* | Yes | Yes | \*Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\)  <br>Required for Mac and Linux platforms |
| Microsoft Defender Antivirus | WW | MU / WU | 443 | `definitionupdates.microsoft.com` | MU / WU - Security intelligence and product updates | Required | Yes\* | Yes\* | Yes\* | Yes | Yes | \*Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\)  <br>Required for Mac and Linux platforms |
| Microsoft Defender Antivirus | WW | MU / WU | 443 | `https://www.microsoft.com/security/encyclopedia/adlpackages.aspx` | MU / WU - Security intelligence and product updates | Required | Yes\* | Yes\* | Yes | Yes | Yes | \*Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\)  <br>Required for Mac and Linux platforms |
| Microsoft Defender Antivirus | WW | MU \(ADL\) | 443 | `*.download.windowsupdate.com` | ADL - Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | WW | MU \(ADL\) | 443 | `*.download.microsoft.com` | ADL - Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | WW | MU \(ADL\) | 443 | `fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx` | ADL - Alternate location for Microsoft Defender Antivirus Security intelligence updates | Optional | Yes | Yes | Yes |  |  | Optional if updates are being managed internally \(WSUS/FileShare/ConfigMgr\) |
| Microsoft Defender Antivirus | WW | MAPS | 443 | `*.wdcp.microsoft.com` | MAPS - Used by Microsoft Defender Antivirus to provide cloud-delivered protection | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender Antivirus | WW | MAPS | 443 | `*.wd.microsoft.com` | MAPS - Used by Microsoft Defender Antivirus to provide cloud-delivered protection | Required | Yes | Yes | Yes | Yes | Yes |  |
| Microsoft Defender Antivirus | WW | Common | 443 | `*.events.data.microsoft.com` | Used by Microsoft Defender Antivirus to send Diagnostic Telemetry for Microsoft Defender Core Service | Required | Yes | No | Yes | No | No | To enhance your endpoint security experience, Microsoft is releasing the Microsoft Defender Core service to help with the stability and performance of Microsoft Defender Antivirus. Alternatively, to wildcard, can allow: us-mobile.events.data.microsoft.com/OneCollector/1.0 eu-mobile.events.data.microsoft.com/OneCollector/1.0 uk-mobile.events.data.microsoft.com/OneCollector/1.0 au-mobile.events.data.microsoft.com/OneCollector/1.0 mobile.events.data.microsoft.com/OneCollector/1.0 |
| Microsoft Defender Antivirus | WW | Common | 443 | `*ecs.office.com/config/v1/MicrosoftWindowsDefenderClient` | Used by Microsoft Defender Antivirus to download internal feature configurations \(ECS\) for Microsoft Defender Core service | Required | Yes | No | Yes | No | No | Microsoft Defender Core service is used to enhance stability and performance of Microsoft Defender Antivirus for customers. |
| Microsoft Defender SmartScreen | WW | Reporting and Notifications | 443 | `*.smartscreen-prod.microsoft.com` | Used for Microsoft Defender SmartScreen protection, reporting, and notifications. Microsoft Defender Antivirus Network Protection and custom URL indicators | Required | Yes |  |  | Yes | Yes | Microsoft Defender SmartScreen reporting and notifications. Network Protection and custom URL indicators |
| Microsoft Defender SmartScreen | WW | Reporting and Notifications | 443 | `*.smartscreen.microsoft.com` | Used for Microsoft Defender SmartScreen protection, reporting, and notifications. Microsoft Defender Antivirus Network Protection and custom URL indicators | Required | Yes |  |  | Yes | Yes | Microsoft Defender SmartScreen reporting and notifications. Network Protection and custom URL indicators |
| Microsoft Defender SmartScreen | WW | Reporting and Notifications | 443 | `*.checkappexec.microsoft.com` | Used for Microsoft Defender SmartScreen to check application execution for trusted apps | Optional | Yes |  |  |  |  | Microsoft Defender SmartScreen checking application execution for trusted apps |
| Microsoft Defender SmartScreen | WW | Reporting and Notifications | 443 | `*.urs.microsoft.com` | Used for Microsoft Defender SmartScreen to check application execution for trusted apps | Optional | Yes |  |  |  |  | Microsoft Defender SmartScreen checking application execution for trusted apps |
| Consolidated Defender for Endpoint services | WW | Streamlined connectivity new URL pattern | 443 | `*.endpoint.security.microsoft.com` | Used for streamlined connectivity URL consolidation as well as for future services | Required | Yes | No | Yes | Yes | Yes | Only required for streamlined connectivity initially. New services also follow this new pattern. |

## Defender portal URLs

This section lists the URLs needed to open the Microsoft Defender portal in a browser.

Note

All URLs in this table are required for access to the Microsoft Defender portal.

| Service | Geography | URL |
| --- | --- | --- |
| Microsoft Defender for Endpoint | WW | `*.blob.core.windows.net` |
| Microsoft Defender for Endpoint | WW | `crl.microsoft.com` |
| Microsoft Defender for Endpoint | WW | `https://*.microsoftonline-p.com` |
| Microsoft Defender for Endpoint | WW | `https://secure.aadcdn.microsoftonline-p.com` |
| Microsoft Defender for Endpoint | WW | `https://static2.sharepointonline.com` |
| Microsoft Defender for Endpoint | WW | `https://login.microsoftonline.com` |
| Microsoft Defender for Endpoint | WW | `https://*.securitycenter.windows.com` |
| Microsoft Defender for Endpoint | WW | `https://onboardingpackagescusprd.blob.core.windows.net` |
| Microsoft 365 Defender | WW | `https://security.microsoft.com` |

## Required client processes for network connectivity

Because the Microsoft Defender for Endpoint client processes in this section generate network communications, make sure that traffic from those processes is not blocked.

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

This section summarizes recent changes to this article and its endpoint listings.

| Date | Change Log |
| --- | --- |
| 06/02/2026 | Added `reflector.defender.microsoft.com`. |
| 04/14/2026 | Replaced `officecdn-microsoft-com.akamaized.net` with new CDN ChannelURL reference for Mac/Linux product updates. New CDN endpoint starting with macOS build 101.26012.0012. |
| 04/13/2026 | Added SmartScreen URLs \(`*.checkappexec.microsoft.com`, `*.urs.microsoft.com`\) to [Microsoft Defender URLs](#microsoft-defender-urls). |
| 03/26/2026 | Added new Azure UAE North \(AEN\) and Azure UAE Central \(AEC\) URLs to the [Microsoft Defender URLs](#microsoft-defender-urls) section: `winatp-gw-aec0a.microsoft.com`, `winatp-gw-aen0a.microsoft.com`, `automatedirstrprdaen0a.blob.core.windows.net`,`automatedirstrprdaec0a.blob.core.windows.net`. |
| 03/26/2026 | Renamed **Microsoft Defender processes** section to **Client processes**, and aligned the content for all URL lists. |
| 16/06/2025 | Corrected row 94, Defender Core service and ECS, to be listed as "Required".  <br>Corrected row 93, `*.events.data.microsoft.com`, to be listed as "Required". |
| 22/01/2024 | Updates for URLs required for Microsoft Defender Core service and DLP service processes:  <br>Added new line 93 for 1DS URL in Microsoft Defender URLs.  <br>Added new line 94 for ECS URL in Microsoft Defender URLs.  <br>Added new line 8 for Defender Core Service in Microsoft Defender Processes.  <br>Added new line 9 for Purview DLP Process. |
