<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/government-service -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Microsoft Intune for US Government GCC High and DoD service description

Note

This article applies to Microsoft Intune features only. If you're looking for information on other features, then go to that specific documentation. For example, for Microsoft Teams devices, see [Teams Rooms on Windows and Android](https://learn.microsoft.com/en-us/microsoftteams/rooms/teams-devices-feature-comparison).

The Intune U.S. government service description is as an overview of the service offering in the Government Community Cloud \(GCC\) High and U.S. Department of Defense \(DoD\) environments.

This article lists the feature differences compared to the commercial offering of [Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/what-is-intune). To learn more about Intune for GCC customers, see [EMS offers for US Government and Microsoft 365 interoperability](https://learn.microsoft.com/en-us/enterprise-mobility-security/solutions/ems-govt-service-description#ems-offers-for-us-government-and-microsoft-365-interoperability).

## Intune commercial and government instances

The Intune GCC High and DoD offerings are built on the Microsoft Azure Government Cloud. This cloud is designed to interoperate with Microsoft 365 GCC High and DoD environments.

Intune has two service instances:

- **Commercial service**: The commercial service is available to anyone with an Intune license and is used by most Intune customers.
- **Government cloud**: This service is also known as **GCC High** or **DoD**. This instance is a datacenter that's physically separate from the commercial instances. The datacenter is locked down and is only used by government customers who purchase the appropriate license.

These government instances are also known as **IL4** and **IL5**, where **IL** refers to Impact Level.

- In the government cloud, the Intune service instance is shared with GCC High and DoD tenants. This architecture is slightly different than other services, such as Microsoft 365 and Azure.
- GCC is the same instance as Microsoft Intune in the commercial space. Other services, like Microsoft 365, have a separate GCC instance. Intune doesn't have a separate GCC instance.

  So, when you see **GCC** in this Intune article, it refers to the commercial service. When you see **GCC High** or **DoD**, it refers to the government cloud.

  GCC instances are commonly used by state and local government customers that require extra accreditation for the cloud services they use.

## Enroll in government tenant

![Screenshot that shows the Microsoft government cloud, including GCC High and DoD services, is physically separate from the public cloud and commercial cloud instances.](https://learn.microsoft.com/en-us/intune/fundamentals/media/government-service/migration-public-government-cloud.png)

If your resources are in a commercial tenant and you want to move to the government cloud, the devices need to unenroll from the current tenant, and then re-enroll in the new tenant. There isn't a built-in way to migrate from the commercial service to the government cloud, and vice versa.

This process is similar to unenrolling from another mobile device management \(MDM\) service and enrolling in Intune. For more information, see [Deployment guide: Setup or move to Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/setup-migration#currently-use-a-third-party-mdm-provider).

Administrators can get help locking down their Intune tenants using the Secure Technical Implementation Guide \(STIG\). To get guidance from the `cyber.mil` website, see the [STIGs Document Library](https://public.cyber.mil/stigs/downloads/?_dl_facet_stigs=mdm-emm) \(opens the `public.cyber.mil` website\).

## Compliance and certifications

Intune is Common Criteria certified and is on the National Information Assurance Partnership \(NIAP\) Product Compliance List \(PCL\). To see the certification materials, see [NIAP - Product Details](https://www.niap-ccevs.org/products/11298).

For information on the US Federal Risk and Authorization Management Program \(FedRAMP\) accreditation and Microsoft, see [FedRAMP](https://learn.microsoft.com/en-us/compliance/regulatory/offering-fedramp).

## Supported Intune features in GCC High and DoD

The following features are available and supported in Microsoft GCC High and/or DoD clouds:

| Feature | Availability |
| --- | --- |
| Log Analytics | You can send Intune log data to Azure Storage, Event Hubs, or Log Analytics.  <br>  <br>For more information on this feature, see [Send log data to storage, event hubs, or log analytics from Intune](https://learn.microsoft.com/en-us/intune/governance/integrate-azure-monitor). |
| Microsoft Defender for Endpoint security settings management | On devices onboarded to Defender but not enrolled in Intune, you can use Intune endpoint security policies to manage Defender security settings.  <br>  <br>This support extends to the US Government Community Cloud \(GCC\), US Government Community High \(GCC High\), and Department of Defense \(DoD\) environments.  <br>  <br>For more information on this feature, see [Defender for Endpoint security settings management](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/security-settings-management). |
| Microsoft Intune advanced capabilities | The following Intune advanced capabilities support GCC High and/or DoD. Review the linked documentation for cloud-specific availability:  <br>  <br>- [Advanced Analytics](https://learn.microsoft.com/en-us/intune/advanced-analytics/)  <br>- [Endpoint Privilege Management](https://learn.microsoft.com/en-us/intune/epm/overview)  <br>- [Enterprise Application Management \(EAM\)](https://learn.microsoft.com/en-us/intune/app-management/deployment/enterprise-app-management)  <br>- [Firmware-over-the-air update](https://learn.microsoft.com/en-us/intune/device-updates/android/manage-fota). Samsung Knox E-FOTA integration supports GCC High.  <br>- [Microsoft Tunnel for Mobile Application Management](https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/mam)  <br>- [Specialty devices management](https://learn.microsoft.com/en-us/intune/device-management/specialty-devices)  <br>  <br>The following Intune advanced capabilities support GCC High environments only and aren't supported in DoD:  <br>  <br>- [Cloud PKI](https://learn.microsoft.com/en-us/intune/cloud-pki/)  <br>- [Remote Help](https://learn.microsoft.com/en-us/intune/remote-help/) |
| Mobile Threat Defense \(MTD\) | Mobile Threat Defense \(MTD\) connectors for Android and iOS/iPadOS devices with MTD vendors that **also support** the GCC High environment can be used. When you sign in to a GCC High tenant, you see the connectors that are available in these environments. |
| Platform support | You can use the same operating systems - Android, Android Open Source Project \(AOSP\), iOS/iPadOS, Linux, macOS, and Windows.  <br>  <br>- **Android \(AOSP\)**: There are some device restrictions. For more information, see [Supported operating systems and browsers in Intune - AOSP](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms#android).  <br>- **Linux**: Generally available. |
| Standard MDM features | You can use app policies, device configuration profiles, compliance policies, and more. |
| Windows Autopilot device preparation | Some features are available now, such as user-driven deployments, and some are still [in the planning phase](#intune-features-planned-for-gcc-high-and-dod). For more information about Windows Autopilot solutions, see [Compare Windows Autopilot device preparation and Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/device-preparation/compare).  <br>  <br>To get started with Windows Autopilot device preparation, see [Windows Autopilot Device Preparation overview](https://learn.microsoft.com/en-us/autopilot/device-preparation/overview). |

## Intune features planned for GCC High and DoD

The following features are currently not available and aren't supported in GCC High and DoD clouds. Planning is started to support these features for GCC High and DoD environments. If ETAs are available, then they're listed.

| Feature | Feature documentation |
| --- | --- |
| **Autopatch and updates** | [Windows Autopatch](https://learn.microsoft.com/en-us/windows/deployment/windows-autopatch/overview/windows-autopatch-overview) |
|  | [Feature updates for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-feature-updates) |
|  | [Quality updates for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-quality-updates) |
|  | [Expedite updates for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-expedite-policy) |
|  | [Driver updates for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-driver-update-policy) |
|  | [Delivery Optimization for Win32 Apps](https://learn.microsoft.com/en-us/windows/deployment/do/waas-delivery-optimization) |
| **BIOS and DFCI** | [BIOS configuration profiles for Windows in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-bios-windows) |
|  | [Device Firmware Configuration Interface \(DFCI\) Management](https://learn.microsoft.com/en-us/autopilot/dfci-management) |
| **Security Copilot** | [What is Microsoft Security Copilot?](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot) |
| **Windows Device Health Attestation \(DHA\)** | [Device Health Attestation](https://learn.microsoft.com/en-us/windows-server/security/device-health-attestation) |
| **[Windows Autopilot device preparation](https://learn.microsoft.com/en-us/autopilot/device-preparation/overview)** | Customize out-of-box experience \(OOBE\) and rename devices during provisioning based on organizational structure |
|  | Self-deploying and pre-provisioning mode |
|  | More admin-specified configurations delivered before allowing desktop access |
|  | Enhanced optional desktop onboarding experience inside the Windows Company Portal app |
|  | The ability to associate a device with a tenant. Provisioning modes which require Windows Autopilot registration are not supported. |

## Intune features not available in GCC High and DoD

The following features aren't available and there's currently no planning to support these features for GCC High and DoD environments:

| Feature | Availability |
| --- | --- |
| [App and driver compatibility reports for Windows updates](https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-compatibility) | n/a |
| [Apple Managed account federation](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-apple-federation-customers) | n/a |
| [Chrome Enterprise Connector](https://learn.microsoft.com/en-us/intune/device-enrollment/configure-chrome-enterprise-connector) | n/a |
| [eSIM cellular support on Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-esim-download-server) | n/a |
| [Intune PowerBI connector for DWH](https://learn.microsoft.com/en-us/power-query/connectors/) | n/a |
| [Microsoft Connected Cache for Enterprise and Education](https://learn.microsoft.com/en-us/windows/deployment/do/mcc-ent-edu-overview) | n/a |
| [Microsoft Store for Business](https://learn.microsoft.com/en-us/windows/configuration/store/?tabs=intune) | n/a |
| On-premises Exchange Connector | n/a |
| [Remediations](https://learn.microsoft.com/en-us/intune/device-management/tools/deploy-remediations) | n/a |
| [Reports for feature update policies](https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-feature-updates) | n/a |
| [ServiceNow connector](https://learn.microsoft.com/en-us/intune/device-management/tools/setup-servicenow) | n/a |
| [TeamViewer connector \(legacy\)](https://learn.microsoft.com/en-us/intune/device-management/tools/teamviewer-legacy) and [TeamViewer integration](https://learn.microsoft.com/en-us/intune/device-management/tools/setup-teamviewer) | n/a |
| [Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/overview) | n/a |
| [Windows Backup for Organizations](https://learn.microsoft.com/en-us/windows/configuration/windows-backup/?tabs=intune) | n/a |
| [Windows Diagnostic Data processor configuration](https://learn.microsoft.com/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enable-windows-diagnostic-data-processor-configuration) | n/a |
| [Windows Enterprise multi-session remote desktops \(AVD\)](https://learn.microsoft.com/en-us/intune/solutions/azure-virtual-desktop-multi-session) | n/a |
| [Windows Subscription Activation](https://learn.microsoft.com/en-us/windows/deployment/windows-subscription-activation?pivots=windows-11) | n/a |

## Related content

- [Microsoft Intune planning guide](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide)
- [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
