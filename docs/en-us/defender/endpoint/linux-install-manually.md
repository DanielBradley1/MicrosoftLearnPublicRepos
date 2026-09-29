<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/linux-install-manually -->
<!-- Sitemap-Last-Modified: 2026-03-20 -->

# Deploy Microsoft Defender for Endpoint on Linux manually

You can deploy [Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux) by using various tools and methods. This article describes how to deploy Defender for Endpoint on Linux manually. To use another method, refer to the [Related content section](#related-content).

Note

We highly recommend using the [Defender Deployment Tool deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-defender-deployment-tool) method, as it simplifies the onboarding process, reduces manual tasks, and supports a wide range of deployment scenarios, including new installations, upgrades, and uninstalls. Please refer to the documentation for more details.

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

## Manual deployment steps

A successful deployment requires the completion of all of the following tasks:

- [Prerequisites and system requirements](#prerequisites-and-system-requirements)
- [Configure the Linux software repository](#configure-the-linux-software-repository)

  - [RHEL and variants \(CentOS, Fedora, Oracle Linux, Amazon Linux 2, Rocky, and Alma\)](#rhel-and-variants-centos-fedora-oracle-linux-amazon-linux-2-rocky-and-alma-1)
  - [SLES and variants](#sles-and-variants-1)
  - [Ubuntu and Debian systems](#ubuntu-and-debian-systems)
  - [Mariner](#mariner)

- [Preinstall setup for custom location installation](#preinstall-setup-for-custom-location-installation)
- [Application installation](#application-installation)

  - [RHEL and variants \(CentOS, Fedora, Oracle Linux, Amazon Linux 2, Rocky, and Alma\)](#rhel-and-variants-centos-fedora-oracle-linux-amazon-linux-2-rocky-and-alma)
  - [SLES and variants](#sles-and-variants)
  - [Ubuntu and Debian systems](#ubuntu-and-debian-systems-1)
  - [Mariner](#mariner-1)

- [Download the onboarding package](#download-the-onboarding-package)
- [Client configuration](#client-configuration)

## Prerequisites and system requirements

Before you begin, see [Prerequisites for Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites) for a description of prerequisites and system requirements for the current software version.

Warning

Upgrading your operating system to a new major version after the product installation requires the product to be reinstalled. You need to [Uninstall](https://learn.microsoft.com/en-us/defender-endpoint/linux-off-board-endpoints#uninstall-the-defender-application-from-a-linux-server) the existing Defender for Endpoint on Linux application, upgrade the operating system, and then reconfigure Defender for Endpoint on Linux following the steps in this article.

## Configure the Linux software repository

Defender for Endpoint on Linux can be deployed from one of the following channels \(denoted as *\[channel\]*\): *insiders-fast*, *insiders-slow*, or `prod`. Each of these channels corresponds to a Linux software repository. The instructions in this article describe configuring your device to use one of these repositories.

The choice of the channel determines the type and frequency of updates that are offered to your device. Devices in *insiders-fast* are the first ones to receive updates and new features, followed later by *insiders-slow* and lastly by `prod`.

In order to preview new features and provide early feedback, it's recommended that you configure some devices in your enterprise to use either *insiders-fast* or *insiders-slow*.

Warning

Switching the channel after the initial installation requires the product to be reinstalled. To switch the product channel: uninstall the existing package, reconfigure your device to use the new channel, and follow the steps in this document to install the package from the new location.

### RHEL and variants \(CentOS, Fedora, Oracle Linux, Amazon Linux 2, Rocky, and Alma\)

You can use either the `dnf` or the `yum` package manager to deploy Defender for Endpoint on Linux on RHEL and its variants. The instructions in the following sections include commands for both package managers; use just the relevant one.

1. Install either `dnf-plugins-core` or `yum-utils` if the one you want to use isn't installed yet:

   ```bash
   sudo dnf install dnf-plugins-core
   ```


   or


   ```bash
   sudo yum install yum-utils
   ```

2. Locate the correct package for your distribution and version. Use the following table to help guide you in locating the package:
   | Distro & version | Package |
   | --- | --- |
   | Alma 8.4 and higher | [https://packages.microsoft.com/config/alma/8/prod.repo](https://packages.microsoft.com/config/alma/8/prod.repo) |
   | Alma 9.2 and higher | [https://packages.microsoft.com/config/alma/9/prod.repo](https://packages.microsoft.com/config/alma/9/prod.repo) |
   | RHEL/Centos/Oracle 9.0-9.8 | [https://packages.microsoft.com/config/rhel/9/prod.repo](https://packages.microsoft.com/config/rhel/9/prod.repo) |
   | RHEL/Centos/Oracle 8.0-8.10 | [https://packages.microsoft.com/config/rhel/8/prod.repo](https://packages.microsoft.com/config/rhel/8/prod.repo) |
   | RHEL/Centos/Oracle 7.2-7.9 | [https://packages.microsoft.com/config/rhel/7.2/prod.repo](https://packages.microsoft.com/config/rhel/7.2/prod.repo) |
   | Amazon Linux 2 | [https://packages.microsoft.com/config/amazonlinux/2/prod.repo](https://packages.microsoft.com/config/amazonlinux/2/prod.repo) |
   | Amazon Linux 2023 | [https://packages.microsoft.com/config/amazonlinux/2023/prod.repo](https://packages.microsoft.com/config/amazonlinux/2023/prod.repo) |
   | Fedora 33 | [https://packages.microsoft.com/config/fedora/33/prod.repo](https://packages.microsoft.com/config/fedora/33/prod.repo) |
   | Fedora 34 | [https://packages.microsoft.com/config/fedora/34/prod.repo](https://packages.microsoft.com/config/fedora/34/prod.repo) |
   | Rocky 8.7 and higher | [https://packages.microsoft.com/config/rocky/8/prod.repo](https://packages.microsoft.com/config/rocky/8/prod.repo) |
   | Rocky 9.2 and higher | [https://packages.microsoft.com/config/rocky/9/prod.repo](https://packages.microsoft.com/config/rocky/9/prod.repo) |


   Note


   For your distribution and version, identify the closest entry for it \(by major, then minor\) under `https://packages.microsoft.com/config/rhel/`.


   Tip


   Online Kernel patching tools, such as Ksplice or similar, can lead to unpredictable OS stability if Defender for Endpoint is running. It's recommended to temporarily stop the Defender for Endpoint daemon before performing online Kernel patching. After the Kernel is updated, Defender for Endpoint on Linux can be safely restarted. This action is especially important for systems running Oracle Linux.

3. In the following commands, replace *\[version\]* and *\[channel\]* with the information you've identified:

   ```bash
   sudo dnf config-manager --add-repo https://packages.microsoft.com/config/rhel/[version]/[channel].repo
   ```


   or


   ```bash
   sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
   ```


   Tip


   Use hostnamectl command to identify system related information including release *\[version\]*.


   For example, if you're running CentOS 8 and want to deploy Defender for Endpoint on Linux from the `prod` channel:


   ```bash
   sudo dnf config-manager --add-repo https://packages.microsoft.com/config/rhel/8/prod.repo
   ```


   or


   ```bash
   sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/8/prod.repo
   ```


   Or if you wish to explore new features on selected devices, you might want to deploy Defender for Endpoint on Linux to *insiders-fast* channel:


   ```bash
   sudo dnf config-manager --add-repo https://packages.microsoft.com/config/rhel/8/insiders-fast.repo
   ```


   or


   ```bash
   sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/8/insiders-fast.repo
   ```

4. Install the Microsoft GPG public key:

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

### SLES and variants

Note

For your distribution and version, identify the closest entry for it \(by major, then minor\) under `https://packages.microsoft.com/config/sles/`.

1. In the following commands, replace *\[distro\]* and *\[version\]* with the information you've identified:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```


   Tip


   Use SPident command to identify system related information including release *\[version\]*.


   For example, if you're running SLES 12 and wish to deploy Defender for Endpoint on Linux from the `prod` channel:


   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

2. Install the Microsoft GPG public key:

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

### Ubuntu and Debian systems

1. Install `curl` if it isn't installed yet:

   ```bash
   sudo apt install curl
   ```

2. Install `libplist-utils` if it isn't installed yet:

   ```bash
   sudo apt install libplist-utils
   ```


   Note


   For your distribution and version, identify the closest entry for it \(by major, then minor\) under `https://packages.microsoft.com/config/[distro]/`.

3. In the following command, replace *\[distro\]* and *\[version\]* with the information you've identified:

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```


   Tip


   Use hostnamectl command to identify system related information including release *\[version\]*.


   For example, if you're running Ubuntu 18.04 and wish to deploy Defender for Endpoint on Linux from the `prod` channel:


   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

4. Install the repository configuration:

   ```bash
   sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
   ```


   For example, if you chose `prod` channel:


   ```bash
   sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
   ```

5. Install the `gpg` package if not already installed:

   ```bash
   sudo apt install gpg
   ```


   If `gpg` isn't available, then install `gnupg`.


   ```bash
   sudo apt install gnupg
   ```

6. Install the Microsoft GPG public key:

   - For Debian 11/Ubuntu 22.04 and earlier, run the following commands.

     ```bash
     curl -sSL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null
     sudo chmod o+r /etc/apt/trusted.gpg.d/microsoft.gpg
     ```

   - For Debian 12, Ubuntu 24.04 and later, run the following commands.

     ```bash
     curl -sSL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /usr/share/keyrings/microsoft-prod.gpg > /dev/null
     sudo chmod o+r /usr/share/keyrings/microsoft-prod.gpg
     ```

   - For Debian 13 and later, run the following commands.

     ```bash
     curl -sSL https://packages.microsoft.com/keys/microsoft-2025.asc | gpg --dearmor | sudo tee /usr/share/keyrings/microsoft-prod.gpg > /dev/null
     sudo chmod o+r /usr/share/keyrings/microsoft-prod.gpg
     ```

7. Install the HTTPS driver if not already installed:

   ```bash
   sudo apt install apt-transport-https
   ```

8. Update the repository metadata:

   ```bash
   sudo apt update
   ```

### Mariner

1. Install `dnf-plugins-core` if it isn't installed yet:

   ```bash
   sudo dnf install dnf-plugins-core
   ```

2. Configure and enable the required repositories.

   Note

   On Mariner, Insider Fast Channel isn't available.

   If you want to deploy Defender for Endpoint on Linux from the `prod` channel. Use the following commands

   ```bash
   sudo dnf install mariner-repos-extras
   sudo dnf config-manager --enable mariner-official-extras
   ```


   Or if you wish to explore new features on selected devices, you might want to deploy Defender for Endpoint on Linux to *insiders-slow* channel. Use the following commands:


   ```bash
   sudo dnf install mariner-repos-extras-preview
   sudo dnf config-manager --enable mariner-official-extras-preview
   ```

## Preinstall setup for custom location installation

These steps are applicable only if Defender is to be installed in a custom location. For detailed instructions on installing Microsoft Defender for Endpoint to a custom location, see [Manual installation: preinstallation setup](https://learn.microsoft.com/en-us/defender-endpoint/linux-custom-location-installation#manual-installation-preinstallation-setup).

For details on installing to a custom location, refer: [Enabling deployment of Defender for Endpoint on Linux to a custom location](https://learn.microsoft.com/en-us/defender-endpoint/linux-custom-location-installation).

## Application installation

Use the commands in the following sections to install Defender for Endpoint on your Linux distribution.

### RHEL and variants \(CentOS, Fedora, Oracle Linux, Amazon Linux 2, Rocky, and Alma\)

```bash
sudo dnf install mdatp
```

or

```bash
sudo yum install mdatp
```

Note

If you have multiple Microsoft repositories configured on your device, you can be specific about which repository to install the package from. The following example shows how to install the package from the `production` channel if you also have the `insiders-fast` repository channel configured on this device. This situation can happen if you're using multiple Microsoft products on your device. Depending on the distribution and the version of your server, the repository alias might be different than the one in the following example.

```bash
# list all repositories
sudo dnf repolist
```

or

```bash
# list all repositories
sudo yum repolist
```

```console
...
packages-microsoft-com-prod               packages-microsoft-com-prod        316
packages-microsoft-com-prod-insiders-fast packages-microsoft-com-prod-ins      2
...
```

For example to install the package from the production repository:

```bash
sudo dnf --enablerepo=packages-microsoft-com-prod install mdatp
```

or

```bash
sudo yum --enablerepo=packages-microsoft-com-prod install mdatp
```

### SLES and variants

```bash
sudo zypper install mdatp
```

Note

If you have multiple Microsoft repositories configured on your device, you can be specific about which repository to install the package from. The following example shows how to install the package from the `production` channel if you also have the `insiders-fast` repository channel configured on this device. This situation can happen if you're using multiple Microsoft products on your device.

```bash
zypper repos
```

```console
...
#  | Alias | Name | ...
XX | packages-microsoft-com-insiders-fast | microsoft-insiders-fast | ...
XX | packages-microsoft-com-prod | microsoft-prod | ...
...
```

```bash
sudo zypper install packages-microsoft-com-prod:mdatp
```

### Ubuntu and Debian systems

```bash
sudo apt install mdatp
```

Note

If you have multiple Microsoft repositories configured on your device, you can be specific about which repository to install the package from. The following example shows how to install the package from the `production` channel if you also have the `insiders-fast` repository channel configured on this device. This situation can happen if you're using multiple Microsoft products on your device.

The version numbers and release codenames in the following code snippets are examples. Use the actual release codename the bash command returns.

```bash
cat /etc/apt/sources.list.d/*
```

```console
deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod insiders-fast main
deb [arch=amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod bionic main
```

```bash
sudo apt -t bionic install mdatp
```

Note

Reboots are NOT required after installing or updating Microsoft Defender for Endpoint on Linux except when you're running auditD in immutable mode.

### Mariner

```bash
sudo dnf install mdatp
```

Note

If you have multiple Microsoft repositories configured on your device, you can be specific about which repository to install the package from. The following example shows how to install the package from the `production` channel if you also have the `insiders-slow` repository channel configured on this device. This situation can happen if you're using multiple Microsoft products on your device.

```bash
sudo dnf config-manager --disable mariner-official-extras-preview
sudo dnf config-manager --enable mariner-official-extras
```

## Download the onboarding package

Download the onboarding package from the [Microsoft Defender portal](https://security.microsoft.com).

Warning

Repackaging the Defender for Endpoint installation package is not a supported scenario. Doing so can negatively impact the integrity of the product and lead to adverse results, including but not limited to triggering tampering alerts and updates failing to apply.

Important

If you miss this step, any command executed shows a warning message indicating that the product is unlicensed. Also the `mdatp health` command returns a value of `false`.

1. In the Microsoft Defender portal, go to **System** > **Settings** > **Endpoints** > **Device management** > **Onboarding**.
2. In the first drop-down menu, select **Linux Server** as the operating system. In the second drop-down menu, select **Local Script** as the deployment method.
3. Select **Download onboarding package**. Save the file as `WindowsDefenderATPOnboardingPackage.zip`.
4. From a command prompt, verify that you have the file, and extract the contents of the archive:

   ```bash
   ls -l
   ```


   ```console
   total 8
   -rw-r--r-- 1 test  staff  5752 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
   ```


   ```bash
   unzip WindowsDefenderATPOnboardingPackage.zip
   ```


   ```console
   Archive:  WindowsDefenderATPOnboardingPackage.zip
   inflating: MicrosoftDefenderATPOnboardingLinuxServer.py
   ```

## Client configuration

1. Copy `MicrosoftDefenderATPOnboardingLinuxServer.py` to the target device.

   Note

   Initially the client device isn't associated with an organization and the *orgId* attribute is blank.

   ```bash
   mdatp health --field org_id
   ```

2. Run one of the following commands, depending on your scenario:

   Note

   To run this command, you must have `python` or `python3` installed on the device depending on the distro and version. If needed, see [Step-by-step Instructions for Installing Python on Linux](https://opensource.com/article/20/4/install-python-linux).

   If you're running RHEL 8.x or Ubuntu 20.04 or higher, you need to use `python3`. Run the following command:

   ```bash
   sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
   ```


   For other distros and versions, you need to use `python`. Run the following command:


   ```bash
   sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
   ```

3. Verify that the device is now associated with your organization and reports a valid organization identifier:

   ```bash
   mdatp health --field org_id
   ```

4. Check the health status of the product by running the following command. A return value of `true` denotes that the product is functioning as expected:

   ```bash
   mdatp health --field healthy
   ```


   Important


   When the product starts for the first time, it downloads the latest anti-malware definitions. This process might take up to a few minutes depending on the network connectivity. During this time, the command mentioned earlier returns a value of `false`. You can check the status of the definition update using the following command:


   ```bash
   mdatp health --field definitions_status
   ```


   You might also need to configure a proxy after completing the initial installation. See [Configure Defender for Endpoint on Linux for static proxy discovery: Post-installation configuration](https://learn.microsoft.com/en-us/defender-endpoint/linux-static-proxy-configuration#post-installation-configuration).

5. Run an antivirus detection test to verify that the device is properly onboarded and reporting to the service. Perform the following steps on the newly onboarded device:

   1. Ensure that real-time protection is enabled \(denoted by a result of `true` from running the following command\):

      ```bash
      mdatp health --field real_time_protection_enabled
      ```


      If it isn't enabled, execute the following command:


      ```bash
      mdatp config real-time-protection --value enabled
      ```

   2. To run a detection test, open a Terminal window, and then run the following command:

      ```bash
      curl -o /tmp/eicar.com.txt https://secure.eicar.org/eicar.com.txt
      ```

   3. You can run more detection tests on zip files using either of the following commands:

      ```bash
      curl -o /tmp/eicar_com.zip https://secure.eicar.org/eicar_com.zip
      curl -o /tmp/eicarcom2.zip https://secure.eicar.org/eicarcom2.zip
      ```


      The files should be quarantined by Defender for Endpoint on Linux.

   4. Use the following command to list all the detected threats:

      ```bash
      mdatp threat list
      ```

6. Run an EDR detection test and simulate a detection to verify that the device is properly onboarded and reporting to the service. Perform the following steps on the newly onboarded device:

   1. Verify that the onboarded Linux server appears in the Defender portal. If this is the first onboarding of the machine, it can take up to 20 minutes until it appears.
   2. Download and extract the [script file](https://aka.ms/MDE-Linux-EDR-DIY) to an onboarded Linux server, and then run the following command: `./mde_linux_edr_diy.sh`

      After a few minutes, a detection should be raised in Microsoft Defender XDR.
   3. Look at the alert details, machine timeline, and perform your typical investigation steps.

## Software requirements

For information, see [Software requirements](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites#software-requirements).

## Troubleshoot installation issues

If you experience any installation issues, for self-troubleshooting, follow these steps:

1. For information on how to find the log that's generated automatically when an installation error occurs, see [Log installation issues](https://learn.microsoft.com/en-us/defender-endpoint/linux-resources#log-installation-issues).
2. For information about common installation issues, see [Installation issues](https://learn.microsoft.com/en-us/defender-endpoint/linux-support-install).
3. If health of the device is `false`, see [Defender for Endpoint agent health issues](https://learn.microsoft.com/en-us/defender-endpoint/health-status).
4. For product performance issues, see [Troubleshoot performance issues](https://learn.microsoft.com/en-us/defender-endpoint/linux-support-perf).
5. For proxy and connectivity issues, see [Troubleshoot cloud connectivity issues](https://learn.microsoft.com/en-us/defender-endpoint/linux-support-connectivity).

To get support from Microsoft, open a support ticket, and provide the log files created by using the [client analyzer](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer).

## How to switch between channels

For example, to change channel from Insiders-Fast to Production, do the following:

1. Uninstall the `Insiders-Fast channel` version of Defender for Endpoint on Linux.

   ```bash
   sudo dnf remove mdatp
   ```


   or


   ```bash
   sudo yum remove mdatp
   ```

2. Disable the Defender for Endpoint on Linux Insiders-Fast channel

   ```bash
   sudo dnf config-manager --disable packages-microsoft-com-fast-prod
   ```


   or


   ```bash
   sudo yum-config-manager --disable packages-microsoft-com-fast-prod
   ```

3. Reinstall Microsoft Defender for Endpoint on Linux using the `Production channel`, and onboard the device in the [Microsoft Defender portal](https://security.microsoft.com).

## How to configure policies for Defender for Endpoint on Linux

To configure antivirus and EDR settings, see the following articles:

- [Defender for Endpoint security settings management](https://learn.microsoft.com/en-us/intune/intune-service/protect/mde-security-integration) describes how to configure settings in the Microsoft Defender portal. \(*This method is recommended*.\)
- [Set preferences for Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences) describes settings you can configure.

## Uninstall Defender for Endpoint on Linux

For manual uninstallation, execute the following command for your Linux distribution.

- `sudo dnf remove mdatp` or `sudo yum remove mdatp` \(depending on your package manager\) for RHEL and variants\(CentOS and Oracle Linux\).
- `sudo zypper remove mdatp` for SLES and variants.
- `sudo apt purge mdatp` for Ubuntu and Debian systems.
- `sudo dnf remove mdatp` for Mariner

## Related content

- [Prerequisites for Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites)
- Other deployment methods:

  - [Deployment tool based deployment \(Recommended\)](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-defender-deployment-tool)
  - [Installer script based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-installer-script)
  - [Ansible based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-ansible)
  - [Chef based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-with-chef)
  - [Puppet based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-puppet)
  - [Saltstack based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-saltack)
  - [Golden Image based deployment](https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-using-golden-images)
  - [Connect your non-Azure machines to Defender for Cloud with Defender for Endpoint](https://learn.microsoft.com/en-us/azure/defender-for-cloud/onboard-machines-with-defender-for-endpoint) \(direct onboarding using Defender for Cloud\)
  - [Deployment guidance for Defender for Endpoint on Linux for SAP](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-deployment-on-sap)
  - [Install Defender for Endpoint on Linux to a custom location](https://learn.microsoft.com/en-us/defender-endpoint/linux-custom-location-installation)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
