<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings-android -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Use custom settings for Android device administrator devices in Microsoft Intune

Using Microsoft Intune, you can add or create custom settings for your Android devices using a **custom profile**. Custom profiles are a feature in Intune. They're designed to add device settings and features that aren't built in to Intune.

This feature applies to:

- Android device administrator \(DA\)

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Android custom profiles use Open Mobile Alliance Uniform Resource Identifier \(OMA-URI\) settings to configure different features on Android devices. These settings are typically used by mobile device manufacturers to control these features.

Using a custom profile, you can configure and assign the following Android settings. The following settings aren't built in to Intune:

- [Create a Wi-Fi profile with a pre-shared key](https://learn.microsoft.com/en-us/intune/device-configuration/templates/create-wifi-preshared-key)
- [Create a per-app VPN profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-per-app-vpn-android)
- [Allow and block apps for Samsung Knox Standard devices](https://learn.microsoft.com/en-us/intune/device-configuration/templates/manage-apps-samsung-knox)
- [Configure web protection in Microsoft Defender for Endpoint for Android](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/configure-web-protection-android)

Important

Only the settings listed can be configured in a custom profile. Android devices don't expose a complete list of OMA-URI settings you can configure.

This article shows you how to create a custom profile for Android DA devices.

## Prerequisites

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following settings:

   - **Platform**: Select **Android device administrator**.
   - **Profile type**: Select **Custom**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **Android DA custom profile**.
   - **Description**: Enter a description for the profile. This setting is optional, but recommended.

6. Select **Next**.
7. In **Configuration settings** > **OMA-URI Settings**, select **Add**. Enter the following settings:

   - **Name**: Enter a unique name for the OMA-URI setting so you can easily find it.
   - **Description**: Enter a description that gives an overview of the setting, and any other important details.
   - **OMA-URI**: Enter the OMA-URI you want to use as a setting.
   - **Data type**: Select the data type for this OMA-URI setting. Your options:

     - String
     - String \(XML file\)
     - Date and time
     - Integer
     - Floating point
     - Boolean
     - Base64 \(file\)

   - **Value**: Enter the data value you want to associate with the OMA-URI you entered. The value depends on the data type you selected. For example, if you select **Date and time**, select the value from a date picker.

8. Select **Save** to save your changes. Continue to add more settings as needed. After you add some settings, you can select **Export**. **Export** creates a list of all the values you added in a comma-separated values \(.csv\) file.

   Select **Next**.
9. In **Scope tags** \(optional\) > **Select scope tags**, choose your scope tags to assign to the profile. For more information, see [Use role-based access control \(RBAC\) and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

   Select **Next**.
10. In **Assignments**, select the groups that will receive this profile. For more information on assigning profiles, see [Assign user and device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).

    Select **Next**.
11. In **Review + create**, when you're done, choose **Create**. The profile is created, and shown in the list.

    You can also [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
