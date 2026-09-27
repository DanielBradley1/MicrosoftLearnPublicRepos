<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Use bootable media to deploy Windows over the network with Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Bootable media only includes the boot image and a pointer to the task sequence. It downloads the OS image and other referenced content from the network. Since the bootable media doesn't contain much content, you can update the task sequence and most content without having to replace the media.

Deploy operating systems over the network with boot media in the following scenarios:

- [Refresh an existing computer with a new version of Windows](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)
- [Install a new version of Windows on a new computer \(bare metal\)](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/install-new-windows-version-new-computer-bare-metal)
- [Replace an existing computer and transfer settings](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/replace-an-existing-computer-and-transfer-settings)

Complete the steps in one of the OS deployment scenarios and then use the following sections to use bootable media to deploy the OS.

## Configure deployment settings

When you use bootable media to start the OS deployment process, configure the task sequence deployment to make the OS available to the media. Set this option on the **Deployment Settings** page of the deployment. For the **Make available to the following** setting, select one of the following options:

- Configuration Manager clients, media, and PXE
- Only media and PXE
- Only media and PXE \(hidden\)

For more information, see [Deploy a task sequence](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/deploy-a-task-sequence).

## Create the bootable media

When you create bootable media, specify whether it's a USB flash drive or CD/DVD set. The computer that starts the media must support the option that you choose as a bootable drive. For more information, see [Create bootable media](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-bootable-media).

## Install the OS from bootable media

To install the OS, insert the bootable media, and then power on the computer.

## Support for cloud-based content

Starting in version 2006, bootable media can download cloud-based content. For example, you send a USB key to a user at a remote office to reimage their device. Or an office that has a local PXE server, but you want devices to prioritize cloud services as much as possible. Instead of further taxing the WAN to download large OS deployment content, boot media and PXE deployments can now get content from cloud-based sources.

For more information, see [Bootable media support for cloud-based content](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/deploy-task-sequence-over-internet#bootable-media-support-for-cloud-based-content).

## Next steps

[User experiences for OS deployment](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/user-experience#task-sequence-wizard)
