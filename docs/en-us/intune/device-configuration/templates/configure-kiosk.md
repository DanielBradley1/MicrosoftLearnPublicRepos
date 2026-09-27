<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-kiosk -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Windows and Windows Holographic for Business device settings to run as a dedicated kiosk using Intune

On Windows devices, use Intune to run devices as a kiosk, sometimes known as a dedicated device. A device in kiosk mode can run one app, or run many apps. You can show and customize a start menu, add different apps, including Win32 apps, add a specific home page to a web browser, and more.

This scenario is common for frontline workers \(FLW\). For more information on FLW devices in Microsoft Intune, go to [FLW device management for devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/solutions/frontline-worker/).

This feature applies to:

- Windows
- Windows Holographic for Business

To create kiosk profiles for other platforms, go to:

- [Android device administrator](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android#kiosk)
- [Android Enterprise](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise) \(Device experience\)
- [iOS/iPadOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-apple)

Intune supports one kiosk profile per device. If you need multiple kiosk profiles on a single device, you can use a [Custom OMA-URI](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings-windows).

Intune uses configuration profiles to create and customize these settings for your organization's needs. After you add these features in a profile, assign or deploy these settings to groups in your organization.

This article shows you how to run one app or many apps as a Windows kiosk device using a device configuration profile. For a list of all the settings, and what they do, go to [Windows client kiosk settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows) and [Windows Holographic for Business kiosk settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows-holographic).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

   - **Platform**: Select **Windows 10 and later**.
   - **Profile type**: Select **Templates** > **Kiosk**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the new profile.
   - **Description**: Enter a description for the profile. This setting is optional, but recommended.

6. Select **Next**.
7. In **Configuration settings** > **Select a kiosk mode**, choose the type of kiosk mode supported by the policy. Options include:

   - **Not Configured** \(default\): Intune doesn't change or update this setting. The policy doesn't enable kiosk mode.
   - **Single app, full-screen kiosk**: The device runs as a single user account, and locks it to a single web browser or app. So when the user signs in, a specific app starts. This mode also restricts users from opening new apps, or changing the running app.

     For example, you can run the Microsoft Edge browser, and only show one site, such as `Contoso.com`. Or, you can run a Store app, and have the device locked on this app.
   - **Multi app kiosk**: The device runs multiple Store apps, Win32 apps, web browsers, or inbox Windows apps by using the Application User Model ID \(AUMID\). Only the apps you add are available on the device.

     The benefit of a multi-app kiosk, or fixed-purpose device, is to provide an easy-to-understand experience for users by only accessing apps they need. And, also removing from their view the apps they don't need.

     Note

     Currently, you can use Intune to configure a multi-app kiosk on Windows 10 devices. For more information about Windows 11 multi-app kiosk support, go to [Set up a multi-app kiosk on Windows 11 devices](https://learn.microsoft.com/en-us/windows/configuration/lock-down-windows-11-to-specific-apps).

     On October 14, 2025, [Windows 10 reached end of support](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.


   For a list of all settings, and what they do, go to:


   - [Windows client kiosk settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows)
   - [Windows Holographic for Business kiosk settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows-holographic)

8. Select **Next**.
9. In **Scope tags** \(optional\), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use RBAC and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

   Select **Next**.
10. In **Assignments**, select the users or user group that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in, the policy is applied.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- You can create kiosk profiles for devices that run the following platforms:

  - [Android device administrator](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android#kiosk)
  - [Android Enterprise](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise) \(Device experience\)
  - [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows)
  - [Windows Holographic for Business](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows-holographic)
