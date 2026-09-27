<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Refresh an existing computer with a new version of Windows

*Applies to: Configuration Manager \(current branch\)*

Use Configuration Manager to partition and format an existing computer and then install a new OS. This process is sometimes called *reimaging* or *wipe and load*. For this scenario, choose from many different deployment methods, such as PXE, bootable media, or Software Center. You can also use a state migration point to store settings, and then restore them to the new OS.

To choose the right OS deployment scenario, see [Scenarios to deploy enterprise operating systems](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/scenarios-to-deploy-enterprise-operating-systems).

## Plan

### Plan for and implement infrastructure requirements

There are several infrastructure requirements that must be in place before you can deploy an OS. Some of these requirements include the Windows ADK, the User State Migration Tool \(USMT\), and Windows Deployment Services \(WDS\). For more information, see [Infrastructure requirements for OS deployment](https://learn.microsoft.com/en-us/intune/configmgr/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).

### Install a state migration point

If you want to capture settings from an existing computer, and then restore the settings to the new OS, consider using a state migration point. For more information, see [State migration point](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/prepare-site-system-roles-for-operating-system-deployments#state-migration-point).

## Configure

### Prepare a boot image

Boot images start a computer in a Windows PE environment. Windows PE is a minimal OS with limited components and services. From Windows PE, Configuration Manager can then install a full Windows OS on the computer.

For more information, see the following articles:

- [Manage boot images](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/manage-boot-images)
- [Customize boot images](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/customize-boot-images)
- [Distribute content](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)

### Prepare an OS image

The OS image contains the files necessary to install the OS on the destination computer.

For more information, see the following articles:

- [Manage OS images](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/manage-operating-system-images)
- [Distribute content](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute)

### Create a task sequence to deploy an OS

Use a task sequence to automate the installation of the OS. Depending on the deployment method that you choose, there might be additional considerations for the task sequence.

For more information, see the following articles:

- [Create a task sequence to install an OS](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-install-an-operating-system)
- [Manage user state](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/manage-user-state)

## Deploy

- Use one of the following deployment methods to deploy the OS:

  - [Use PXE to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)
  - [Use multicast to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-multicast-to-deploy-windows-over-the-network)
  - [Create an image for an OEM in factory or a local depot](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot)
  - [Use stand-alone media to deploy Windows without using the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network)
  - [Use bootable media to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-bootable-media-to-deploy-windows-over-the-network)
  - [Use Software Center to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network)

## Monitor

For more information, see [Monitor OS deployments](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/monitor-operating-system-deployments).

Note

When you reimage a UEFI device, Windows Boot Manager creates a new entry in the boot loader. This behavior is most noticeable when you repeatedly reimage a device, such as in a test environment or a student lab. It generally doesn't impact the performance or usage of the device. If the list gets too large, some specific hardware devices may encounter functional issues. For example, not booting to an external USB drive, or not able to select the current boot entry from the list. Use the Windows **bcdedit** command to clear unused boot entries. For more information, see [BCDEdit /deletevalue](https://learn.microsoft.com/en-us/windows-hardware/drivers/devtest/bcdedit--deletevalue).
