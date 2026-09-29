<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/edr-in-block-mode -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# Endpoint detection and response in block mode

This article describes EDR in block mode, which helps protect devices that are running a non-Microsoft antivirus solution \(with Microsoft Defender Antivirus in passive mode\).

## Prerequisites

### Supported operating systems

- Windows

## What is EDR in block mode?

[Endpoint detection and response](https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response) \(EDR\) in block mode provides added protection from malicious artifacts when Microsoft Defender Antivirus is not the primary antivirus product and is running in passive mode. EDR in block mode is available in Defender for Endpoint Plan 2.

Important

EDR in block mode cannot provide all available protection when Microsoft Defender Antivirus real-time protection is in passive mode. Some capabilities that depend on Microsoft Defender Antivirus to be the active antivirus solution will not work, such as the following examples:

- Real-time protection, including on-access scanning, is not available when Microsoft Defender Antivirus is in passive mode. To learn more about real-time protection policy settings, see **[Enable and configure Microsoft Defender Antivirus always-on protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus)**.
- Features like **[network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection)** and **[attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview)** and indicators \(file hash, ip address, URL, and certificates\) are only available when Microsoft Defender Antivirus is running in Active mode. It is expected that your non-Microsoft antivirus solution includes these capabilities.

EDR in block mode works behind the scenes to remediate malicious artifacts that were detected by EDR capabilities. Such artifacts might have been missed by the primary, non-Microsoft antivirus product. EDR in block mode allows Microsoft Defender Antivirus to take actions on post-breach, behavioral EDR detections.

EDR in block mode is integrated with [threat & vulnerability management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) capabilities. Your organization's security team gets a [security recommendation](https://learn.microsoft.com/en-us/defender-endpoint/api/ti-indicator) to turn EDR in block mode on if it isn't already enabled.

[![The recommendation to turn on EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/media/edrblockmode-tvmrecommendation.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/edrblockmode-tvmrecommendation.png#lightbox)

Tip

To get the best protection, make sure to **[deploy Microsoft Defender for Endpoint baselines](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-security-baseline)**.

Watch this video to learn why and how to turn on endpoint detection and response \(EDR\) in block mode, enable behavioral blocking, and containment at every stage from pre-breach to post-breach.

<iframe src="https://learn-video.azurefd.net/vod/player?id=69b80126-fa43-4f52-b89d-e4ebc3aba0a4" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## What happens when something is detected?

When EDR in block mode is turned on, and a malicious artifact is detected, Defender for Endpoint remediates that artifact. Your security operations team sees the detection status as **Blocked** or **Prevented** in the [Action center](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts#check-activity-details-and-status), listed as completed actions. The following image shows an instance of unwanted software that was detected and remediated through EDR in block mode:

[![The detection by EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/media/edr-in-block-mode-detection.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/edr-in-block-mode-detection.png#lightbox)

## Enable EDR in block mode

Important

- Make sure the [requirements](#requirements-for-edr-in-block-mode) are met before turning on EDR in block mode.
- Defender for Endpoint Plan 2 licenses are required.
- Beginning with [platform version 4.18.2202.X](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates), you can set EDR in block mode to target specific device groups using Intune CSPs. You can continue to set EDR in block mode tenant-wide in the [Microsoft Defender portal](https://security.microsoft.com).
- EDR in block mode is primarily recommended for devices that are running Microsoft Defender Antivirus in passive mode \(a non-Microsoft antivirus solution is installed and active on the device\).

### Microsoft Defender portal

1. Go to the Microsoft Defender portal \([https://security.microsoft.com/](https://security.microsoft.com/)\) and sign in.
2. Choose **Settings** > **Endpoints** > **General** > **Advanced features**.
3. Scroll down, and then turn on **Enable EDR in block mode**.

### Intune

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To create a custom policy in Intune, see [Deploy OMA-URIs to target a CSP through Intune, and a comparison to on-premises](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/device-configuration/deploy-oma-uris-to-target-csp-via-intune).

For more information on the Defender CSP used for EDR in block mode, see "Configuration/PassiveRemediation" under [Defender CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/defender-csp).

### Group Policy

You can use Group Policy to enable EDR in block mode.

1. In Centralized Group Policy, open the [Group Policy Management Console \(GPMC\)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console) on your Group Policy management computer.
2. In the GPMC console tree, expand Group Policy Objects in the forest and domain containing the GPO you want to edit.
3. Right-click the GPO, and then select **Edit**.
4. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Features**.
5. In the details pane of **Features**, open the **Enable EDR in block mode** setting. To open the setting, use any of the following methods:

   - Double-click the setting.
   - Right-click the setting, and then select **Edit**.
   - Select the setting, and then select **Action** > **Edit**.

6. In the setting window that opens, select **Enabled**, and then select **OK**.

Tip

You can also configure Group Policy locally on individual devices by using the Local Group Policy Editor \(`gpedit.msc`\). Navigate to the same path: **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Features**.

## Requirements for EDR in block mode

The following table lists requirements for EDR in block mode:

| Requirement | Details |
| --- | --- |
| Permissions | You must have either the Global Administrator or Security Administrator role assigned in [Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). For more information, see [Basic permissions](https://learn.microsoft.com/en-us/defender-endpoint/basic-permissions). |
| Operating system | Devices must be running one of the following versions of Windows:  <br>- Windows 11  <br>- Windows 10 \(all releases\)  <br>- Windows Server 2019 or later  <br>- Windows Server, version 1803 or later  <br>- Windows Server 2016 and Windows Server 2012 R2 \(with the [new unified client solution](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2)\) |
| Microsoft Defender for Endpoint Plan 2 | Devices must be onboarded to Defender for Endpoint. See the following articles:  <br>- [Minimum requirements for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements)  <br>- [Onboard devices and configure Microsoft Defender for Endpoint capabilities](https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure)  <br>- [Onboard Windows servers to the Defender for Endpoint service](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server)  <br>- [New Windows Server 2012 R2 and 2016 functionality in the modern unified solution](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2)  <br>\(See [Is EDR in block mode supported on Windows Server 2016 and Windows Server 2012 R2?](https://learn.microsoft.com/en-us/defender-endpoint/edr-block-mode-faqs)\) |
| Microsoft Defender Antivirus | Devices must have Microsoft Defender Antivirus installed and running in either active mode or passive mode. [Confirm Microsoft Defender Antivirus is in active or passive mode](https://learn.microsoft.com/en-us/defender-endpoint/edr-block-mode-faqs). |
| Cloud-delivered protection | Microsoft Defender Antivirus must be configured such that [cloud-delivered protection is enabled](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure). |
| Microsoft Defender Antivirus platform | Devices must be up to date. To confirm, using PowerShell, run the [Get-MpComputerStatus](https://learn.microsoft.com/en-us/powershell/module/defender/get-mpcomputerstatus) cmdlet as an administrator. In the **AMProductVersion** line, you should see **4.18.2001.10** or above.  <br>  <br>To learn more, see [Manage Microsoft Defender Antivirus updates and apply baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates). |
| Microsoft Defender Antivirus engine | Devices must be up to date. To confirm, using PowerShell, run the [Get-MpComputerStatus](https://learn.microsoft.com/en-us/powershell/module/defender/get-mpcomputerstatus) cmdlet as an administrator. In the **AMEngineVersion** line, you should see **1.1.16700.2** or above.  <br>  <br>To learn more, see [Manage Microsoft Defender Antivirus updates and apply baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates). |

Important

To get the best protection value, make sure your antivirus solution is configured to receive regular updates and essential features, and that your [exclusions are configured](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure). EDR in block mode respects exclusions that are defined for Microsoft Defender Antivirus, but not [indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview) that are defined for Microsoft Defender for Endpoint.

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## See also

- [Endpoint detection and response \(EDR\) in block mode frequently asked questions \(FAQ\)](https://learn.microsoft.com/en-us/defender-endpoint/edr-block-mode-faqs)
