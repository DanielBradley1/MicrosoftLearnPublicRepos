<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements -->
<!-- Sitemap-Last-Modified: 2025-11-17 -->

# Minimum requirements for Microsoft Defender for Endpoint

There are some minimum requirements for onboarding devices to Defender for Endpoint. This article describes licensing, hardware and software requirements, and other configuration settings needed to onboard devices.

Tip

- For information about the latest enhancements in Defender for Endpoint, see [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
- For information about how Defender for Endpoint demonstrates industry-leading optics and detection capabilities, see [Insights from the MITRE ATT&CK-based evaluation](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).
- If you're looking for endpoint protection for small and medium-sized businesses, see [Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview) and [Defender for Business requirements](https://learn.microsoft.com/en-us/defender-business/mdb-requirements).

### Licensing requirements

- To [onboard servers](https://learn.microsoft.com/en-us/defender-endpoint/onboard-windows-server) to Defender for Endpoint, server licenses are required. You can choose from:

  - Microsoft Defender for Servers Plan 1 or Plan 2 \(as part of the [Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)\) offering
  - Microsoft Defender for Endpoint Server
  - [Microsoft Defender for Business servers](https://learn.microsoft.com/en-us/defender-business/get-defender-business) \(for small and medium-sized businesses only\)

For more detailed information about licensing requirements for Microsoft Defender for Endpoint, see [Microsoft Defender for Endpoint licensing information](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).

For detailed licensing information, see the [Product Terms site](https://www.microsoft.com/licensing/terms/) and work with your account team to learn more about the terms and conditions.

## Browser requirements

Access Microsoft Defender for Endpoint and other [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/) experiences in the Microsoft Defender portal using Microsoft Edge, Internet Explorer 11, or any HTML 5 compliant web browser.

## Hardware and software requirements

Devices on your network must be running one of the operating systems listed in this article. New features or capabilities are typically provided only on vendor-supported operating systems. For more information, see [Supported Microsoft Defender for Endpoint capabilities by platform](https://learn.microsoft.com/en-us/defender-endpoint/supported-capabilities-by-platform). Microsoft recommends installing the latest available security patches for any operating system.

### Windows versions supported by Defender for Endpoint

Important

You may continue to use Microsoft Windows after OS support ends; however, it will no longer receive quality updates, new or updated features, or security updates for the operating system itself. However, devices protected by Microsoft Defender for Endpoint will continue to receive regular product updates through existing channels, keeping detection and protection capabilities current.

- Windows 10 and 11 Enterprise, IoT Enterprise, Education, Pro, Pro Education including [Windows on Arm](https://learn.microsoft.com/en-us/windows/arm/overview)
- [Windows Enterprise LTSC 2016 \(and later\)](https://learn.microsoft.com/en-us/windows/whats-new/ltsc/)
- [Windows Enterprise multi-session](https://learn.microsoft.com/en-us/azure/virtual-desktop/windows-multisession-faq)
- Windows 7 SP1 Pro, Enterprise, provided that you onboard using the [Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows).
- Windows 8.1 Pro, Enterprise, provided that you onboard using the [Log Analytics](https://learn.microsoft.com/en-us/azure/azure-monitor/agents/log-analytics-agent) / [Microsoft Monitoring Agent](https://learn.microsoft.com/en-us/defender-endpoint/update-agent-mma-windows) \(MMA\)
- Windows Server

  - Windows Server 2012 R2 and later \(including Core installation type\)
  - Windows Server Semi-Annual Channel, version 1803 and later
  - Windows Server 2008 R2 SP1, provided that you onboard using the [Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows).

- [Windows 365](https://learn.microsoft.com/en-us/windows-365/) Cloud PCs and supported [Azure \(Windows\) Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/) machines running one of the previously listed operating systems/versions
- [Azure Local](https://learn.microsoft.com/en-us/azure/azure-local) Nodes running Azure Stack HCI OS, version 23H2 and later

Note

To avoid service interruptions, make sure to [stay up to date with the Microsoft Monitoring Agent](https://learn.microsoft.com/en-us/defender-endpoint/update-agent-mma-windows) \(MMA, also known as the Log Analytics or Azure Monitor agent\).

To add anti-malware protection to these older operating systems, you can use [System Center Endpoint Protection](https://learn.microsoft.com/en-us/defender-endpoint/onboard-downlevel#configure-and-update-system-center-endpoint-protection-clients).

### Other operating systems supported by Defender for Endpoint

- [Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac) \(client devices\)
- [Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/defender-endpoint/mde-plugin-wsl)
- [Android](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-android)
- [iOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-ios)

Note

- Make sure to confirm that the Linux distributions and versions of Android, iOS, and macOS are compatible with Defender for Endpoint.
- Although Windows 10 IoT Enterprise is a supported OS in Microsoft Defender for Endpoint and enables OEMs/ODMs to distribute it as part of their product or solution, customers should follow the OEM/ODM's guidance around host-based installed software and supportability.
- Endpoints running mobile versions of Windows \(such as Windows CE and Windows 10 Mobile\) aren't supported.
- Virtual Machines running Windows 10 Enterprise 2016 LTSB can encounter performance issues when used on non-Microsoft virtualization platforms.
- For virtual environments, we recommend using Windows 10 Enterprise LTSC 2019 or later.
- [Defender for Endpoint Plan 1 and Plan 2](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) don't include server licenses. To onboard servers to those plans, you need another license, such as Microsoft Defender for Servers Plan 1 or Plan 2 \(as part of the [Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction) offering\). To learn more. see [Defender for Endpoint onboarding Windows Server](https://learn.microsoft.com/en-us/defender-endpoint/onboard-windows-server).
- If your organization is a small or medium-sized business, see [Microsoft Defender for Business requirements](https://learn.microsoft.com/en-us/defender-business/mdb-requirements).
- Windows 11 24H2 Home devices that have been upgraded to a supported edition might require you to run the following command before onboarding: `DISM /online /Add-Capability /CapabilityName:Microsoft.Windows.Sense.Client~~~~`. For more information about edition upgrades and features, see [Windows features](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-features?view=windows-11&preserve-view=true).

### Hardware requirements

The minimum hardware requirements for Defender for Endpoint on Windows devices are the same as the requirements for the operating system itself \(that is, they aren't in addition to the requirements for the operating system\).

- Cores: 2 minimum, 4 preferred
- Memory: 1GB minimum, 4 GB preferred

### Network and data storage and configuration requirements

When you run the onboarding wizard for the first time, you must choose where your Microsoft Defender for Endpoint-related information is stored: in the European Union, the United Kingdom, or the United States datacenter.

Note

- You can't change your data storage location after the first-time setup.
- Review the [Microsoft Defender for Endpoint data storage and privacy](https://learn.microsoft.com/en-us/defender-endpoint/data-storage-privacy) for more information on where and how Microsoft stores your data.

#### IP stack

Internet Protocol Version 4 \(IPv4\) stack must be enabled on devices for communication to the Defender for Endpoint cloud service to work as expected.

Alternatively, if you must use an Internet Protocol Version 6 \(IPv6\) only configuration, consider adding dynamic IPv6/IPv4 transitional mechanisms, such as DNS64/NAT64 to ensure end-to-end IPv6 connectivity to Microsoft 365 without any other network reconfiguration.

#### Internet connectivity

Internet connectivity on devices is required either directly or through a proxy.

For more information on other proxy configuration settings, see [Configure device proxy and Internet connectivity settings](https://learn.microsoft.com/en-us/defender-endpoint/configure-proxy-internet).

## Microsoft Defender Antivirus configuration requirement

The Defender for Endpoint agent depends on Microsoft Defender Antivirus to scan files and provide information about them.

Configure Security intelligence updates on the Defender for Endpoint devices whether Microsoft Defender Antivirus is the active anti-malware solution or not. For more information, see [Manage Microsoft Defender Antivirus updates and apply baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates).

When Microsoft Defender Antivirus isn't the active anti-malware in your organization and you use the Defender for Endpoint service, Microsoft Defender Antivirus goes into passive mode.

If your organization turns off Microsoft Defender Antivirus through Group Policy or other methods, devices that are onboarded must be excluded from the Group Policy.

If you're onboarding servers and Microsoft Defender Antivirus isn't the active anti-malware on your servers, configure Microsoft Defender Antivirus to run in passive mode or uninstall it. The configuration is dependent on the server version. For more information, see [Microsoft Defender Antivirus compatibility](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility).

Note

Your regular Group Policy doesn't apply to tamper protection, and changes to Microsoft Defender Antivirus settings are ignored when tamper protection is on. See [What happens when tamper protection is turned on](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#what-happens-when-tamper-protection-is-turned-on)?

## Microsoft Defender Antivirus Early Launch Antimalware \(ELAM\) driver is enabled

If you're running Microsoft Defender Antivirus as the primary anti-malware product on your devices, the Defender for Endpoint agent successfully onboards.

If you're running a non-Microsoft anti-malware client and use Mobile Device Management solutions or Microsoft Configuration Manager \(current branch\), you need to ensure the Microsoft Defender Antivirus ELAM driver is enabled. For more information, see [Ensure that Microsoft Defender Antivirus isn't disabled by policy](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## Related articles

- [Set up Microsoft Defender for Endpoint deployment](https://learn.microsoft.com/en-us/defender-endpoint/production-deployment)
- [Onboard devices](https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure)
