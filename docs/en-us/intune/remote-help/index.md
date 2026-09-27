<!-- Source: https://learn.microsoft.com/en-us/intune/remote-help/ -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Use Remote Help with Microsoft Intune

Microsoft Intune Remote Help is a cloud-based remote support solution that allows IT support teams to connect securely to an end-user's device for real-time assistance. It enables organizations to provide remote troubleshooting and guidance with enterprise security controls in place. Remote Help distinguishes between helpers \(support personnel\) and sharers \(end users sharing their screen\), both of whom must sign in with corporate Entra ID accounts for each session. This requirement means Remote Help only works within your organization's tenant – helpers can't assist users in another tenant or external organization.

## Remote Help capabilities

The Remote Help app supports the following capabilities in general across the supported platforms.

- **Enable Remote Help for your tenant**: By default, Remote Help isn't enabled for Intune tenants. If you choose to turn on Remote Help, its use is enabled tenant-wide. Remote Help must be enabled before users can be authenticated through your tenant when using Remote Help.

  [![A screenshot of the tenant administration screen where you can enable Remote Help.](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-enable.png)](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-enable-expanded.png#lightbox)
- **Requires Organization login**: To use Remote Help, both the helper and the sharer must sign in with a Microsoft Entra account from your organization. You can't use Remote Help to assist users who aren't members of your organization.

  ![Screenshot of Remote Help requiring an organizational account.](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-organizational-account.png)
- **Compliance Warnings**: Before a helper connects to a user's device, helpers see a noncompliance warning about that device if it's not compliant with its assigned policies.
- **Role-based access control**: Admins can set RBAC rules that determine the scope of a helper's access, such as:

  - The users who can help others and the range of actions they can do while providing help. For example, who can run elevated privileges while helping.
  - The users who can only view a device, and who can request full control of the session while assisting others.

- **Monitor active Remote Help sessions, and view details about past sessions**: In the Microsoft Intune admin center, you can view reports that include details about who helped who, on what device, and for how long. You can also find details about active sessions. An administrator can also reference audit log sessions created for Remote Help in Intune under **Tenant Administration** > **Audit Logs**.

  For unenrolled devices, auditing the Remote Help sessions is limited.
- **Web app for sharers** - In situations where the Sharer needs assistance but is unable to install the native application for macOS or Windows, the Sharer can use the Web App to share their screen to a helper. This web app provides view only capabilities to the helper, allowing them to guide the user through resolving issues.

## Platform-specific capabilities

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/windows.svg)](#tabpanel_1_windows)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/macos.svg)](#tabpanel_1_macos)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/android.svg)](#tabpanel_1_android)

- **Elevation**: Allows helpers to enter UAC credentials when prompted on the sharer's device. Enabling elevation also allows the helper to view and control the sharer's device when the sharer grants the helper access.

  [![Screenshot of the prompt to enable elevation support during a remote help session on Windows.](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-windows-elevation.png)](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-windows-elevation-expanded.png#lightbox)
- **Remote launch**: Allows helpers to launch Remote Help on the helper and sharer's device from Intune by sending a notification to the sharer's device.

  ![A screenshot of the sharer's computer showing the prompt to start a Remote Help session using the Remote Launch feature.](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-windows-remote-launch.png)
- **Unattended control: Remote sign-in**: Allows an authorized helper to sign in to a corporate Windows device with their own credentials and troubleshoot without requiring an end user to be present or signed in. Unlike attended control, which displays an active user's session, unattended remote sign-in creates a separate authenticated Windows session governed by user authentication, Intune role-based access control \(RBAC\), and auditing. This capability is initiated from the Microsoft Intune admin center and applies only to physical, corporate-owned, Intune-managed Windows devices.

  [![Screenshot of the Remote Help control session type dialog with unattended control selected.](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-unattended-windows.png)](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-unattended-windows.png#lightbox)
- **Optional support for unenrolled devices**: This setting is turned off by default. Enabling this option allows help to be provided to devices that aren't enrolled in Intune. This setting doesn't apply to devices used by helpers or to unattended control, which supports only Intune-enrolled devices.

  ![A screenshot of the option to enable unenrolled devices](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-unenrolled.png)
- **Conditional access support**: You can use Conditional Access policies to control how helpers and sharers access Remote Help. For example, you can require multifactor authentication \(MFA\) for helpers or restrict access to specific locations or compliant devices. These policies apply to Remote Help sessions that are accepted by an end user, who participates in the session, and don't apply to unattended access.
- **Chat functionality**: Remote Help includes enhanced chat that maintains a continuous thread of all messages. This chat supports special characters and other languages including Chinese and Arabic. Chat functionality applies to Remote Help sessions that are accepted by an end user, who participates in the session, and doesn't apply to unattended access. For more information, see [Supported languages for chat](https://learn.microsoft.com/en-us/intune/remote-help/plan#supported-languages-for-chat).
- **Web app for sharers** - In situations where the Sharer needs assistance but is unable to install the native application for macOS, the Sharer can use the Web App to share their screen to a helper. This web app provides view only capabilities to the helper, allowing them to guide the user through resolving issues.

- **Conditional access support**: You can use Conditional Access policies to control how helpers and sharers access Remote Help. For example, you can require multifactor authentication \(MFA\) for helpers or restrict access to specific locations or compliant devices.
- **Chat functionality**: Remote Help includes enhanced chat that maintains a continuous thread of all messages. This chat supports special characters and other languages including Chinese and Arabic. For more information on languages supported, see [Languages Supported](https://learn.microsoft.com/en-us/intune/remote-help/plan#supported-languages-for-chat).
- **Optional support for unenrolled devices**: This setting is turned off by default. For Windows and macOS devices, enabling this option allows help to be provided to devices that aren't enrolled in Intune. This setting doesn't apply to devices used by helpers.

  ![A screenshot of the opion to enable unenrolled devices](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-unenrolled.png)

- **Unattended control**: Helpers can connect to Android devices without requiring the sharer to accept the connection each time. This capability requires the Android device to be enrolled in Intune as an Android Enterprise dedicated device.

  [![Screenshot of an unattended Remote Help session on Android](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-android-unattended.png)](https://learn.microsoft.com/en-us/intune/remote-help/media/index/remote-help-android-unattended-expanded.png#lightbox)

## Demos and Videos

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/windows.svg)](#tabpanel_2_windows)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/macos.svg)](#tabpanel_2_macos)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/android.svg)](#tabpanel_2_android)

The [Remote Help](https://regale.cloud/Microsoft/viewer/1746/remote-help/index.html#/0/0) interactive demo walks you through scenarios step-by-step with interactive annotations and navigation controls.

Use the interactive demos to explore Remote Help on macOS:

- [macOS native experience](https://regale.cloud/microsoft/play/1746/remote-help#/7/0)
- [macOS web app experience](https://regale.cloud/microsoft/play/1746/remote-help#/6/0)

Check back in this space for demos and videos of Remote Help for Android.

## Next Steps

[Next: Plan Remote Help >](https://learn.microsoft.com/en-us/intune/remote-help/plan)
