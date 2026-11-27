<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/china -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Intune operated by 21Vianet in China

Intune operated by 21Vianet is designed to meet the needs for secure, reliable, and scalable cloud services in China. Intune as a service is built on top of Microsoft Azure. Microsoft Azure operated by 21Vianet is a physically separated instance of cloud services located in China. It's independently operated and transacted by 21Vianet. This service is powered by technology that Microsoft has licensed to 21Vianet.

Microsoft doesn't operate the service itself. 21Vianet operates, provides, and manages delivery of the service. 21Vianet is an Internet data center services provider in China. It provides hosting, managed network services, and cloud computing infrastructure services. By licensing Microsoft technologies, 21Vianet operates local datacenters to provide you with the ability to use Intune service while keeping your data within China. 21Vianet also provides your subscription, billing, and support services.

Note

If you're interested in viewing or deleting personal data, see the [Azure Data Subject Requests for the GDPR](https://learn.microsoft.com/en-us/microsoft-365/compliance/gdpr-dsr-azure) article. If you're looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## Features differences in Intune operated by 21Vianet

The following features are available in Intune operated by 21Vianet. The table describes differences from the commercial service.

| Feature | Availability |
| --- | --- |
| **Deployments and co-management** | Only standalone Intune deployments are supported. You can use co-management to attach an existing Configuration Manager deployment to Intune.  <br>  <br>For more information, see [Co-management for Windows devices](https://learn.microsoft.com/en-us/intune/configmgr/comanage/overview). |
| **Windows device management** | Supported through the modern mobile device management \(MDM\) channel.  <br>  <br>For more information, see [Windows enrollment methods](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/guide). |
| **Company Portal for Windows** | Supported. Use WinGet to download the Company Portal package and dependencies, then deploy it as a line-of-business app through Intune.  <br>  <br>For more information, see [Use the WinGet tool to install and manage applications](https://learn.microsoft.com/en-us/windows/package-manager/winget/). |
| **Company Portal for Android** | The app uses Google Mobile Services \(GMS\) to communicate with Intune. Because Google Play services are unavailable in China, some tasks can take up to 8 hours to finish.  <br>  <br>For more information, see [Limitations of Intune management when GMS is unavailable](https://learn.microsoft.com/en-us/intune/app-management/manage-without-gms#limitations-of-intune-management-when-gms-is-unavailable). |
| **Company Portal client experience** | The client experience can differ in China to meet local regulations and provide improved functionality.  <br>  <br>For more information, see [Install Company Portal in People's Republic of China](https://learn.microsoft.com/en-us/intune/user-help/company-portal/install-android-china). |
| **Mobile Application Management \(MAM\)** | Availability depends on whether the apps are available in People's Republic of China.  <br>  <br>For more information, see [Microsoft Intune protected apps](https://learn.microsoft.com/en-us/intune/app-management/ref-protected-apps). |
| **Mobile Threat Defense \(MTD\)** | Connectors for Android and iOS/iPadOS devices are supported when the MTD partner also supports the 21Vianet environment. Sign in to your 21Vianet tenant to view the available connectors.  <br>  <br>For more information, see [Mobile Threat Defense integration with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/overview). |

## Intune features not available in Intune operated by 21Vianet

The following features are not available in Intune operated by 21Vianet. Windows Autopilot device preparation is listed separately in the [planned features](#intune-features-planned-for-intune-operated-by-21vianet) section.

| Feature | Availability |
| --- | --- |
| **[App and driver compatibility reports for Windows updates](https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-compatibility)** | Not available. |
| **[Apple Managed account federation](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-apple-federation-customers)** | Not available. |
| **[Chrome Enterprise Connector](https://learn.microsoft.com/en-us/intune/device-enrollment/configure-chrome-enterprise-connector)** | Not available. |
| **[eSIM cellular support on Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-esim-download-server)** | Not available. |
| **[Intune Power BI connector for Data Warehouse](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/connect-power-bi)** | Not available. |
| **[Microsoft Connected Cache for Enterprise and Education](https://learn.microsoft.com/en-us/windows/deployment/do/mcc-ent-edu-overview)** | Not available. |
| **[Microsoft Store for Business](https://learn.microsoft.com/en-us/lifecycle/announcements/microsoft-store-for-business-education-retiring)** | Not available. |
| **On-premises Exchange Connector** | Not available. |
| **[Remediations](https://learn.microsoft.com/en-us/intune/device-management/tools/deploy-remediations)** | Not available. |
| **[Reports for feature update policies](https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-feature-updates)** | Not available. |
| **[ServiceNow connector](https://learn.microsoft.com/en-us/intune/device-management/tools/setup-servicenow)** | Not available. |
| **[TeamViewer connector \(legacy\)](https://learn.microsoft.com/en-us/intune/device-management/tools/teamviewer-legacy) and [TeamViewer integration](https://learn.microsoft.com/en-us/intune/device-management/tools/setup-teamviewer)** | Not available. |
| **[Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/overview)** | Not available, including Windows Autopilot with co-management. |
| **[Windows Backup for Organizations](https://learn.microsoft.com/en-us/windows/configuration/windows-backup/?tabs=intune)** | Not available. |
| **[Windows Diagnostic Data processor configuration](https://learn.microsoft.com/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enable-windows-diagnostic-data-processor-configuration)** | Not available. |
| **[Azure Virtual Desktop Windows Enterprise multi-session](https://learn.microsoft.com/en-us/intune/solutions/azure-virtual-desktop-multi-session)** | Not available. |
| **[Windows Subscription Activation](https://learn.microsoft.com/en-us/windows/deployment/windows-subscription-activation?pivots=windows-11)** | Not available. |
| **[Migration from public clouds to sovereign clouds](https://learn.microsoft.com/en-us/intune/fundamentals/setup-migration)** | Built-in migration is not supported. To move to Intune operated by 21Vianet, you must migrate manually. |
| **[Tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions)** | Syncing devices to Intune without enrollment to support cloud console scenarios is not supported. |
| **[Derived credentials](https://learn.microsoft.com/en-us/intune/device-security/certificates/derived-credentials)** | Not available. |
| **[Log Analytics](https://learn.microsoft.com/en-us/intune/governance/integrate-azure-monitor)** | Not available. |
| **[Google Play Protect capabilities](https://learn.microsoft.com/en-us/intune/app-management/manage-without-gms#unavailable-intune-features)** | Not available, including Play integrity verdict, because GMS is unavailable in China. |
| **[Google Play Store app management](https://learn.microsoft.com/en-us/intune/app-management/manage-without-gms#unavailable-intune-features)** | Not available because GMS is unavailable in China. |
| **[Android Enterprise](https://learn.microsoft.com/en-us/intune/device-enrollment/android/guide)** | Not available because GMS is unavailable in China. |
| **Fencing** | Not available. |
| **[Android Open Source Project \(AOSP\) management](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-userless)** | Not supported for corporate devices. |
| **[Jamf partner device management integration](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/configure-jamf-cloud-connector)** | Not supported for macOS devices. |
| **[Microsoft Intune advanced capabilities](https://learn.microsoft.com/en-us/intune/fundamentals/advanced-capabilities)** | None of the following advanced capabilities are available:  <br>  <br>- [Firmware Over-the-Air updates](https://learn.microsoft.com/en-us/intune/device-updates/android/manage-fota)  <br>- [Specialty device management](https://learn.microsoft.com/en-us/intune/device-management/specialty-devices)  <br>- [Microsoft Tunnel for MAM](https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/mam)  <br>- [Advanced Analytics](https://learn.microsoft.com/en-us/intune/advanced-analytics/)  <br>- [Remote Help](https://learn.microsoft.com/en-us/intune/remote-help/)  <br>- [Microsoft Cloud PKI](https://learn.microsoft.com/en-us/intune/cloud-pki/)  <br>- [Endpoint Privilege Management](https://learn.microsoft.com/en-us/intune/epm/overview)  <br>- [Enterprise Application Management](https://learn.microsoft.com/en-us/intune/app-management/deployment/enterprise-app-management) |
| **Autopatch and updates** | [Windows Autopatch](https://learn.microsoft.com/en-us/windows/deployment/windows-autopatch/overview/windows-autopatch-overview) |
|  | [Feature updates for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-feature-updates) |
|  | [Quality updates for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-quality-updates) |
|  | [Expedite updates for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-expedite-policy) |
|  | [Driver updates for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-driver-update-policy) |
|  | [Delivery Optimization for Win32 Apps](https://learn.microsoft.com/en-us/windows/deployment/do/waas-delivery-optimization) |
| **[Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot)** | Not available. |

## Intune features planned for Intune operated by 21Vianet

The following features are currently not available and aren't supported in in Intune operated by 21Vianet. This list is not comprehensive and is provided as directional guidance into key planned investments. Plans, target dates, and capabilities are subject to change. As features become generally available, or are cancelled or postponed, information will be removed from this list.

| Feature | Feature documentation |
| --- | --- |
| **[Windows Autopilot device preparation](https://learn.microsoft.com/en-us/autopilot/device-preparation/overview)** | Customize out-of-box experience \(OOBE\) and rename devices during provisioning based on organizational structure |
|  | Self-deploying and pre-provisioning mode |
|  | More admin-specified configurations delivered before allowing desktop access |
|  | Enhanced optional desktop onboarding experience inside the Windows Company Portal app |
|  | The ability to associate a device with a tenant. Provisioning modes which require Windows Autopilot registration are not supported. |
| **[App inventory](https://learn.microsoft.com/en-us/intune/app-management/deployment/enhanced-app-inventory)** | Collect detailed application data from Windows devices. |
| **[Properties catalog](https://learn.microsoft.com/en-us/intune/device-configuration/collect-device-properties)** | Collect device properties from Windows devices. |

## You control customer data

In Microsoft Azure, Intune, Microsoft 365, and Power BI operated by 21Vianet, you have full control of your data:

- You know where customer data is located.
- You control access to your customer data.
- You control your customer data if you leave the service.
- You have options to control the security of your customer data.

With Microsoft Azure, Intune, Microsoft 365, and Power BI operated by 21Vianet, you're the owner of your data:

- 21Vianet doesn't use customer data for advertising.
- You control who has access to your customer data.
- We use logical isolation to segregate each customer's data.
- We provide simple, transparent data-use policies, and get independent audits.
- Our subcontractors are under contract to meet our privacy requirements.

## Data subject requests

The Tenant Administrator role for Intune operated by 21Vianet can request data for data subjects in the following ways:

- In the Microsoft Entra admin center, a Tenant Administrator can permanently delete a data subject from Microsoft Entra ID and related services. For more information, see [Azure Data Subject Requests - Delete](https://learn.microsoft.com/en-us/microsoft-365/compliance/gdpr-dsr-azure#step-5-delete)
- System-generated logs for Microsoft services operated by 21Vianet can be exported by Tenant Administrators using the Data Log Export. For more information, see [Azure Data Subject Requests - Export](https://learn.microsoft.com/en-us/microsoft-365/compliance/gdpr-dsr-azure#step-6-export).

## Next steps

[Learn more about Intune supported configurations](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms)
