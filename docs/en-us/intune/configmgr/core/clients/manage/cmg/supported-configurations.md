<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/supported-configurations -->
<!-- Sitemap-Last-Modified: 2023-11-16 -->

# Supported configurations for cloud management gateway

*Applies to: Configuration Manager \(current branch\)*

Use this article as a reference for the features and configurations that are supported by the Configuration Manager cloud management gateway \(CMG\).

## Specifications

- All Windows versions listed in [Supported operating systems for clients and devices](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices) are supported for CMG.
- CMG only supports the management point and software update point roles.
- CMG doesn't support clients that only communicate with IPv6 addresses.
- Software update points using a network load balancer don't work with CMG.
- Starting in version 2203, the option to deploy a CMG as a **cloud service \(classic\)** is removed. All CMG deployments should use a [virtual machine scale set](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets). For more information, see [Removed and deprecated features](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).
- CMG names need to be between 3-24 alphanumeric characters. The name must begin with a letter, end with a letter or digit, and not contain consecutive hyphens.

## Support for Configuration Manager features

The following table lists CMG support for Configuration Manager features:

| Feature | Support |
| --- | --- |
| Software updates | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Endpoint protection | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) <sup>[Note 1](#bkmk_note1)</sup> |
| Hardware and software inventory | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Client status and notifications | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Run scripts | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| CMPivot | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Compliance settings | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Automatic client upgrade | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Client install  <br>\(with [Microsoft Entra integration](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-cmg-azure)\) | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Client install  <br>\(with [token authentication](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-cmg-token)\) | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Software distribution \(device-targeted\) | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Software distribution \(user-targeted, required\)  <br>\(with Microsoft Entra integration\) | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Software distribution \(user-targeted, available\)  <br>\([all requirements](https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/prerequisites-deploy-user-available-apps)\) | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| BitLocker Management | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Pull distribution point source | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Windows [in-place upgrade task sequence](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system) <sup>[Note 2](#bkmk_note2)</sup> | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Task sequence without a boot image, deployed with the option to **Download all content locally before starting task sequence** <sup>[Note 2](#bkmk_note2)</sup> | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Task sequence without a boot image, deployed with [either download option](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/deploy-task-sequence-over-internet#deploy-windows-in-place-upgrade-via-cmg) <sup>[Note 2](#bkmk_note2)</sup> | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Task sequence with a boot image, started from Software Center <sup>[Note 2](#bkmk_note2)</sup> | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Task sequence with a boot image, started from bootable media <sup>[Note 2](#bkmk_note2)</sup> | ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) |
| Any other task sequence scenario <sup>[Note 2](#bkmk_note2)</sup> | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Content for PXE or multicast-enabled deployments | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Client push | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Automatic site assignment | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Software approval requests | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Configuration Manager console | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Remote tools | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) <sup>[Note 3](#bkmk_note3)</sup> |
| Reporting website | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Wake on LAN | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| macOS clients | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Peer cache | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| On-premises MDM | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Alternate content providers | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) <sup>[Note 4](#bkmk_note4)</sup> |
| Content for App-V streaming applications | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| Content for Microsoft 365 Apps updates | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |
| [Prestage content](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/manage-network-bandwidth#BKMK_PrestagingContent) | ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) |

| Key |
| --- |
| ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) = This feature is supported with CMG by all supported versions of Configuration Manager |
| ![Supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/green-check.png) \(*YYMM*\) = This feature is supported with CMG starting with version *YYMM* of Configuration Manager |
| ![Not supported.](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/media/red-x.png) = This feature isn't supported with CMG |

### Support notes

#### Note 1: Support for endpoint protection

Clients that communicate via a CMG can immediately apply endpoint protection policies without an active connection to Active Directory.

#### Note 2: Support for task sequences

For more information about support for deploying a task sequence to a client via the CMG, see [Deploy a task sequence over the internet](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/deploy-task-sequence-over-internet).

#### Note 3: Support for remote tools

As announced at Microsoft Ignite 2021, a public preview of the new remote assistance solution is now available in the Microsoft Intune admin center. This cloud-based tool can help you more securely support users of Windows devices.

For more information, see the following resources:

- [Remote Help: a new remote assistance tool from Microsoft \(blog post\)](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/remote-help-a-new-remote-assistance-tool-from-microsoft/ba-p/2822622)
- [Enable remote help scenarios with Microsoft Intune \(demo video\)](https://techcommunity.microsoft.com/t5/video-hub/enable-remote-help-scenarios-with-microsoft-endpoint-manager/ba-p/2911349)
- [Use Remote Help with Intune and Configuration Manager](https://learn.microsoft.com/en-us/intune/remote-help/)

#### Note 4: Support for alternate content providers

Alternate content providers aren't supported to get content from a content-enabled CMG. You can still use them on a client that communicates with a CMG and gets content from other supported content locations.

Tip

Starting in version 2203, you can also configure the task sequence to allow token authentication with alternate content providers. For more information, see [Task sequence variables: SMSTSAllowTokenAuthURLForACP](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-variables#smstsallowtokenauthurlforacp).

## Next steps

Next, plan how the design the CMG for the best performance at the appropriate scale:

[CMG performance and scale](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/perf-scale)
