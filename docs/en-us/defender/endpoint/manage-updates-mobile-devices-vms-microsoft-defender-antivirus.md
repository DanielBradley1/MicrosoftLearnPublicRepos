<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-updates-mobile-devices-vms-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# Manage updates for mobile devices and virtual machines \(VMs\)

This article explains how to configure Microsoft Defender Antivirus update settings for mobile devices and virtual machines \(VMs\) to reduce performance impact during updates. Mobile devices and VMs may require more configuration to ensure performance is not impacted by updates.

For Microsoft Defender Antivirus, two update-related settings are especially useful for mobile devices and VMs:

- Opt in to Microsoft Update on mobile computers without a WSUS connection
- Prevent Security intelligence updates when running on battery power

The following articles may also be useful in these situations:

- [About scheduled scans](https://learn.microsoft.com/en-us/defender-endpoint/schedule-antivirus-scans)
- [Manage updates for endpoints that are out of date](https://learn.microsoft.com/en-us/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus)
- [Deployment guide for Microsoft Defender Antivirus in a virtual desktop infrastructure \(VDI\) environment](https://learn.microsoft.com/en-us/defender-endpoint/deployment-vdi-microsoft-defender-antivirus)

## Prerequisites

Before you configure the update settings described in this article, make sure your environment meets the following requirements.

### Supported operating systems

The following operating systems are supported:

- Windows

## Opt in to Microsoft Update on mobile computers without a WSUS connection

You can use Microsoft Update to keep Security intelligence on mobile devices running Microsoft Defender Antivirus up to date when they are not connected to the corporate network or don't otherwise have a WSUS connection.

Opting in to Microsoft Update means that protection updates can be delivered to devices \(via Microsoft Update\) even if you have set WSUS to override Microsoft Update.

You can opt in to Microsoft Update on the mobile device in one of the following ways:

- Change the setting with Group Policy.
- Use a VBScript to create a script, then run it on each computer in your network.
- Manually opt in every computer on your network through the **Settings** menu.

### Use Group Policy to opt in to Microsoft Update

Perform the following steps to enable Microsoft Update by using Group Policy:

1. In Centralized Group Policy, open the [Group Policy Management Console \(GPMC\)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console) on your Group Policy management computer.
2. In the GPMC console tree, expand Group Policy Objects in the forest and domain containing the GPO you want to edit.
3. Right-click the GPO, and then select **Edit**.
4. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Security Intelligence Updates**.

   Note

   Group Policy paths before Windows 10, version 2004 \(May 2020\) might use *Windows* Defender Antivirus instead of *Microsoft* Defender Antivirus. Group Policy paths before Windows 10, version 1909 \(November 2019\) might use *Signature Updates* instead of *Security Intelligence Updates*. The older and newer names refer to the same policy locations.
5. In the details pane of **Security Intelligence Updates**, open the **Allow security intelligence updates from Microsoft Update** setting. To open the setting, use any of the following methods:

   - Double-click the setting.
   - Right-click the setting, and then select **Edit**.
   - Select the setting, and then select **Action** > **Edit**.

6. In the setting window that opens, select **Enabled**, and then select **OK**.

Tip

You can also configure Group Policy locally on individual devices by using the Local Group Policy Editor \(`gpedit.msc`\). Navigate to the same path: **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Security Intelligence Updates**.

### Use a VBScript to opt in to Microsoft Update

Use the following process to create and run a VBScript that opts devices in to Microsoft Update:

1. Use the instructions in the MSDN article [Opt-In to Microsoft Update](https://learn.microsoft.com/en-us/windows/win32/wua_sdk/opt-in-to-microsoft-update) to create the VBScript.
2. Run the VBScript you created on each computer in your network.

### Manually opt in to Microsoft Update

To manually opt a device in to Microsoft Update, complete the following steps:

1. Open **Windows Update** in **Update & security** settings on the computer you want to opt in.
2. Select **Advanced** options.
3. Select the checkbox for **Give me updates for other Microsoft products when I update Windows**.

## Prevent Security intelligence updates when running on battery power

You can configure Microsoft Defender Antivirus to only download protection updates when the PC is connected to a wired power source.

### Use Group Policy to prevent security intelligence updates on battery power

Perform the following steps to prevent security intelligence updates when devices are running on battery power:

1. In Centralized Group Policy, open the [Group Policy Management Console \(GPMC\)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-management-console) on your Group Policy management computer.
2. In the GPMC console tree, expand Group Policy Objects in the forest and domain containing the GPO you want to edit.
3. Right-click the GPO, and then select **Edit**.
4. In the **Group Policy Management Editor**, go to **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Security Intelligence Updates**.

   Note

   Group Policy paths before Windows 10, version 2004 \(May 2020\) might use *Windows* Defender Antivirus instead of *Microsoft* Defender Antivirus. Group Policy paths before Windows 10, version 1909 \(November 2019\) might use *Signature Updates* instead of *Security Intelligence Updates*. The older and newer names refer to the same policy locations.
5. In the details pane of **Security Intelligence Updates**, open the **Allow security intelligence updates when running on battery power** setting. To open the setting, use any of the following methods:

   - Double-click the setting.
   - Right-click the setting, and then select **Edit**.
   - Select the setting, and then select **Action** > **Edit**.

Tip

You can also configure Group Policy locally on individual devices by using the Local Group Policy Editor \(`gpedit.msc`\). Navigate to the same path: **Computer configuration** > **Administrative templates** > **Windows components** > **Microsoft Defender Antivirus** > **Security Intelligence Updates**.

1. In the setting window that opens, select **Disabled**, and then select **OK**.

Disabling **Allow security intelligence updates when running on battery power** prevents protection updates from downloading when the PC is on battery power.

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

## Related articles

The following articles provide related guidance:

- [Manage Microsoft Defender Antivirus updates and apply baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates)
- [Update and manage Microsoft Defender Antivirus in Windows 10](https://learn.microsoft.com/en-us/defender-endpoint/deploy-manage-report-microsoft-defender-antivirus)
