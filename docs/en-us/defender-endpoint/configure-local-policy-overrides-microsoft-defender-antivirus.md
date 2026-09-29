<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Prevent or allow users to locally modify Microsoft Defender Antivirus policy settings

By default, Microsoft Defender Antivirus settings that you deploy through a Group Policy Object \(GPO\) prevent users from changing those settings locally. However, some users might need to change settings on their own devices. For example, security researchers and threat investigators often need more control over individual settings.

The following procedures configure local overrides and control how local and global exclusion lists are merged.

Tip

If you're looking for antivirus-related information for other platforms, see the following articles:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

## Prerequisites

### Supported operating systems

- Windows

## Configure local overrides for Microsoft Defender Antivirus settings using Group Policy

Group Policy is the only supported method for configuring these local override policies. By default, the policies are set to **Disabled**. If you set a policy to **Enabled**, users can change the related setting on their devices by using one of the following methods:

- The [Windows Security app](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-security-center-antivirus).
- The Local Group Policy Editor \(`gpedit.msc`\).
- The [**Set-MpPreference**](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference) cmdlet \(where supported\).

To configure local override policies by using Group Policy, follow these steps:

1. Open the [Group Policy Management Console \(GPMC\)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console) on your Group Policy management computer.
2. In the GPMC console tree, expand Group Policy Objects in the forest and domain containing the GPO you want to edit.
3. Right-click the GPO, and then select **Edit**.
4. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus**.
5. Go to the **Location** identified in the following table \(for example, **MAPS**\).
   | Location | Setting | Article |
   | --- | --- | --- |
   | MAPS | Configure local setting override for reporting to Microsoft MAPS | [Enable cloud-delivered protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure) |
   | Quarantine | Configure local setting override for the removal of items from Quarantine folder | [Configure remediation for scans](https://learn.microsoft.com/en-us/defender-endpoint/configure-remediation-microsoft-defender-antivirus) |
   | Real-time protection | Configure local setting override for monitoring file and program activity on your computer | [Enable and configure Microsoft Defender Antivirus always-on protection and monitoring](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) |
   | Real-time protection | Configure local setting override for monitoring for incoming and outgoing file activity | [Enable and configure Microsoft Defender Antivirus always-on protection and monitoring](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) |
   | Real-time protection | Configure local setting override for scanning all downloaded files and attachments | [Enable and configure Microsoft Defender Antivirus always-on protection and monitoring](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) |
   | Real-time protection | Configure local setting override to turn on behavior monitoring | [Enable and configure Microsoft Defender Antivirus always-on protection and monitoring](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) |
   | Real-time protection | Configure local setting override to turn on real-time protection | [Enable and configure Microsoft Defender Antivirus always-on protection and monitoring](https://learn.microsoft.com/en-us/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) |
   | Remediation | Configure local setting override for the time of day to run a scheduled full scan to complete remediation | [Configure remediation for scans](https://learn.microsoft.com/en-us/defender-endpoint/configure-remediation-microsoft-defender-antivirus) |
   | Scan | Configure local setting override for maximum percentage of CPU utilization | [Configure and run scans](https://learn.microsoft.com/en-us/defender-endpoint/run-scan-microsoft-defender-antivirus) |
   | Scan | Configure local setting override for the scheduled scan day | [About scheduled scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans) |
   | Scan | Configure local setting override for scheduled quick scan time | [About scheduled scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans) |
   | Scan | Configure local setting override for scheduled scan time | [About scheduled scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans) |
   | Scan | Configure local setting override for the scan type to use for a scheduled scan | [About scheduled scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans) |
6. In the details pane for the selected **Location**, find the setting listed in the **Setting** column of the table. For example, select **Configure local setting override for reporting to Microsoft MAPS**. Open the setting by using any of the following methods:

   - Double-click the setting.
   - Right-click the setting, and then select **Edit**.
   - Select the setting, and then select **Action** > **Edit**.

7. In the setting window that opens, select the required configuration \(for example, **Enabled** or **Disabled**\), and then select **OK**.

   Repeat these steps for each setting you want to configure.
8. Deploy the GPO to the devices you want to manage.

## Configure how locally and globally defined threat remediation and exclusions lists are merged

You can also control how locally and globally defined lists are merged. The local administrator merge behavior setting applies to the following features:

- [Exclusion lists](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure)
- [Specified remediation lists](https://learn.microsoft.com/en-us/defender-endpoint/configure-remediation-microsoft-defender-antivirus)
- [File and folder exclusions for attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#file-and-folder-exclusions-for-asr-rules)

By default, lists configured in Local Group Policy and the Windows Security app merge with lists from your deployed GPO. If the lists conflict, the deployed GPO takes precedence. You can disable local list merging so that only lists from management policies are used.

### Use Microsoft Intune to disable local list merging

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To disable local list merging in Microsoft Intune, use an endpoint security **Antivirus** policy. For detailed instructions, see [Create endpoint security policies](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#create-endpoint-security-policies) or [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: Go to **Manage** > **Antivirus** on the **Endpoint security \| Overview** page at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/overview](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), and then select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Create policy**.
- **Platform**: Select **Windows**.
- **Profile**: Select **Microsoft Defender Antivirus**.

When you create or modify the policy, use these specific settings on the **Configuration settings** tab:

- **Disable local admin merge**: Select **Disable local admin merge**.

For more information about antivirus policy profiles available in Microsoft Intune, see [Antivirus policy for endpoint security in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/antivirus).

### Use the Microsoft Defender portal to disable local list merging

If your organization [manages endpoint security policies in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure), use a Microsoft Defender Antivirus policy to disable local list merging.

For detailed instructions, see [Create an endpoint security policy](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure#create-an-endpoint-security-policy) or [Edit an endpoint security policy](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure#edit-an-endpoint-security-policy) \(links open new tabs\).

When you create the policy on the **Windows policies** tab of the **Endpoint security policies** page in the Defender portal at [https://security.microsoft.com/policy-inventory?osPlatform=Windows](https://security.microsoft.com/policy-inventory?osPlatform=Windows), use these specific settings:

- **Select platform**: Select **Windows**.
- **Select template**: Select **Microsoft Defender Antivirus**.

When you create or modify the policy, use this specific setting on the **Configuration settings** tab:

- **Disable local admin merge**: Select **Disable local admin merge**.

### Use Group Policy to disable local list merging

To disable local list merging by using Group Policy, follow these steps:

1. Open the [Group Policy Management Console \(GPMC\)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console) on your Group Policy management computer.
2. In the GPMC console tree, expand Group Policy Objects in the forest and domain containing the GPO you want to edit.
3. Right-click the GPO, and then select **Edit**.
4. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus**.
5. In the details pane of **Microsoft Defender Antivirus**, open the **Configure local administrator merge behavior for lists** setting by using any of the following methods:

   - Double-click the setting.
   - Right-click the setting, and then select **Edit**.
   - Select the setting, and then select **Action** > **Edit**.

6. In the setting window that opens, select **Disabled**, and then select **OK**.

Note

In the following administrative templates, set **Configure local administrator merge behavior for lists** to **Enabled** to disable the local administrator merge behavior:

- Administrative Templates \(.admx\) for Windows 11 2022 Update \(22H2\)
- Administrative Templates \(.admx\) for Windows 10 November 2021 Update \(21H2\)

Note

Disabling local list merging overrides controlled folder access settings. It also overrides any protected folders or allowed apps set by the local administrator. For more information about controlled folder access settings, see [Allow a blocked app in Windows Security](https://support.microsoft.com/Windows/Security/Threat-Malware-Protection/virus-and-threat-protection-in-the-windows-security-app).

## Related articles

See the following related articles:

- [Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/advanced-threat-protection-configure)
- [Microsoft Defender Antivirus in Windows](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)
- [Configure end-user interaction with Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus)
