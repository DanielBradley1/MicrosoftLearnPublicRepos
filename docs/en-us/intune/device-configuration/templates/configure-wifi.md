<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Add and use Wi-Fi settings on your devices in Microsoft Intune

Important

On October 22, 2022, Microsoft Intune ended support for devices running Windows 8.1. Technical assistance and automatic updates on these devices aren't available.

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Wi-Fi is a wireless network that's used by many mobile devices to get network access. Microsoft Intune includes built-in Wi-Fi settings that can be deployed to users and devices in your organization. This group of settings is called a **profile**, and can be assigned to different users and groups. Once assigned, your users get access your organization's Wi-Fi network without configuring it themselves.

For example, you install a new Wi-Fi network named Contoso Wi-Fi. You then want to set up all iOS/iPadOS devices to connect to this network. Here's the process:

1. You create a Wi-Fi profile that includes the settings that connect to the Contoso Wi-Fi wireless network.
2. You assign the profile to a group that includes all users of iOS/iPadOS devices.
3. Users find the new Contoso Wi-Fi network in the list of wireless networks on their devices. They can then connect to the network, using the authentication method of your choosing.

This article lists the steps to create a Wi-Fi profile. It also includes links that describe the different settings for each platform.

## Before you begin

- To create a Wi-Fi profile, you need to know the settings for your Wi-Fi network, including the SSID \(service set identifier\), security type, and more.
- To configure the Wi-Fi policy, at a minimum, sign in to the Intune admin center with the **Policy and Profile manager** role. For information on the built-in roles in Intune, and what they can do, go to [Role-based access control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).
- Wi-Fi profiles support the following device platforms:

  - Android device administrator
  - Android Enterprise and kiosk
  - Android \(AOSP\)
  - iOS/iPadOS
  - macOS
  - Windows
  - Windows Holographic for Business


  For specific versions, go to [Supported operating systems and browsers in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

   - **Platform**: Select the platform of your devices. Your options:

     - **Android device administrator**
     - **Android \(AOSP\)**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows 10 and later**
     - **Windows 8.1 and later**

   - **Profile type**: Select **Wi-Fi**. Or, select **Templates** > **Wi-Fi**.

     Tip

     - For **Android Enterprise** devices running as a dedicated device \(kiosk\), select **Fully Managed, Dedicated, and Corporate-Owned Work Profile** > **Wi-Fi**.
     - For **Windows 8.1 and newer**, you can choose **Wi-Fi import**. This option lets you import Wi-Fi settings as an XML file that you previously exported from a different device.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **WiFi profile for entire company**.
   - **Description**: Enter a description for the profile. This setting is optional, but recommended.

6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Select your platform for detailed settings:

   - [Android](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-android-enterprise), including dedicated devices
   - [iOS/iPadOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-apple)
   - [macOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-apple)
   - [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-windows)
   - [Windows 8.1 and newer](https://learn.microsoft.com/en-us/intune/device-configuration/templates/import-wifi-settings-windows), including Windows Holographic for Business
   - [Android device administrator](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-android)

8. Select **Next**.
9. In **Scope tags** \(optional\), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use RBAC and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

   Select **Next**.
10. In **Assignments**, select the user or groups that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

Tip

If you use certificate based authentication for your Wi-Fi profile, deploy the Wi-Fi profile, certificate profile, and trusted root profile to the same groups. This step makes sure that each device can recognize the legitimacy of your certificate authority. For more information, go to [How to configure certificates with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview).

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- [Troubleshoot Wi-Fi profiles in Intune](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/troubleshoot-wi-fi-profiles).
