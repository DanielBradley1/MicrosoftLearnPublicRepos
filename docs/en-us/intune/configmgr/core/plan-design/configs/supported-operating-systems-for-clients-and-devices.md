<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices -->
<!-- Sitemap-Last-Modified: 2026-05-27 -->

# Supported OS versions for clients and devices for Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Configuration Manager supports installing client software on Windows computers.

## General requirements and limitations

Review the following requirements and limitations for all clients:

- Changing the startup type or **Log on as** settings for any Configuration Manager service isn't supported. This change can prevent key services from running correctly.

## Windows computers

To manage the following Windows OS versions, use the client that's included with Configuration Manager. For more information, see [How to deploy clients to Windows computers](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-windows-computers).

### Supported client OS versions

- **Windows 11** \(*starting in Configuration Manager version 2107*\)

  Note

  You can continue to use Microsoft Endpoint Manager to manage devices running Windows 11 the same as with Windows 10. For more information, including some known issues, see [Support for Windows 11](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-11).
- **Windows 10**

  For more information, see [Support for Windows 10](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-10).

For more information on the versions of the Windows Assessment and Deployment Kit \(Windows ADK\) that Configuration Manager current branch supports, see [Support for the Windows ADK](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-adk).

#### Azure Virtual Desktop

[Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/) is a desktop and app virtualization service that runs on Microsoft Azure. You can use Configuration Manager to manage these virtual devices running Windows in Azure.

Similar to a terminal server, some of these virtual devices allow multiple concurrent active user sessions. To help with client performance, Configuration Manager disables user policies on any device that allows these multiple user sessions. Even if you enable user policies, the client disables them by default on these devices, which include Windows Enterprise multi-session and terminal servers.

The client only disables user policy when it detects this type of device during a new installation. For an existing client of this type that you update to this version, the previous behavior persists. On an existing device, it configures the user policy setting even if it detects that the device allows multiple user sessions.

If you require user policy in this scenario, and accept any potential performance impact, use [client settings](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-settings) to enable user policy. In the **Client Policy** group, configure the following setting: **Enable user policy for multiple user sessions**.

Starting in version 2006, the **Windows 10 Enterprise multi-session** platform is available in the list of supported OS versions on objects with requirement rules or applicability lists. Starting in version 2107, the **Windows 11 Enterprise multi-session** platform is available.

Note

If you previously selected the top-level platform, this action automatically selected all child platforms. New platforms aren't automatically selected. For example, if you want to add **Windows 10 Enterprise multi-session**, manually select it under the **Windows 10** platform.

For more information, see the following articles:

- [Support for virtualization environments](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-virtualization-environments)
- [Manage Configuration Manager clients in a virtual desktop infrastructure \(VDI\)](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/considerations-for-managing-clients-in-a-vdi)

### Supported server OS versions

- **Windows Server 2025**: IoT, Standard, Datacenter, Datacenter: Azure Edition \(*starting in Configuration Manager version 2409*\)
- **Windows Server 2022**: IoT, Standard, Datacenter, Datacenter: Azure Edition \(*starting in Configuration Manager version 2107*\)

  - *Windows Server IoT 2022 for Storage* is not supported

- **Windows Server 2019**: IoT, Standard, Datacenter

  - *Windows Server IoT 2019 for Storage* is not supported

- **Windows Server 2016**: Standard, Datacenter
- **Windows Storage Server 2016**: Workgroup, Standard, IoT
- **Windows Server 2012 R2** \(x64\): Standard, Datacenter <sup>[Extended Security Updates](#bkmk_ESU)</sup>
- **Windows Storage Server 2012 R2** \(x64\) <sup>[Extended Security Updates](#bkmk_ESU)</sup>
- **Windows Server 2012** \(x64\): Standard, Datacenter <sup>[Extended Security Updates](#bkmk_ESU)</sup>
- **Windows Storage Server 2012** \(x64\) <sup>[Extended Security Updates](#bkmk_ESU)</sup>

#### Server Core

The following versions specifically refer to the Server Core installation of the OS. <sup>[Note 2](#bkmk_note2)</sup>

Windows Server semi-annual channel versions are Server Core installations, such as Windows Server, version 1809. As a Configuration Manager client, they're supported the same as the associated Windows 11 or Windows 10 semi-annual channel version. For more information, see [Support for Windows 11](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-11) or [Support for Windows 10](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-10).

- **Windows Server 2025** \(x64\) <sup>[Note 1](#bkmk_note1)</sup> \(*starting in version 2409*\)
- **Windows Server 2022** \(x64\) <sup>[Note 1](#bkmk_note1)</sup> \(*starting in version 2107*\)
- **Windows Server 2019** \(x64\) <sup>[Note 1](#bkmk_note1)</sup>
- **Windows Server 2016** \(x64\) <sup>[Note 1](#bkmk_note1)</sup>
- **Windows Server 2012 R2** \(x64\) <sup>[Note 1](#bkmk_note1)</sup> <sup>[Extended Security Updates](#bkmk_ESU)</sup>
- **Windows Server 2012** \(x64\) <sup>[Note 1](#bkmk_note1)</sup> <sup>[Extended Security Updates](#bkmk_ESU)</sup>

#### Note 1

To support [client push installation](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/client-installation-methods#client-push-installation), add the File Server service of the File and Storage Services server role. For more information about installing Windows features on Server Core, see [Install roles, role services, and features by using Windows PowerShell cmdlets](https://learn.microsoft.com/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-windows-powershell-cmdlets).

#### Note 2

The Software Center app isn't supported on any version of Windows Server Core.

## Windows Embedded computers

Manage Windows Embedded devices by installing the Configuration Manager client on the device. For more information, see [Planning for client deployment to Windows Embedded devices](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices).

### Requirements and limitations

- All client features are supported on Windows Embedded systems that don't have write filters enabled.
- Clients that use one of the following are supported for all features except power management:

  - Enhanced Write Filters \(EWF\)
  - RAM File-Based Write Filters \(FBWF\)
  - Unified Write Filters \(UWF\)

### Supported OS versions

- **Windows 11 Enterprise**
- **Windows 11 IoT Enterprise** <sup>[Note 4](#bkmk_note4)</sup>
- **Windows 10 Enterprise** \(x86, x64\)
- **Windows 10 IoT Enterprise** \(x86, x64\) <sup>[Note 4](#bkmk_note4)</sup>

#### Note 4: Windows IoT Enterprise

This version includes the long-term servicing channel \(LTSC\). For more information, see [Overview of Windows 10 IoT Enterprise](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/getting_started).

## Extended Security Updates and Configuration Manager

The [Extended Security Updates \(ESU\)](https://learn.microsoft.com/en-us/lifecycle/faq/extended-security-updates) program is a last resort option for customers who need to run certain legacy Microsoft products past the end of support. For example, Windows 10. It includes Critical and/or Important security updates \(as defined by the [Microsoft Security Response Center \(MSRC\)](https://www.microsoft.com/msrc)\) for a maximum of three years after the product's End of Extended Support date.

Products that are beyond their support lifecycle aren't supported for use with Configuration Manager. This includes any products that are covered under the ESU program. Security updates released under the ESU program will be published to Windows Server Update Services \(WSUS\). These updates will appear in the Configuration Manager console. While ESU-covered products are not supported operating systems in Configuration Manager<sup>[1](#clarification1)</sup>, any [supported version of Configuration Manager current branch](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates#version-details) can be used to deploy and install ESU security updates for **Windows Server 2012, Windows Server 2012 R2**, and **Windows 10**<sup>[2](#clarification2)</sup>. For details on supported Windows 10 editions under the ESU program, see the [Extended Security Updates FAQ](https://learn.microsoft.com/en-us/lifecycle/faq/extended-security-updates). No further support is offered for computers running Windows 7 or Windows Server 2008/ 2008 R2, including customers with an additional further year of ESU support as noted in [KB4522133](https://support.microsoft.com/en-us/topic/kb4522133-procedure-to-continue-receiving-security-updates-after-extended-support-ended-on-january-10-2023-48c59204-fe67-3f42-84fc-c3c3145ff28e)

Client management features not related to Windows software update management or OS deployment will no longer be tested on the operating systems covered under the ESU program and we don't guarantee that they'll continue to function. It's highly recommended to upgrade or migrate to a current version of the operating systems as soon as possible to receive client management support.

Important

**1.** "Not Supported" means these operating systems are not considered supported platforms for all general features of Configuration Manager.

The only supported scenarios are:

- Deployment of ESU security updates.
- For ESU-enabled Windows 10 devices, upgrade to Windows 11 via a Windows 11 Feature Update.
- For any Windows 10 device, upgrade to Windows 11 via Microsoft Configuration Manager Operating System Deployment \(OSD\).

**2.** If ConfigMgr product fixes are required for ESU functionality, they will only be made available in the latest released version of Configuration Manager current branch and will not be backported to earlier supported versions.

Tip

Starting in Configuration Manager 2010, you'll be notified in-console about devices with operating systems that are past the end of support date and that are no longer eligible to receive security updates. For more information, see [Console notifications](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console-notifications#bkmk_2010). This information is provided for your convenience and only for use internally within your company. You should not solely rely on this information to confirm update or license compliance. Be sure to verify the accuracy of the information provided to you.

## Mac computers

Important

Starting in January 2022, this feature of Configuration Manager is [deprecated](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). The macOS client installation package isn't available for new deployments, but existing deployments are supported until December 31, 2022.

Migrate management of macOS devices to Microsoft Intune:

1. First, uninstall the Configuration Manager client for macOS. For more information, see [Uninstalling the Mac client](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/maintain-mac-clients#uninstalling-the-mac-client).
2. Then enroll the device to Intune. For more information, see [Deployment guide: Manage macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-macos).

Manage Apple Mac computers with the Configuration Manager client for macOS.

For more information, see [How to deploy clients to Macs](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-macs).

### Requirements and limitations for macOS

- Installing or running the Configuration Manager client for macOS on computers under an account other than root isn't supported. Doing so can prevent key services from running correctly.

### Supported versions

- **macOS Big Sur \(11\)** \(requires Configuration Manager client for macOS version 5.0.9000.1002 or later\)
- **macOS Catalina \(10.15\)** \(requires Configuration Manager client for macOS version 5.0.8742.1000 or later\)
- **macOS Mojave \(10.14\)**

## On-premises MDM

Important

Starting in November 2021, this feature of Configuration Manager is [deprecated](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

Configuration Manager has built-in capabilities for managing mobile devices that are on-premises without installing client software. For more information, see [Manage mobile devices with on-premises infrastructure](https://learn.microsoft.com/en-us/intune/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure).

### Supported operating systems

- **Windows 10 Pro** \(x86, x64\)
- **Windows 10 Enterprise** \(x86, x64\)
- **Windows 10 IoT Enterprise** \(x86, x64\) This version includes the long-term servicing channel \(LTSC\). For more information, see [Overview of Windows 10 IoT Enterprise](https://learn.microsoft.com/en-us/windows/iot-core/windows-iot-enterprise).
- **Windows 10 Team for Surface Hub**

## Exchange Server connector

Configuration Manager supports limited management of devices that connect to your Exchange Server, without installing the Configuration Manager client. For more information, see [Manage mobile devices with Configuration Manager and Exchange](https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync).

### Supported versions of Exchange Server

- **Exchange Online \(Microsoft 365\)**: This version includes Business Productivity Online Standard Suite
- **Exchange Server 2016**
- **Exchange Server 2013**
- **Exchange Server 2010 SP1** or **Exchange Server 2010 SP2**
