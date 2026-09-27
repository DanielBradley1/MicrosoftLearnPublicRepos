<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/install-new-windows-version-new-computer-bare-metal -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Install a new version of Windows on a new computer \(bare metal\) with Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

This topic provides the general steps in Configuration Manager to install an operating system on a new computer. For this scenario, you can choose from many different deployment methods, such as PXE, OEM, or stand-alone media. If you are unsure that this is the right operating system deployment scenario for you, see [Scenarios to deploy enterprise operating systems](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems).

Use the following sections to refresh an existing computer with a new version of Windows.

## Plan

- **Plan for and implement infrastructure requirements**

  There are several infrastructure requirements that must be in place before you can deploy operating systems, such as Windows ADK, Windows Deployment Services \(WDS\), supported hard disk configurations, etc. For more information, see [Infrastructure requirements for operating system deployment](https://learn.microsoft.com/en-us/intune/configmgr/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).

## Configure

1. **Prepare a boot image**

   Boot images start a computer in a Windows PE environment \(a minimal operating system with limited components and services\) that can then install a full Windows operating system on the computer. When you deploy operating systems, you must select a boot image to use and distribute the image to a distribution point. Use the following to prepare the boot image:

   - To learn more about boot images, see [Manage boot images](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/manage-boot-images).
   - For more information about how to customize a boot image, see [Customize boot images](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/customize-boot-images).
   - Distribute the boot image to distribution points. For more information, see [Distribute content](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).

2. **Prepare an operating system image**

   The operating system image contains the files necessary to install the operating system on the destination computer. Use the following to prepare the operating system image:

   - To learn more about how to create an operating system image, see [Manage operating system images](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/manage-operating-system-images).
   - Distribute the operating system image to distribution points. For more information, see [Distribute content](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).


   Note


   New installations of Windows can also be performed from installation source files via OS upgrade packages, but use OS images such as **install.wim** instead.


   Deploying new installations of Windows via OS upgrade packages is still supported, but is dependent on drivers being compatible with this method. When installing Windows from an OS upgrade package, drivers are installed while still in Windows PE versus simply being injected while in Windows PE. Some drivers are not compatible with being installed while in Windows PE. If drivers are not compatible with being installed while in Windows PE, then use an OS image instead.

3. **Create a task sequence to deploy operating systems over the network**

   Use a task sequence to automate the installation of the operating system over the network. Use the steps in [Create a task sequence to install an operating system](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-install-an-operating-system) to create the task sequence to deploy the operating system. Depending on the deployment method that you choose, there might be additional considerations for the task sequence.

## Deploy

- Use one of the following deployment methods to deploy the operating system:

  - [Use PXE to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)
  - [Use multicast to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network)
  - [Create an image for an OEM in factory or a local depot](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot)
  - [Use stand-alone media to deploy Windows without using the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network)
  - [Use bootable media to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network)

## Monitor

- **Monitor the task sequence deployment**

  To monitor the task sequence deployment to install the operating system, see [Monitor operating system deployments](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/monitor-operating-system-deployments).
