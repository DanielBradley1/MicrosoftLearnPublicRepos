<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/prevent-end-user-interaction-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Prevent users from seeing or interacting with the Microsoft Defender Antivirus user interface

You can use Group Policy to prevent users on endpoints from seeing the Microsoft Defender Antivirus interface. You can also prevent them from pausing scans.

## Prerequisites

### Supported operating systems

This feature is supported on the following operating systems:

- Windows

## Hide the Microsoft Defender Antivirus interface

In Windows 10, versions 1703, hiding the interface hides Microsoft Defender Antivirus notifications and prevent the Virus & threat protection tile from appearing in the Windows Security app.

With the setting set to **Enabled**:

[![The Windows Security without the shield icon and virus and threat protection sections](https://learn.microsoft.com/en-us/defender/media/wdav-headless-mode-off-1703.png)](https://learn.microsoft.com/en-us/defender/media/wdav-headless-mode-off-1703.png#lightbox)

With the setting set to **Disabled** or not configured:

[![The Windows Security with shield icon and threat protection sections](https://learn.microsoft.com/en-us/defender/media/wdav-headless-mode-1703.png)](https://learn.microsoft.com/en-us/defender/media/wdav-headless-mode-1703.png#lightbox)

Note

Hiding the interface will also prevent Microsoft Defender Antivirus notifications from appearing on the endpoint. Microsoft Defender for Endpoint notifications will still appear. You can also individually [configure the notifications that appear on endpoints](https://learn.microsoft.com/en-us/defender-endpoint/configure-notifications-microsoft-defender-antivirus)

In earlier versions of Windows 10, the **Enable headless UI mode** setting hides the Windows Defender client interface. If the user attempts to open the Windows Defender client interface, they'll receive a warning that says, "Your system administrator has restricted access to this app."

[![The warning message when headless mode is enabled in Windows 10, versions earlier than 1703](https://learn.microsoft.com/en-us/defender/media/wdav-headless-mode-1607.png)](https://learn.microsoft.com/en-us/defender/media/wdav-headless-mode-1607.png#lightbox)

## Use Group Policy to hide the Microsoft Defender Antivirus interface from users

To hide the Microsoft Defender Antivirus interface by using Group Policy, perform the following steps:

1. On your Group Policy management machine, open the [Group Policy Management Console](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), right-click the Group Policy Object you want to configure and select **Edit**.
2. Using the **Group Policy Management Editor** go to **Computer configuration**.
3. Select **Administrative templates**.
4. Expand the tree to **Windows components > Microsoft Defender Antivirus > Client interface**.
5. Double-click the **Enable headless UI mode** setting and set the option to **Enabled**. Select **OK**.

See [Prevent users from locally modifying policy settings](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus) for other Microsoft Defender Antivirus policy settings that prevent users from modifying protection on their PCs.

## Prevent users from pausing a scan

You can prevent users from pausing scans, which can be helpful to ensure scheduled or on-demand scans aren't interrupted by users.

Note

The **Allow users to pause scan** setting is not supported on Windows 10.

### Use Group Policy to prevent users from pausing a scan

To prevent users from pausing a scan by using Group Policy, perform the following steps:

1. On your Group Policy management machine, open the [Group Policy Management Console](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), right-click the Group Policy Object you want to configure and select **Edit**.
2. Using the **Group Policy Management Editor** go to **Computer configuration**.
3. Select **Administrative templates**.
4. Expand the tree to **Windows components** > **Microsoft Defender Antivirus** > **Scan**.
5. Double-click the **Allow users to pause scan** setting and set the option to **Disabled**. Select **OK**.

## Use PowerShell to configure UI Lockdown mode

The `UILockdown` parameter indicates whether to disable UI Lockdown mode. If you specify a value of `$True`, Microsoft Defender Antivirus disables UI Lockdown mode. If you specify a value of `$False` or don't specify a value, UI Lockdown mode is enabled.

```powershell
PS C:\>Set-MpPreference -UILockdown $true
```

## Related articles

For more information, see the following articles:

- [Configure the notifications that appear on endpoints](https://learn.microsoft.com/en-us/defender-endpoint/configure-notifications-microsoft-defender-antivirus)
- [Configure end-user interaction with Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/configure-local-policy-overrides-microsoft-defender-antivirus)
- [Microsoft Defender Antivirus in Windows 10](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
