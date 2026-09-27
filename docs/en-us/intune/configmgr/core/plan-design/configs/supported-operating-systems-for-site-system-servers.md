<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers -->
<!-- Sitemap-Last-Modified: 2024-12-19 -->

# Supported operating systems for Configuration Manager site system servers

*Applies to: Configuration Manager \(current branch\)*

This article details the Windows versions that you can use to host a Configuration Manager site or site system role.

## Windows Server 2025

*Applies to Datacenter: Azure Edition, Standard and Datacenter editions*

Site servers:

- Central administration site
- Primary site
- Secondary site

Site system servers:

- Certificate registration point
- Cloud management gateway connection point
- Data warehouse service point
- Distribution point <sup>[Note 1](#bkmk_note1)</sup>
- Endpoint Protection point
- Fallback status point
- Management point
- Reporting services point
- Service connection point
- Site database server <sup>[Note 2](#bkmk_note2)</sup>
- SMS Provider
- Software update point
- State migration point

## Windows Server 2022

*Applies to Datacenter: Azure Edition, Standard and Datacenter editions*

Site servers:

- Central administration site
- Primary site
- Secondary site

Site system servers:

- Asset Intelligence synchronization point
- Certificate registration point
- Cloud management gateway connection point
- Data warehouse service point
- Distribution point <sup>[Note 1](#bkmk_note1)</sup>
- Endpoint Protection point
- Enrollment point
- Enrollment proxy point
- Fallback status point
- Management point
- Reporting services point
- Service connection point
- Site database server <sup>[Note 2](#bkmk_note2)</sup>
- SMS Provider
- Software update point
- State migration point

## Windows Server 2019

*Applies to Standard and Datacenter editions*

Site servers:

- Central administration site
- Primary site
- Secondary site

Site system servers:

- Asset Intelligence synchronization point
- Certificate registration point
- Cloud management gateway connection point
- Data warehouse service point
- Distribution point <sup>[Note 1](#bkmk_note1)</sup>
- Endpoint Protection point
- Enrollment point
- Enrollment proxy point
- Fallback status point
- Management point
- Reporting services point
- Service connection point
- Site database server <sup>[Note 2](#bkmk_note2)</sup>
- SMS Provider
- Software update point
- State migration point

## Windows Server 2016

*Applies to Standard and Datacenter editions*

Site servers:

- Central administration site
- Primary site
- Secondary site

Site system servers:

- Asset Intelligence synchronization point
- Certificate registration point
- Cloud management gateway connection point
- Data warehouse service point
- Distribution point <sup>[Note 1](#bkmk_note1)</sup>
- Endpoint Protection point
- Enrollment point
- Enrollment proxy point
- Fallback status point
- Management point
- Reporting services point
- Service connection point
- Site database server <sup>[Note 2](#bkmk_note2)</sup>
- SMS Provider
- Software update point
- State migration point

## Windows Storage Server 2016

Site system server:

- Distribution point <sup>[Note 1](#bkmk_note1)</sup>

## Windows Server 2012/2012 R2

*Applies to Standard and Datacenter*

On October 10th, 2023, Windows Server 2012 and Windows Server 2012 R2 entered the Extended Support Updates phase. Microsoft will no longer provide support for Configuration Manager site servers or roles installed to these Operating Systems. For more information, see [Extended Security Updates and Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_ESU).

Tip

Starting in Configuration Manager 2309, you'll be notified when performing a site upgrade about site systems with operating systems that are past the end of support date.

Starting in Configuration Manager 2403 you'll be blocked from performing a site upgrade if any site systems are detected with operating systems that are past the end of support date. For more information, see [Extended Security Updates and Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_ESU).

## Client OS versions

The following client OS versions are supported for use as a **distribution point** <sup>[Note 1](#bkmk_note1)</sup>:

- Windows 11

  For more information on supported build versions and editions, see [Support for Windows 11](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-11).
- Windows 10 \(x86, x64\)

  For more information on supported build versions and editions, see [Support for Windows 10](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-10).

This support has the following limitation:

- Distribution points on this OS don't support PXE or multicast with the default Windows Deployment Services. You can PXE-enable a distribution point on this OS with the option to **Enable a PXE responder without Windows Deployment Service**. For more information, see [Install and configure distribution points](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe).

## Server core installations

The server core installation of the following server OS versions is supported for use as a **distribution point**:

- Windows Server 2025
- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1809
- Windows Server, version 1803
- Windows Server, version 1709
- Windows Server 2016

This support has the following limitation:

- Distribution points on this OS don't support PXE or multicast with the default Windows Deployment Services. You can PXE-enable a distribution point on this OS with the option to **Enable a PXE responder without Windows Deployment Service**. For more information, see [Install and configure distribution points](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe).

## General notes

### Extended Security Updates for Windows Server 2012 and Windows Server 2012 R2

On October 10th, 2023, Windows Server 2012 and Windows Server 2012 R2 will enter the Extended Support Updates phase. Microsoft will no longer provide support for Configuration Manager site servers or roles installed to these Operating Systems. For more information, see [Extended Security Updates and Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_ESU).

### Note 1: Distribution points

Distribution points support several different configurations that each have different requirements. In some cases, these configurations support installation not only on servers, but on client operating systems. For more information, see [Manage content and content infrastructure](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/manage-content-and-content-infrastructure).

### Note 2: Site database servers

Site database servers aren't supported on a read-only domain controller \(RODC\). For more information, see [SQL Server security considerations: Installing SQL Server on a domain controller](https://learn.microsoft.com/en-us/sql/sql-server/install/security-considerations-for-a-sql-server-installation#Install_DC).

Additionally, secondary site servers aren't supported on any domain controller.

## Next steps

[Supported SQL Server versions](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-sql-server-versions)

See also:

- [Recommended hardware](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/recommended-hardware)
- [Site and site system prerequisites](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/site-and-site-system-prerequisites)
- [Size and scale numbers](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/size-and-scale-numbers)
