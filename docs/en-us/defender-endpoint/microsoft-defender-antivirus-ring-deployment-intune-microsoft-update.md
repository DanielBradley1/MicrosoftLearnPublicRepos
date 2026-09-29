<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-intune-microsoft-update -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Deploy Microsoft Defender Antivirus updates in rings by using Intune and Microsoft Update

Use deployment rings to validate Microsoft Defender Antivirus engine, platform, and security intelligence updates on pilot devices before broader production deployment. The procedures modify existing endpoint security **Antivirus** policies in Microsoft Intune for devices that get updates directly from Microsoft Update.

The procedures require Microsoft Intune. Intune is a separate product that isn't part of Microsoft Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, see [Microsoft Defender Antivirus ring deployment](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment) for other management methods. For licensing information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

## Prerequisites

Before you configure the deployment rings, make sure your environment meets the following requirements:

- Existing endpoint security **Antivirus** policies that use the **Windows** platform and **Microsoft Defender Antivirus** profile for pilot and production device groups.
- Devices that can access Microsoft Update directly.
- Supported Windows devices. To manage Windows Server devices through Intune antivirus policies, use [Defender for Endpoint security settings management](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/security-settings-management).

## Configure the pilot environment

Use a limited group of representative test devices for the pilot environment. Include the device types and workloads used in your production environment. If you have a Citrix environment, include at least one persistent or nonpersistent Citrix VM in the pilot group, as applicable.

[![Diagram of an example Microsoft Defender Antivirus ring deployment schedule.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-intune-schedule.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-intune-schedule.png#lightbox)

To modify your pilot endpoint security **Antivirus** policy in Microsoft Intune, see [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(link opens in a new tab in the Intune documentation\).

1. Go to **Manage** > **Antivirus** on the **Endpoint security \| Overview** page at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/overview](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), and then select your pilot policy \(for example, *MDAV\_Settings\_Pilot*\).
2. On the policy details page, select **Edit** next to **Configuration settings**, and then configure the following recommended settings:

   - **Engine Updates Channel**: Select **Beta Channel**.
   - **Platform Updates Channel**: Select **Beta Channel**.
   - **Security Intelligence Updates Channel**: Select **Current Channel \(Staged\)**.


   Note


   Security intelligence updates were previously called signature updates or definition updates.


   [![Screenshot of the recommended Microsoft Defender Antivirus update-channel settings for the pilot policy in Intune.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-intune-microsoft-defender-antivirus-pilot-policy-settings.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-intune-microsoft-defender-antivirus-pilot-policy-settings.png#lightbox)

3. Save the policy changes.

For more information, see [Antivirus policy profiles](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/antivirus#antivirus-policy-profiles), [Microsoft Defender Antivirus update-channel settings](https://learn.microsoft.com/en-us/defender-endpoint/use-intune-config-manager-microsoft-defender-antivirus#engine-updates-channel), and [Manage the gradual rollout process for Microsoft Defender updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-gradual-rollout).

## Configure the production environment

Use a production policy to deploy validated updates broadly or to delay monthly engine and platform updates for critical devices.

To modify your production endpoint security **Antivirus** policy in Microsoft Intune, see [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(link opens in a new tab in the Intune documentation\).

1. Go to **Manage** > **Antivirus** on the **Endpoint security \| Overview** page at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/overview](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), and then select your production policy \(for example, *MDAV\_Settings\_Production*\).
2. On the policy details page, select **Edit** next to **Configuration settings**, and then configure the following recommended settings:

   - **Engine Updates Channel**: Select **Critical - Time delay**. This channel delays engine updates by 48 hours and is intended for critical environments.
   - **Platform Updates Channel**: Select **Critical - Time delay**. This channel delays platform updates by 48 hours and is intended for critical environments.
   - **Security Intelligence Updates Channel**: Select **Current Channel \(Broad\)**. This configuration provides a three-hour window to identify a false positive and prevent an incompatible security intelligence update from reaching production devices.


   [![Screenshot of the recommended Microsoft Defender Antivirus update-channel settings for the production policy in Intune.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-intune-microsoft-defender-antivirus-production-policy-settings.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-intune-microsoft-defender-antivirus-production-policy-settings.png#lightbox)

3. Save the policy changes.

### If you encounter problems

If a security intelligence update causes problems in your production environment, you can temporarily prevent devices assigned to the production policy from downloading more security intelligence updates while you investigate. Setting **Signature Update Fallback Order** to only `FileShares` while leaving **Signature Update File Shares Sources** empty leaves Microsoft Defender Antivirus without an available update source.

To modify your production endpoint security **Antivirus** policy in Microsoft Intune, see [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(link opens in a new tab in the Intune documentation\).

Important

Devices don't receive new security intelligence updates until you restore the update sources. Restore the original settings as soon as you resolve the issue.

1. Go to **Manage** > **Antivirus** on the **Endpoint security \| Overview** page at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/overview](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), and then select your production policy \(for example, *MDAV\_Settings\_Production*\).
2. On the policy details page, select **Edit** next to **Configuration settings**. Record the current **Signature Update Fallback Order** value so you can restore it later, and then configure the following settings:

   - **Signature Update Fallback Order**: Enter `FileShares`.
   - **Signature Update File Shares Sources**: Leave this setting empty.


   [![Screenshot of the Microsoft Defender Antivirus file-share fallback setting for the production policy in Intune.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-intune-microsoft-defender-antivirus-production-policy-fallback.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-intune-microsoft-defender-antivirus-production-policy-fallback.png#lightbox)

3. Save the policy changes. Intune notifies online devices to sync. The notification can take from immediately to a few hours, and offline devices receive the policy when they next sync. For more information, see [Policy refresh intervals](https://learn.microsoft.com/en-us/intune/device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).
4. After you resolve the issue, edit the policy again, restore **Signature Update Fallback Order** to the value you recorded before making the temporary change, and then save the policy.

## Next step

[Microsoft Defender Antivirus ring deployment](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment)
