<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-cloud-block-timeout-period-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Configure the Microsoft Defender Antivirus cloud block time-out period

When Microsoft Defender Antivirus finds a suspicious file, it can prevent the file from running while it queries the [Microsoft Defender Antivirus cloud service](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-microsoft-defender-antivirus).

By default, [Block at first sight](https://learn.microsoft.com/en-us/defender-endpoint/configure-block-at-first-sight-microsoft-defender-antivirus) blocks the file for 10 seconds while waiting for a cloud determination. You can add up to 50 seconds, for a maximum time-out period of 60 seconds. Before you begin, review the [prerequisites](#prerequisites) for this feature.

## Prerequisites

Before you specify an extended time-out period, enable [Block at first sight](https://learn.microsoft.com/en-us/defender-endpoint/configure-block-at-first-sight-microsoft-defender-antivirus), cloud protection, and automatic sample submission. Keep Microsoft Defender Antivirus up to date on the devices.

### Supported operating systems

The following operating systems support this feature:

- Windows
- Windows Server

  Note

  Windows Server supports this Microsoft Defender Antivirus setting when you configure it directly by using Microsoft Configuration Manager, Group Policy, or PowerShell. The Microsoft Intune and Microsoft Defender portal procedures in this article can manage supported Windows Server versions through [Defender for Endpoint security settings management](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure).

  To onboard and manage servers through Defender for Endpoint, you need an eligible server license. If your organization accesses Defender for Endpoint only through Defender for Servers, you also need at least one active Defender for Endpoint user subscription license to use security settings management. For more information, see [Server plans](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#server-plans) and [Licensing and subscriptions for security settings management](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/security-settings-management#licensing-and-subscriptions).

## Specify the extended time-out period using Microsoft Intune

Microsoft Intune is the recommended tool for configuring and distributing Defender for Endpoint features to devices. However, Intune is a separate product that isn't part of Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. If you don't have Intune, you can use any of the other methods in this article. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

To specify the cloud block time-out period in Microsoft Intune, use an endpoint security **Antivirus** policy. For detailed instructions, see [Create endpoint security policies](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#create-endpoint-security-policies) or [Modify existing policies](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#modify-existing-policies) \(links open new tabs in the Intune documentation\).

When you create the policy, use these specific settings:

- **Policy type**: Go to **Manage** > **Antivirus** on the **Endpoint security \| Overview** page at [https://intune.microsoft.com/#view/Microsoft\_Intune\_Workflows/SecurityManagementMenu/~/overview](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), and then select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Create policy**.
- **Platform**: Select **Windows**.
- **Profile**: Select **Microsoft Defender Antivirus**.

When you create or modify the policy, use these specific settings on the **Configuration settings** tab:

- Slide the toggle for **Cloud Extended Timeout** to ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **Configured**.
- In the box that appears, specify a value from 0 to 50 seconds. The value is added to the default 10-second time-out period. For example, enter `50` for a total time-out period of 60 seconds.

## Specify the extended time-out period using the Microsoft Defender portal

If your organization [manages endpoint security policies in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure), you specify the cloud block time-out period with the same endpoint security policies that Intune uses.

For detailed instructions, see [Create an endpoint security policy](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure#create-an-endpoint-security-policy) or [Edit an endpoint security policy](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure#edit-an-endpoint-security-policy) \(links open new tabs\).

When you create the policy on the **Windows policies** tab of the **Endpoint security policies** page in the Defender portal at [https://security.microsoft.com/policy-inventory?osPlatform=Windows](https://security.microsoft.com/policy-inventory?osPlatform=Windows), use these specific settings:

- **Select platform**: Select **Windows**.
- **Select template**: Select **Microsoft Defender Antivirus**.

When you create or modify the policy, use these specific settings on the **Configuration settings** tab:

- Slide the toggle for **Cloud Extended Timeout** to ![](https://learn.microsoft.com/en-us/defender-endpoint/media/toggle-on.png) **Configured**.
- In the box that appears, specify a value from 0 to 50 seconds. The value is added to the default 10-second time-out period. For example, enter `50` for a total time-out period of 60 seconds.

## Specify the extended time-out period using Microsoft Configuration Manager

For instructions to create and deploy an antimalware policy, see [Endpoint Protection antimalware policies in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-antimalware-policies).

In the **Cloud Protection Service** settings of the antimalware policy, configure **Allow extended cloud check to block and scan for up to \(seconds\)**. Enter a value from `0` to `50`. The value is added to the default 10-second time-out period.

## Specify the extended time-out period using Group Policy

You can use Group Policy to specify an extended time-out period for cloud checks.

1. In Centralized Group Policy, open the [Group Policy Management Console \(GPMC\)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console) on your Group Policy management computer.
2. In the GPMC console tree, expand Group Policy Objects in the forest and domain containing the GPO you want to edit.
3. Right-click the GPO, and then select **Edit**.
4. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **MpEngine**.

   Note

   Group Policy paths before Windows 10, version 2004 \(May 2020\) might use *Windows* Defender Antivirus instead of *Microsoft* Defender Antivirus. Both names refer to the same policy location.
5. In the details pane of **MpEngine**, open the **Configure extended cloud check** setting. To open the setting, use any of the following methods:

   - Double-click the setting.
   - Right-click the setting, and then select **Edit**.
   - Select the setting, and then select **Action** > **Edit**.

6. In the setting window that opens, select **Enabled**.
7. In the **Options** section, for **Specify the extended cloud check time in seconds**, enter the extra time that Defender Antivirus prevents the file from running while waiting for a cloud determination. Enter a value from `0` to `50`. The value is added to the default 10-second time-out period.
8. Select **OK**.

Tip

You can also configure Group Policy locally on individual devices by using the Local Group Policy Editor \(`gpedit.msc`\). Navigate to the same path: **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **MpEngine**.

## Specify the extended time-out period using PowerShell

In an elevated PowerShell session \(a PowerShell window you opened by selecting **Run as administrator**\), replace <0-50> with an integer from 0 to 50, and then run the following command:

```powershell
Set-MpPreference -CloudExtendedTimeout <0-50>
```

For example, the following command adds 50 seconds to the default 10-second period, for a total of 60 seconds:

```powershell
Set-MpPreference -CloudExtendedTimeout 50
```

For detailed syntax and parameter information, see [Set-MpPreference](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference).

## Related content

For information about Microsoft Defender Antivirus and Defender for Endpoint on other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
