<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-security-baseline -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Increase compliance with the Microsoft Defender for Endpoint security baseline

Microsoft Intune security baselines are groups of preconfigured Windows settings recommended by the relevant Microsoft security teams. The Microsoft Defender for Endpoint security baseline helps you configure and enforce Defender security settings on managed Windows devices.

Use this article to compare the Defender for Endpoint and Windows security baselines and to create, assign, and monitor the Defender for Endpoint baseline in Intune. For general information about security baselines, see [Security baselines FAQ](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview#q--a).

## Prerequisites

Before you deploy and monitor the Defender for Endpoint security baseline:

- [Enroll your devices in Intune](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines#enroll-devices-to-intune-management).
- [Ensure you have the required permissions](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines#obtain-required-permissions). To manage security baselines, the Intune role assigned to your account needs **Read** permission for the organization and **Assign**, **Create**, **Delete**, **Read**, and **Update** permissions for security baselines. The **Policy and Profile Manager** role is the least privileged built-in Intune role with these permissions.
- Ensure the devices run a supported version of Windows 11 or Windows 10, version 1809 \(November 2018\), or later.
- Ensure you have an active Defender for Endpoint subscription and a Microsoft Intune Plan 1 subscription.

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

## Compare the Microsoft Defender for Endpoint and Windows security baselines

The **Security Baseline for Windows 10 and later** contains recommended settings for Windows, including settings for browsers, PowerShell, and Windows security features. The **Microsoft Defender for Endpoint baseline** contains settings recommended by the Defender for Endpoint security team.

Review the default settings for each baseline:

- [Windows MDM security baseline settings reference for Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/ref-windows-mdm-settings)
- [Microsoft Defender for Endpoint security baseline settings reference for Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/ref-defender-settings)

You can deploy more than one baseline to the same devices. However, the baselines can contain overlapping settings with different default values. Review the settings in each baseline, customize them for your environment, and test the profiles before broad deployment to prevent policy conflicts.

Use the latest baseline versions as soon as practical. New versions can add or remove settings and change defaults to align with current security recommendations. For instructions, see [Update a baseline profile to the latest version](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/configure-baselines#update-a-baseline-profile-to-the-latest-version) \(opens in a new tab in the Intune documentation\).

Note

The Defender for Endpoint security baseline is optimized for physical devices and is currently not recommended for virtual machines \(VMs\) or virtual desktop infrastructure \(VDI\) endpoints. Some baseline settings can affect remote interactive sessions in virtualized environments.

## Review and assign the Microsoft Defender for Endpoint security baseline

For the complete procedure to create and assign a security baseline profile, see [Create a profile for a security baseline](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/configure-baselines#create-a-profile-for-a-security-baseline) \(opens in a new tab in the Intune documentation\).

When you create the profile, use these specific settings:

- **Security baseline**: On the **Endpoint security \| Security baselines** page in the Microsoft Intune admin center at [https://intune.microsoft.com](https://intune.microsoft.com), select **Microsoft Defender for Endpoint baseline**, and then select **Create policy**.
- **Configuration settings** tab: Review every default setting and customize settings that don't meet your organization's requirements. The defaults represent the Defender for Endpoint security team's recommended configuration.
- **Assignments** tab: Assign the profile to the appropriate user or device groups. The setting scope determines whether you should use user groups, device groups, or separate profiles for each type.
- **Review + create** tab: Review the profile, and then select **Create** to save and deploy it to the assigned groups.

Tip

Security baselines in Intune provide a convenient way to configure and protect managed Windows devices. For more information, see [Use security baselines to help secure Windows devices you manage with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview).

## Monitor the Microsoft Defender for Endpoint security baseline

After you assign the baseline profile, use the following reports in Intune to monitor its deployment:

- **Device and user check-in status**: Review the number of devices and users that report each deployment status. Select **View report** to generate detailed results and review the status of individual devices.
- **Device assignment status**: Review the assignment status for each targeted device.
- **Per setting status**: Review the number of devices that report success, an error, or a conflict for each setting in the profile.

For the complete procedure, see [Monitor the baseline and your devices](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/monitor-baselines#monitor-the-baseline-and-your-devices) \(opens in a new tab in the Intune documentation\).

## Related articles

- [Ensure your devices are configured properly](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines)
- [Get devices onboarded to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-onboarding)
- [Monitor ASR rule activity](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor)
