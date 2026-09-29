<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/gov -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# Microsoft Defender for Endpoint for US Government customers

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Microsoft Defender for Endpoint for US Government customers, built in the Azure US Government environment, uses the same underlying technologies as Defender for Endpoint in Azure Commercial.

This offering is available to GCC, GCC High, and DoD customers and is based on the same prevention, detection, investigation, and remediation as the commercial version. However, there are some differences in the availability of capabilities for this offering.

Note

If you're a GCC customer using Defender for Endpoint in Commercial, see the [Defender for Endpoint documentation](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint).

## Licensing requirements

Microsoft Defender for Endpoint for US Government customers requires one of the Microsoft volume licensing offers listed in this article for desktop and server licensing.

### Desktop licensing

| GCC | GCC High | DoD |
| --- | --- | --- |
| Microsoft 365 GCC G5 | Microsoft 365 E5 for GCC High | Microsoft 365 G5 for DOD |
| Microsoft 365 G5 Security GCC | Microsoft 365 G5 Security for GCC High | Microsoft 365 G5 Security for DOD |
| Microsoft Defender for Endpoint - GCC | Microsoft Defender for Endpoint for GCC High | Microsoft Defender for Endpoint for DOD |
| Windows 10 Enterprise E5 GCC | Windows 10 Enterprise E5 for GCC High | Windows 10 Enterprise E5 for DOD |

- \*G3 includes Microsoft Defender for Endpoint Plan 1

### Server licensing

| GCC | GCC High | DoD |
| --- | --- | --- |
| Microsoft Defender for Endpoint Server GCC | Microsoft Defender for Endpoint Server for GCC High | Microsoft Defender for Endpoint Server for DOD |
| Microsoft Defender for servers | Microsoft Defender for servers - Government | Microsoft Defender for servers - Government |

## Portal URLs

The following are the Microsoft Defender for Endpoint portal URLs for US Government customers:

| Customer type | Portal URL |
| --- | --- |
| GCC | [https://security.microsoft.com](https://security.microsoft.com) |
| GCC High | [https://security.microsoft.us](https://security.microsoft.us) |
| DoD | [https://security.apps.mil](https://security.apps.mil) |

Note

If you're a GCC customer and in the process of moving from Microsoft Defender for Endpoint commercial to GCC, use [https://transition.security.microsoft.com](https://transition.security.microsoft.com) to access your Microsoft Defender for Endpoint commercial data.

## Endpoint versions

### Standalone OS versions

The following OS versions are supported:

| OS version | GCC | GCC High | DoD |
| :--- | :---: | :---: | :---: |
| Windows 11 | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows 10, version 21H1 and later | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows 10, version 20H2 \(with [KB4586853](https://support.microsoft.com/servicing/os/windows-10/2020/11/november-30-2020-kb4586853-os-builds-19041-662-and-19042-662-preview)\)  <br>See note 1 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows 10, version 2004 \(with [KB4586853](https://support.microsoft.com/servicing/os/windows-10/2020/11/november-30-2020-kb4586853-os-builds-19041-662-and-19042-662-preview)\)  <br>See note 1 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-version-2004-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-version-2004-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-version-2004-end-of-servicing); upgrade now |
| Windows 10, version 1909 \(with [KB4586819](https://support.microsoft.com/topic/november-19-2020-kb4586819-os-builds-18362-1237-and-18363-1237-preview-25cbb849-74af-b8b8-29b8-68aa925e8cc3)\)  <br>See note 1 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1909-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1909-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1909-end-of-servicing); upgrade now |
| Windows 10, version 1903 \(with [KB4586819](https://support.microsoft.com/topic/november-19-2020-kb4586819-os-builds-18362-1237-and-18363-1237-preview-25cbb849-74af-b8b8-29b8-68aa925e8cc3)\)  <br>See note 1 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1903-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1903-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1903-end-of-servicing); upgrade now |
| Windows 10, version 1809 \(with [KB4586839](https://support.microsoft.com/topic/november-19-2020-kb4586839-os-build-17763-1613-preview-aeebda71-959c-48e0-204f-7d9dc84db0f0)\)  <br>See note 1 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1803-1809-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1803-1809-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1803-1809-end-of-servicing); upgrade now |
| Windows 10, version 1803 \(with [KB4598245](https://support.microsoft.com/servicing/os/windows-10/2021/01/january-12-2021-kb4598245-os-build-17134-1967-expired)\)  <br>See note 1 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1803-1809-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1803-1809-end-of-servicing); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-1803-1809-end-of-servicing); upgrade now |
| Windows 10, version 1709 | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg)  <br>Not supported | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) With [KB4499147](https://support.microsoft.com/servicing/os/windows-10/2019/05/may-28-2019-kb4499147-os-build-16299-1182)  <br>See note 1 following this table  <br>[Deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/revised-end-of-service-windows-10-1709); upgrade now | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg)  <br>Not supported |
| Windows 10, version 1703 and earlier | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg)  <br>Not supported | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg)  <br>Not supported | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg)  <br>Not supported |
| Windows Server 2022 and later | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2019 \(with [KB4586839](https://support.microsoft.com/topic/november-19-2020-kb4586839-os-build-17763-1613-preview-aeebda71-959c-48e0-204f-7d9dc84db0f0)\)  <br>See note 1 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2016 \(Modern\)  <br>See note 2 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2012 R2 \(Modern\)  <br>See note 2 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2016 \(Legacy\)  <br>See note 3 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2012 R2 \(Legacy\)  <br>See note 3 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2008 R2 SP1 \(Legacy\)  <br>See note 3 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows 8.1 Enterprise \(Legacy\)  <br>See note 3 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows 8 Pro \(Legacy\)  <br>See note 3 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows 7 SP1 Enterprise \(Legacy\)  <br>See note 3 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows 7 SP1 Pro \(Legacy\)  <br>See note 3 following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Linux | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| macOS | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Android | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br> | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br> | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br> |
| iOS | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br> | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br> | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br> |

Note

- The patch must be deployed before device onboarding in order to configure Defender for Endpoint to the correct environment.
- Learn about the [unified modern solution for Windows 2016 and 2012 R2](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2). If you previously onboarded your servers using MMA, follow the guidance provided in [Server migration](https://learn.microsoft.com/en-us/defender-endpoint/server-migration) to migrate to the new solution.
- When using the [Microsoft Monitoring Agent](https://learn.microsoft.com/en-us/defender-endpoint/onboard-downlevel#install-and-configure-microsoft-monitoring-agent-windows-81-only) make sure to choose `Azure US Government` under **Azure Cloud** if using the [setup wizard](https://learn.microsoft.com/en-us/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard). If you're using a [command line](https://learn.microsoft.com/en-us/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) or a [script](https://learn.microsoft.com/en-us/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation), set the `OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE` parameter to `1`. The minimum MMA supported version is `10.20.18029` \(March 2020\).

### OS versions when using Microsoft Defender for servers

The following OS versions are supported when using [Microsoft Defender for servers](https://learn.microsoft.com/en-us/azure/security-center/security-center-wdatp):

| OS version | GCC | GCC High | DoD |
| :--- | :---: | :---: | :---: |
| Windows Server 2022 and later | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2019 | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2016 | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2012 R2 | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Windows Server 2008 R2 SP1 | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |

## Required connectivity settings

If a proxy or firewall is blocking all traffic by default and allowing only specific domains through, add the domains listed in the downloadable sheet to the allowed domains list.

Note

You can use the [streamlined connectivity feature](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity) to onboard new government devices to Defender for Endpoint, using a reduced URL set or static IP ranges. A dedicated endpoint group supports streamlined connectivity in government environments, and consolidates several service dependencies into a smaller set of URLs.

The following URL lists include the services and their associated URLs your network must be able to connect to. Verify there are no firewall or network-filtering rules that would deny access to these URLs, or create an *allow* rule specifically for them.

| URL list | Description |
| --- | --- |
| Microsoft Defender for Endpoint Streamlined Connectivity URL list for Gov/GCC/DoD \(Preview\) | List of consolidated URLs for service locations, geographic locations, and OS for Gov/GCC/DoD customers.  <br>  <br>[See the full list](https://learn.microsoft.com/en-us/defender-endpoint/streamlined-device-connectivity-urls-gov). |
| Microsoft Defender for Endpoint Standard Connectivity URL list for Gov/GCC/DoD | List of specific DNS records for service locations, geographic locations, and OS for Gov/GCC/DoD customers.  <br>  <br>[See the full list](https://learn.microsoft.com/en-us/defender-endpoint/standard-device-connectivity-urls-gov) |

For more information, see [Configure device proxy and Internet connectivity settings](https://learn.microsoft.com/en-us/defender-endpoint/configure-proxy-internet).

## API

Instead of the public URIs listed in our [API documentation](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-list), you need to use the following URIs:

| Endpoint type | GCC | GCC High & DoD |
| --- | --- | --- |
| Sign in | `https://login.microsoftonline.com` | `https://login.microsoftonline.us` |
| Defender for Endpoint API | `https://api-gcc.securitycenter.microsoft.us` | `https://api-gov.securitycenter.microsoft.us` |

## Feature parity with commercial

Defender for Endpoint for US Government customers doesn't have complete parity with the commercial offering. While our goal is to deliver all commercial features and functionality to our US Government customers, there are some capabilities not yet available we want to highlight.

These are the known gaps:

| Feature name | GCC | GCC High | DoD |
| --- | :---: | :---: | :---: |
| Microsoft Secure Score | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg)  <br>See note following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Microsoft Threat Experts | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg) |
| Microsoft Defender for Endpoint Security Configuration Management | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Microsoft Defender for IoT enterprise IoT security | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-no.svg) |

Note

While Microsoft Secure Score is available for GCC, GCC High and DoD customers, there are some security recommendations that aren't available.

These are the features and known gaps for [Mobile Threat Defense \(Microsoft Defender for Endpoint on Android & iOS\)](https://learn.microsoft.com/en-us/defender-endpoint/mtd):

| Feature name | GCC | GCC High | DoD |
| --- | :---: | :---: | :---: |
| Reports: Web content filtering | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Reports: Device health | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Web Protection \(Anti-Phishing and custom indicators\) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Malware Protection \(Android-Only\) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Jailbreak Detection \(iOS-Only\) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Conditional Access/Conditional Launch | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Support for MAM | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Privacy Controls | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Microsoft Defender Vulnerability Management core capabilities  <br>\(included in Defender for Endpoint Plan 2\)  <br>See note following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |
| Microsoft Defender Vulnerability Management premium capabilities  <br>See note following this table | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) | ![](https://learn.microsoft.com/en-us/defender-endpoint/media/svg/check-yes.svg) |

Note

The following Defender Vulnerability Management functionality isn't available for GCC, GCC High, and DoD customers:

- Report inaccuracy
- Request CVE support

## Upgrade the XDR security portal experience

If your organization has a Microsoft 365 Business Premium license and Microsoft Defender Suite, you can upgrade the XDR security portal experience to Plan 2 \(P2\) by opening a [support request](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
