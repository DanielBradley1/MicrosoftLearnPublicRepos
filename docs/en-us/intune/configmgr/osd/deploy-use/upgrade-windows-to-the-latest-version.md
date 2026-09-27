<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/upgrade-windows-to-the-latest-version -->
<!-- Sitemap-Last-Modified: 2024-12-19 -->

# Upgrade Windows to the latest version with Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

This article provides the steps in Configuration Manager to upgrade the Windows OS on a computer. You can choose from different deployment methods, such as stand-alone media or Software Center. The in-place upgrade scenario has the following features:

- Upgrades the OS to Windows 10 or later, or Windows Server 2016 and later
- Keeps the applications, settings, and user data on the computer
- Has no external dependencies, such as the Windows ADK
- Is faster and more resilient than traditional OS deployments

Note

The Windows in-place upgrade task sequence supports deployment to internet-based clients managed through the [cloud management gateway](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/overview). This ability allows remote users to more easily upgrade to Windows without needing to connect to the intranet. For more information, see [Deploy Windows in-place upgrade via CMG](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/deploy-task-sequence-over-internet#deploy-windows-in-place-upgrade-via-cmg).

Starting in version 2103, you can upgrade by using a feature update deployed with the task sequence. This integration combines the simplicity of Windows servicing with the flexibility of task sequences. Servicing uses content that you synchronize through the software update point. This process simplifies the need to manually get, import, and maintain the Windows image content used with a standard task sequence to upgrade Windows. The size of the servicing ESD file is generally smaller than the OS upgrade package and WIM image file. You can also use Windows features such as Dynamic Update and Delivery Optimization. The user experience with a feature update in a task sequence is the same as with an OS upgrade package.

## Supported versions

### Upgrade version

Only create OS upgrade packages to upgrade to the following OS versions:

- Windows 11
- Windows 10
- Windows Server 2016
- Windows Server 2019
- Windows Server 2022
- 

  - Windows Server 2025

### Original version

Devices must run one of the following OS versions to target an OS upgrade task sequence:

#### Windows client

- Windows 7
- Windows 8.1
- An earlier version of Windows 10 or Windows 11. For example, you can upgrade Windows 10, version 2004 to Windows 10, version 21H1.

For more information, see [Windows client upgrade paths](https://learn.microsoft.com/en-us/windows/deployment/upgrade/windows-10-upgrade-paths).

Note

Starting in version 2403 OS deployment is supported for Windows on ARM64 devices. Starting in version 2103, you can deploy a task sequence with a feature update to an ARM64 device.

#### Windows Server

- Windows Server 2012
- Windows Server 2012 R2
- An earlier version of Windows Server 2016
- An earlier version of Windows Server 2019
- An earlier version of Windows Server 2022
- An earlier version of Windows Server 2025

For more information about Windows Server supported upgrade paths, see [Windows Server 2016 supported upgrade paths](https://learn.microsoft.com/en-us/windows-server/get-started/supported-upgrade-paths#upgrading-previous-retail-versions-of-windows-server-to-windows-server-2016) and [Windows Server Upgrade Center](https://learn.microsoft.com/en-us/windows-server/upgrade/upgrade-overview).

## Plan

### Task sequence requirements and limitations

Review the following requirements and limitations for the task sequence to upgrade an OS to make sure it meets your needs:

- Only add task sequence steps that are related to the core task of upgrading the OS. These steps primarily include installing packages, applications, or updates. Also use steps that run command lines, PowerShell, or set dynamic variables.
- Review drivers and applications that are installed on computers. Before you deploy the upgrade task sequence, make sure the drivers are compatible with the target version of Windows.

The following tasks aren't compatible with the in-place upgrade. They require you to use traditional OS deployments:

- Changing the computer's domain membership, or updating the local Administrators group.
- Implementing a fundamental change on the computer, such as:

  - Changing disk partitions
  - Changing the system architecture from x86 to x64
  - Implementing UEFI. For more information on a possible option, see [Convert from BIOS to UEFI during an in-place upgrade](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#bkmk_ipu).
  - Modifying the base OS language

- You have custom requirements including using a custom base image, using third-party disk encryption, or require WinPE offline operations.

### Infrastructure requirements

The only infrastructure prerequisite for the upgrade scenario is to have a distribution point available. Distribute the OS upgrade package or feature update, and any other content that you include in the task sequence. For more information, see [Install or modify a distribution point](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/install-and-configure-distribution-points).

Starting in version 2103, if you use a feature update with a Windows upgrade task sequence, you need a software update point to synchronize the **Upgrades** classification. For more information, see [Install and configure a software update point](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/install-a-software-update-point).

## Configure

### Prepare the OS upgrade package

The Windows upgrade package contains the source files necessary to upgrade the OS on the destination computer. The upgrade package must be the same edition, architecture, and language as the clients that you upgrade. For more information, see [Manage OS upgrade packages](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/manage-operating-system-upgrade-packages).

Note

In version 2103 or later, if you use a feature update with a Windows upgrade task sequence, you don't need the OS upgrade package.

### Create a task sequence to upgrade the OS

Use the steps in [Create a task sequence to upgrade an OS](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system) to automate the upgrade of the OS.

Note

To create a task sequence to upgrade Windows, you typically use the steps in [Create a task sequence to upgrade an OS](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system). The task sequence includes the **Upgrade OS** step, as well as additional recommended steps and groups to handle the end-to-end upgrade process.

You can create a custom task sequence and add the [Upgrade OS](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_UpgradeOS) step. This step is the only one required to upgrade Windows. If you choose this method, to complete the upgrade, also add the [Restart Computer](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_RestartComputer) step after the **Upgrade OS** step. Make sure to use the setting for **The currently installed default operating system** to restart the computer into the installed OS and not Windows PE.

## Next steps

First [create a task sequence to upgrade an OS](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

Then deploy the task sequence with one of the following deployment methods:

- [Use Software Center to deploy Windows over the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-software-center-to-deploy-windows-over-the-network)
- [Use stand-alone media to deploy Windows without using the network](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network)

  Important

  When you use stand-alone media, you must include a boot image in the task sequence. This configuration makes the task sequence available in the Task Sequence Media Wizard.

To monitor the task sequence deployment to upgrade the OS, see [Monitor OS deployments](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/monitor-operating-system-deployments).
