<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows-holographic -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Windows Holographic for Business device settings to run as a kiosk in Intune

On Windows Holographic for Business devices, you can configure the devices to run in single-app kiosk mode or mult-app kiosk mode. Some features aren't supported on Windows Holographic for Business.

This article describes the different settings you can control on Windows Holographic for Business devices. As part of your mobile device management \(MDM\) solution, use these settings to configure your Windows Holographic for Business devices to run in kiosk mode.

As an Intune administrator, you can create and assign these settings to your devices.

To learn more about the Windows kiosk feature in Intune, see [configure kiosk settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-kiosk).

## Before you begin

- [Create a Windows kiosk device configuration profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-kiosk#create-the-profile).

  When you create a Windows client kiosk device configuration profile, you see more settings than what's listed in this article. Windows Holographic for Business devices support the settings listed in this article.

  Important

  On October 14, 2025, [Windows 10 reached end of support](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.
- This kiosk profile is directly related to the device restrictions profile you create by using the [Microsoft Edge kiosk settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-windows-holographic#microsoft-edge-browser). To summarize:

  1. Create this kiosk profile to run the device in kiosk mode.
  2. Create the [device restrictions profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-windows-holographic#microsoft-edge-browser), and configure specific features and settings allowed in Microsoft Edge.

- Assign this kiosk profile to the same devices as your [Microsoft Edge profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-windows-holographic#microsoft-edge-browser).

## Single app, full-screen kiosk

Runs only one app on the device. When the user signs in, a specific app starts. This mode also restricts the user from opening new apps or changing the running app.

- **User logon type**: Select the account type that runs the app. Your options:

  - **Not configured**: Intune doesn't change or update this setting.
  - **Auto logon \(Windows 10, version 1803 and later, or Windows 11\)**: Not supported on Windows Holographic for Business.
  - **Local user account**: Enter the local \(to the device\) user account. Or, enter a Microsoft Account \(MSA\) account associated with the kiosk app. The account you enter signs in to the kiosk.

    For kiosks in public-facing environments, use a user type with the least privilege.

- **Application type**: Select **Add Store app**.

  - **App to run in kiosk mode**: Select an app from the list.

    Don't see any apps listed? Add some by using the steps at [Client Apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/).

## Multi-app kiosk

Apps in this mode appear on the Start menu. These apps are the only apps the user can open. If an app depends on another app, include both apps in the allowed apps list.

- **Target devices running Windows 10/11 in S mode devices**: Select **No**. S mode isn't supported on Windows Holographic for Business.
- **User logon type**: Add one or more user accounts that can use the apps you add. Your options:

  - **Not configured**: Intune doesn't change or update this setting.
  - **Auto logon \(Windows 10 version 1803 and later, or Windows 11\)**: Not supported on Windows Holographic for Business.
  - **Local user accounts**: Enter the local \(to the device\) user account. The account you enter signs in to the kiosk.
  - **Microsoft Entra user or group \(Windows 10, version 1803 and later, or Windows 11\)**: Requires user credentials to sign in to the device. Select **Add** to choose Microsoft Entra users or groups from the list. You can select multiple users and groups. Choose **Select** to save your changes.
  - **HoloLens visitor**: The visitor account is a guest account that doesn't require any user credentials or authentication, as described in [shared PC mode concepts](https://learn.microsoft.com/en-us/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Browser and Applications**: Add the apps to run on the kiosk device. You can add several apps.

  - **Browsers**

    - **Add Microsoft Edge**: Microsoft Edge is added to the app grid, and all applications can run on this kiosk. Select the Microsoft Edge kiosk mode type:

      - **Normal mode \(full version of Microsoft Edge\)**: Runs a full-version of Microsoft Edge with all browsing features. User data and state are saved between sessions.
      - **Public browsing \(InPrivate\)**: Runs a multitab version of Microsoft Edge InPrivate with a tailored experience for kiosks that run in full-screen mode.


      For more information on these options, see [Deploy Microsoft Edge kiosk mode](https://learn.microsoft.com/en-us/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).


      Note


      This setting enables the Microsoft Edge browser on the device. To configure Microsoft Edge-specific settings, in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), create a device restrictions profile \(**Devices** > **Manage devices** > **Configuration** > **Create** > **New policy** > **Windows 10 and later** for platform > **Templates** > **Device Restrictions** > **Microsoft Edge Browser**\). [Microsoft Edge browser](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-windows-holographic#microsoft-edge-browser) describes the available Holographic for Business settings.

    - **Add Kiosk browser**: Not supported on Windows Holographic for Business.

  - **Applications**

    - **Add store app**: Select an existing app you added or deployed to Intune as [Client Apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/), including LOB apps. If you don't have any apps listed, Intune supports many [app types](https://learn.microsoft.com/en-us/intune/app-management/deployment/) that you [add to Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-microsoft-store-legacy).
    - **Add Win32 app**: Not supported on Windows Holographic for Business.
    - **Add by AUMID**: Use this option to add inbox Windows apps, like Notepad or Calculator. Enter the following properties:

      - **Application name**: Required. Enter a name for the application.
      - **Application user model ID \(AUMID\)**: Required. Enter the Application user model ID \(AUMID\) of the Windows app. To get this ID, see [find the Application User Model ID of an installed app](https://learn.microsoft.com/en-us/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

    - **AutoLaunch**: Optional. After you add your apps and browser, select one app or browser to automatically open when the user signs in. Only a single app or browser can be autolaunched.
    - **Tile size**: Required. After you add your apps, select a Small, Medium, Wide, or Large app tile size.

- **Use alternative Start layout**: Select **Yes** to enter an XML file that describes how the apps appear on the Start menu, including the order of the apps. Use this option if you require more customization in your Start menu. [Customize and export start layout](https://learn.microsoft.com/en-us/hololens/hololens-kiosk#start-layout-for-hololens) provides some guidance, and includes a specific XML file for Windows Holographic for Business devices.
- **Windows Taskbar**: Not supported on Windows Holographic for Business.
- **Allow Access to Downloads Folder**: Not supported on Windows Holographic for Business.
- **Specify Maintenance Window for App Restarts**: Not supported on Windows Holographic for Business.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- Create kiosk profiles for [Android Enterprise](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise) \(Device experience\) and [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows) devices.
