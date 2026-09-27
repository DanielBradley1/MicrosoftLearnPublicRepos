<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Removed and deprecated features for Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

This article lists the features that are deprecated or removed from support for Configuration Manager. Deprecated features will be removed in a future update. These future changes might affect your use of Configuration Manager.

This information is subject to change with future releases. It might not include each deprecated Configuration Manager feature.

## Deprecated features

The following features are deprecated. You can still use them now, but Microsoft plans to end support in the future.

| Feature | Deprecation first announced | Planned end of support |
| --- | --- | --- |
| **Microsoft Connected Cache \(MCC\)** integration in Configuration Manager will be deprecated in a future release of Configuration Manager. After deprecation, no further feature development or updates will be provided for Microsoft Connected Cache within Configuration Manager. Customers should begin transitioning to the standalone version of Microsoft Connected Cache to continue receiving ongoing improvements and support. For more information, see [Microsoft Connected Cache](https://learn.microsoft.com/en-us/windows/deployment/do/waas-microsoft-connected-cache). | June 2026 | TBD |
| The **MDT Integration with CM and Standalone** is no longer supported with Configuration Manager. Customers should remove MDT TS steps, followed by removing MDT integration, to avoid TS corruption and modification failures. More information on the MDT retirement [here](https://learn.microsoft.com/en-us/troubleshoot/mem/configmgr/mdt/mdt-retirement). | Dec 2024 | The first release after Oct 10, 2025 |
| **Office 365 Client Management dashboard add-in support statement**. For more information, see [Office 365 Client Management dashboard](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/office-365-dashboard). | April 2024 | The first release after April 1, 2025 |
| Windows Information Protection | July 2022 | TBD |
| The site system roles for on-premises MDM and macOS clients: **enrollment proxy point and enrollment point**. | January 2022 | Mar 31, 2024 |
| The **Microsoft Store for Business and Education**. For more information, see [Manage apps from the Microsoft Store for Business and Education with Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/manage-apps-from-the-windows-store-for-business). | November 2021 | The first release after March 1, 2023 |
| **Asset intelligence**. For more information, see [Asset intelligence deprecation](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/deprecation). | November 2021 | The first release after November 1, 2022 |
| **On-premises MDM**. For more information, see [On-premises MDM in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure). | November 2021 | The first release after November 1, 2022 |
| Azure Active Directory \(Azure AD\) Graph API and Azure AD Authentication Library \(ADAL\), which is used by Configuration Manager for some cloud-attached scenarios. If you use cloud-attached features such as co-management, tenant attach, or Microsoft Entra discovery, starting June 30, 2022, these features may not work correctly in Configuration Manager version 2107 or earlier. Stay current with Configuration Manager to make sure these features continue to work. For more information, see [CMG FAQ](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/cloud-management-gateway-faq#do-i-need-to-do-anything-with-the-deprecation-of-the-azure-ad-graph-api-and-azure-ad-authentication-library--adal--). | July 2021 | June 30, 2022 |
| The BitLocker management implementation for the [recovery service](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/recovery-service) has changed. The legacy MBAM-based service is replaced by the messaging processing engine on the management point. | March 2021 | The first release after Mar 2025 |
| Older style of console extensions that haven't been approved in the **Console Extension** node, will no longer be supported. For more information about new console extensions, see [Manage console extensions](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console-extensions). | April 2021 | TBD<sup>[Note 1](#bkmk_note1)</sup> |
| The implementation for sharing content from Azure has changed. Use a content-enabled cloud management gateway. Starting in version 2107, you can't create a traditional cloud distribution point. | February 2019 | The first release after October 5, 2022 |
| Cloud management gateway and cloud distribution point deployments with Azure Service Manager using a management certificate. For more information, see [Plan for CMG](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager). | November 2018 | The first release after October 5, 2022 |

### Note 1: Support removed TBD

The specific timeframe is to be determined \(TBD\). Microsoft recommends that you change to the new process or feature, but you can continue to use the deprecated process or feature for the near future.

## Unsupported and removed features

The following features are no longer supported. In some cases, they're no longer in the product.

| Feature | Deprecation first announced | Support removed |
| --- | --- | --- |
| [System Center Update Publisher \(SCUP\) and integration with ConfigMgr](https://learn.microsoft.com/en-us/intune/configmgr/sum/tools/updates-publisher) | October 2023 | Jan 31, 2024 |
| Sites that allow HTTP client communication. Configure the site for HTTPS or Enhanced HTTP. For more information, see [Enable the site for HTTPS-only or enhanced HTTP](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/list-of-prerequisite-checks#enable-site-system-roles-for-https-or-enhanced-http). | March 2021 | The first release after April 1, 2024 |
| Upgrade from any version of System Center 2012 Configuration Manager to current branch. For more information, see [Upgrade to Configuration Manager current branch](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/upgrade-to-configuration-manager) | April 2022 | Version 2303 |
| The Configuration Manager client for **macOS** and Mac client management. For more information, see [Supported clients: Mac computers](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#mac-computers). Migrate management of macOS devices to Microsoft Intune. For more information, see [Deployment guide: Manage macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-macos). | January 2022 | December 31, 2022 |
| [Community hub service and integration with ConfigMgr](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/community-hub) | October 2022 | The first release after March 1, 2023 |
| The geographical view in the **Site Hierarchy** node of the **Monitoring** workspace in the Configuration Manager console. | August 2020 | The first release after September 2023 |
| **Desktop Analytics**. For more information, see [Windows compatibility reports in Intune](https://go.microsoft.com/fwlink/?linkid=2212414). | November 2021 | November 30, 2022 |
| The ability to deploy a cloud management gateway \(CMG\) as a **cloud service \(classic\)**. All CMG deployments should use a [virtual machine scale set](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets). | September 2021 | Version 2203 |
| Cloud management gateway \(CMG\) as a **cloud service \(classic\)**. All CMG deployments should use a [virtual machine scale set](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets). |  | Version 2403 |
| The following compliance settings for **Company resource access**:  [Certificate profiles](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/introduction-to-certificate-profiles), [VPN profiles](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/vpn-profiles), [Wi-Fi profiles](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-wifi-profiles), [Windows Hello for Business settings](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/windows-hello-for-business-settings), and email profiles. This deprecation includes the [co-management resource access workload](https://learn.microsoft.com/en-us/intune/configmgr/comanage/workloads#resource-access-policies). Use Microsoft Intune to [deploy resource access profiles](https://learn.microsoft.com/en-us/intune/device-configuration/overview). For more information, see [Frequently asked questions about resource access deprecation](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/resource-access-deprecation-faq). | March 2021 | Version 2203 |
| Desktop Analytics data for Windows 7, Windows 8, and earlier versions of Windows 10 that don't support the [Windows diagnostic data processor configuration](https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-compatibility). | July 2021 | January 31, 2022 |
| Third-party add-ons that use Microsoft .NET Framework version 4.6.1 or earlier, and rely on Configuration Manager libraries. Such add-ons need to use .NET 4.6.2 or later. For more information, see [External dependencies require .NET 4.6.2](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2109#bkmk_dotnetsdk). | September 2021 | Version 2111 |
| [Log Analytics connector for Azure Monitor.](https://learn.microsoft.com/en-us/azure/azure-monitor/platform/collect-sccm?context=%2fmem%2fconfigmgr%2fcore%2fcontext%2fcore-context) This feature is called the *OMS Connector* in the Azure Services node. | November 2020 | Version 2107 |
| Microsoft Edge legacy [browser profiles](https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/browser-profiles). For more information, see [New Microsoft Edge to replace Microsoft Edge Legacy with April's Windows 10 Update Tuesday release](https://techcommunity.microsoft.com/t5/microsoft-365-blog/new-microsoft-edge-to-replace-microsoft-edge-legacy-with-april-s/ba-p/2114224) | March 2021 | April 2021 |
| The [collection evaluation viewer](https://learn.microsoft.com/en-us/intune/configmgr/core/support/ceviewer), which was integrated in version 2010. | November 2020 | Version 2103 |
| Desktop Analytics tile and page for **Security Updates** | December 2020 | March 2021 |
| Desktop Analytics option to **View recent data** for device enrollment and security updates. For more information, see [Data latency](https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-compatibility). | May 2020 | July 2020 |
| Windows Analytics and Upgrade Readiness integration. For more information, see [KB 4521815: Windows Analytics retirement on January 31, 2020](https://support.microsoft.com/help/4521815/windows-analytics-retirement). | October 14, 2019 | January 31, 2020 |
| Device health attestation assessment for Conditional Access compliance policies  For more information, see [What happened to hybrid MDM](https://learn.microsoft.com/en-us/intune/configmgr/mdm/understand/what-happened-to-hybrid). | July 3, 2019 | Version 1910 |
| The Configuration Manager Company Portal app | May 21, 2019 | Version 1910 |
| The application catalog, including both site system roles: the application catalog website point and web service point. For more information, see [Remove the application catalog](https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/plan-for-and-configure-application-management#remove-the-application-catalog). | May 21, 2019 | Version 1910 |
| Certificate-based authentication with Windows Hello for Business settings in Configuration Manager  <br>For more information, see [Windows Hello for Business settings](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/windows-hello-for-business-settings). | December 2017 | Version 1910 |
| System Center Endpoint Protection for Mac and Linux  <br>For more information, see [End of support blog post](https://techcommunity.microsoft.com/t5/configuration-manager-blog/end-of-support-for-scep-for-mac-and-scep-for-linux-on-december/ba-p/286257). | October 2018 | December 31, 2018 |
| On-premises Conditional Access  <br>For more information, see [What happened to hybrid MDM](https://learn.microsoft.com/en-us/intune/configmgr/mdm/understand/what-happened-to-hybrid). | January 30, 2019 | September 1, 2019 |
| Hybrid mobile device management \(MDM\)  <br>For more information, see [What happened to hybrid MDM](https://learn.microsoft.com/en-us/intune/configmgr/mdm/understand/what-happened-to-hybrid).  <br>  <br>Starting with the 1902 Intune service release, expected at the end of February 2019, new customers can't create a new hybrid connection. | August 14, 2018 | September 1, 2019 |
| Security Content Automation Protocol \(SCAP\) extensions.  <br> | September 2018 | Version 1810 |
| The **Silverlight user experience** for the application catalog website point is no longer supported. Users should use the new Software Center. For more information, see [Configure Software Center](https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/plan-for-software-center#configure-software-center). | August 11, 2017 | Version 1806 |
| The previous version of Software Center.  <br>  <br>For more information about the new Software Center, see [Plan for and configure application management](https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/plan-for-software-center). | December 13, 2016 | Version 1802 |
| Management of Virtual Hard Disks \(VHDs\) with Configuration Manager.  <br>  <br>This deprecation includes removal of options to create a new VHD or manage a VHD using a task sequence, and the removal of the Virtual Hard Disks node from the Configuration Manager console.  <br>  <br>Existing VHDs are not deleted, but are no longer accessible from within the Configuration Manager console. | January 6, 2017 | Version 1710 |
| Task sequences:  <br>- Convert Disk to Dynamic  <br>- Install Deployment Tools | November 18, 2016 | Version 1710 |
| Upgrade Assessment Tool  <br>  <br>The Upgrade Assessment Tool depends on both Configuration Manager and the Application Compatibility Toolkit \(ACT\) 6.x. The final version of ACT was shipped in the Windows 10 v1511 ADK. As there are no further updates to ACT, support for the Upgrade Assessment Tool is discontinued. Deprecation notice was added to the [download page for UAT](https://www.microsoft.com/software-download/windows10) on September 12, 2016. | September 12, 2016 | July 11, 2017 |
| Software update points with a network load balancing \(NLB\) cluster | February 27, 2016 | Version 1702 |
| Task sequences:  <br>- OSDPreserveDriveLetter  <br>  <br>During an operating system deployment, by default, Windows Setup now determines the best drive letter to use \(typically C:\). If you want to specify a different drive to use, you can change the location in the Apply Operating System task sequence step. Go to the **Select the location where you want to apply this operating system** setting. Select **Specific logical drive letter** and choose the drive that you want to use. | June 20, 2016 | Version 1606 |
| [Network Access Protection](#network-access-protection) \(NAP\) - as found in System Center 2012 Configuration Manager | July 10, 2015 | Version 1511 |
| [Out of Band Management](#out-of-band-management) - as found in System Center 2012 Configuration Manager | October 16, 2015 | Version 1511 |
| System Center Configuration Manager Management Pack - for System Center Operations Manager is not available for download | October 16, 2015 | Version 1511 |

### WINS

Windows Internet Name Service \(WINS\) is a legacy computer name registration and resolution service. It's a deprecated service. You should replace WINS with Domain Name System \(DNS\). For more information, see [Windows Internet Name Service \(WINS\)](https://learn.microsoft.com/en-us/windows-server/networking/technologies/wins/wins-top).

### Out of Band Management

With Configuration Manager, native support for AMT-based computers from within the Configuration Manager console has been removed.

- AMT-based computers remain fully managed when you use the [Intel SCS Add-on for Configuration Manager](https://www.intel.com/content/www/us/en/software/setup-configuration-software.html). The add-on provides you access to the latest capabilities to manage AMT, while removing limitations introduced until Configuration Manager could incorporate those changes.
- Out of Band Management in System Center 2012 Configuration Manager is not affected by this change.

### Network Access Protection

Configuration Manager has removed support for Network Access Protection. The feature has been deprecated in Windows Server 2012 R2, and is removed from Windows 10.

For network access protection alternatives, see the *Deprecated functionality* section of [Network Policy and Access Services Overview](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831683\(v=ws.11\)).

## See also

- [Removed and deprecated](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated)
- [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle)
- [Support for current branch versions of Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/current-branch-versions-supported)
