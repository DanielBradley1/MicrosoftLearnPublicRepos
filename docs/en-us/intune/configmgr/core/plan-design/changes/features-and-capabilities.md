<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/features-and-capabilities -->
<!-- Sitemap-Last-Modified: 2024-07-17 -->

# Features and capabilities of Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

This article summarizes the primary management features of Configuration Manager. Each feature has its own prerequisites, and how you use each might influence the design and implementation of your Configuration Manager hierarchy. For example, if you want to deploy software updates to devices in your hierarchy, you need a software update point site system role.

## Co-management

Co-management is one of the primary ways to attach your existing Configuration Manager deployment to the Microsoft 365 cloud. It enables you to concurrently manage Windows devices by using both Configuration Manager and Microsoft Intune. Co-management lets you cloud-attach your existing investment in Configuration Manager by adding new functionality like Conditional Access. For more information, see [What is co-management](https://learn.microsoft.com/en-us/intune/configmgr/comanage/overview)?

## Cloud-attached management

Use features like the cloud management gateway and Microsoft Entra ID to manage internet-based clients.

For more information, see the following articles:

- [Cloud management gateway overview](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/overview)
- [Plan for Microsoft Entra ID](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/plan-for-security#azure-active-directory)
- [Azure services](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/azure-services-wizard)

## Real-time management

Use CMPivot to immediately query online devices, then filter and group the data for deeper insights. Also use the Configuration Manager console to manage and deploy Windows PowerShell scripts to clients. For more information, see [CMPivot](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/cmpivot) and [Create and run PowerShell scripts](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/create-deploy-scripts).

## Application management

Helps you create, manage, deploy, and monitor applications to a range of different devices that you manage. Deploy, update, and manage Microsoft 365 Apps from the Configuration Manager console. Additionally, Configuration Manager integrates with the Microsoft Store for Business and Education to deliver cloud-based apps. For more information, see [Introduction to application management](https://learn.microsoft.com/en-us/previous-versions/troubleshoot/configmgr/introduction-to-application-management).

## OS deployment

Deploy an in-place upgrade of Windows, or capture and deploy OS images. Image deployment can use PXE, multicast, or bootable media. It can also help redeploy existing devices using Windows Autopilot. For more information, see [Introduction to OS deployment](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/introduction-to-operating-system-deployment).

## Software updates

Manage, deploy, and monitor software updates in the organization. Integrate with Windows Delivery Optimization and other peer caching technologies to help control network usage. For more information, see [Introduction to software updates](https://learn.microsoft.com/en-us/intune/configmgr/sum/understand/software-updates-introduction).

## Company resource access

Lets you give users in your organization access to data and applications from remote locations. This feature includes Wi-Fi, VPN, email, and certificate profiles. For more information, see [Protect data and site infrastructure](https://learn.microsoft.com/en-us/intune/configmgr/protect/understand/protect-data-and-site-infrastructure).

## Compliance settings

Helps you to assess, track, and remediate the configuration compliance of client devices in the organization. Additionally, you can use compliance settings to configure a range of features and security settings on devices you manage. For more information, see [Ensure device compliance](https://learn.microsoft.com/en-us/intune/configmgr/compliance/understand/ensure-device-compliance).

## Endpoint Protection

Provides security, antimalware, and Windows Firewall management for computers in your organization. This area includes management and integration with the following Windows Defender suite features:

- Windows Defender Antivirus
- Microsoft Defender for Endpoint
- Windows Defender Exploit Guard
- Windows Defender Application Guard
- Windows Defender Application Control
- Windows Defender Firewall

For more information, see [Endpoint Protection](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection).

## Inventory

Helps you identify and monitor assets.

### Hardware inventory

Collects detailed information about the hardware of devices in your organization. For more information, see [Introduction to hardware inventory](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/introduction-to-hardware-inventory).

### Software inventory

Collects and reports information about the files that are stored on client computers in your organization. For more information, see [Introduction to software inventory](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/inventory/introduction-to-software-inventory).

### Asset Intelligence

Provides tools to collect inventory data and monitor software license usage in your organization. For more information, see [Introduction to Asset Intelligence](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence).

## On-premises mobile device management

Enrolls and manages devices by using the on-premises Configuration Manager infrastructure with the management functionality built into the device platforms. \(Typical management uses a separately installed Configuration Manager client.\) This feature currently supports managing Windows 10 Enterprise and Windows 10 Mobile devices. For more information, see [Manage mobile devices with on-premises infrastructure](https://learn.microsoft.com/en-us/intune/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure).

## Power management

Manage and monitor the power consumption of client computers in the organization. Configure power plans, and use Wake-on-LAN to do maintenance outside of business hours. For more information, see [Introduction to power management](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/introduction-to-power-management).

## Remote control

Provides tools to remotely administer client computers from the Configuration Manager console. For more information, see [Introduction to remote control](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/introduction-to-remote-control).

## Reporting

Use the advanced reporting capabilities of SQL Server Reporting Services from the Configuration Manager console. This feature provides hundreds of default reports. For more information, see [Introduction to reporting](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/introduction-to-reporting).

## Software metering

Monitor and collect software usage data from Configuration Manager clients. You can use this data to determine whether software is used after it's installed. For more information, see [Monitor app usage with software metering](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/monitor-app-usage-with-software-metering).

## Next steps

For more information about how to plan and install Configuration Manager to support these management capabilities in your environment, see [Get ready for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/get-ready).
