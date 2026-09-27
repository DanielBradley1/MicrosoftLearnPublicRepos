<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-enterprise-sso-plugin-macos -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Use the Microsoft Enterprise SSO plug-in on macOS devices

The [Microsoft Enterprise SSO plug-in](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin) is a feature in Microsoft Entra ID that provides single sign-on \(SSO\) features for Apple devices. This plug-in uses the Apple single sign-on app extension framework.

- For iOS/iPadOS devices, the Enterprise SSO plug-in includes the **SSO app extension**.
- For macOS devices, the Enterprise SSO plug-in includes **[Platform SSO and the SSO app extension](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-macos)**.

The **SSO app extension** provides single sign-on to apps and websites that use Microsoft Entra ID for authentication, including Microsoft 365 apps. It reduces the number of authentication prompts users get when using devices managed by Mobile Device Management \(MDM\), including any MDM that supports configuring SSO profiles.

This feature applies to:

- macOS

  For iOS/iPadOS, go to [Use the Microsoft Enterprise SSO plug-in on iOS/iPadOS devices](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-enterprise-sso-plugin-ios).

On macOS devices, you can configure SSO app extension settings in two places in Intune:

- **Device features template** \(**this article**\) - This option configures only the SSO app extension and uses your MDM provider, like Intune, to deploy the settings to devices.

  Use this article if you only want to configure the SSO app extension settings and don't want to also configure Platform SSO.
- **[Settings Catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-macos)** - This option configures Platform SSO and the SSO app extension together. You use Intune to deploy the settings to your devices.

  Use the settings catalog settings if you want to configure both the Platform SSO and SSO app extension settings. For more information, go to [Configure platform SSO for macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-macos).

For an overview of your SSO options on Apple devices, go to [SSO overview and options for Apple devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/enterprise-sso-plugin).

This article shows how to create an SSO app extension configuration policy for macOS Apple devices with Intune, Jamf Pro, and other MDM solutions.

If you want to configure Platform SSO and SSO app extension settings together, then go to [Configure platform SSO for macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-macos).

## App support

For your apps to use the Microsoft Enterprise SSO plug-in, you have two options:

- **Option 1 - MSAL**: Apps that support the [Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview) automatically take advantage of the Microsoft Enterprise SSO plug-in. For example, Microsoft 365 apps support MSAL. So, they automatically use the plug-in.

  If your organization creates its own apps, then your app developer can add a dependency to the MSAL. This dependency enables your app to use the Microsoft Enterprise SSO plug-in.

  For a sample tutorial, go to [Tutorial: Sign in users and call Microsoft Graph from an iOS or macOS app](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-v2-ios).
- **Option 2 - AllowList**: Apps that don't support or weren't developed with MSAL can use the SSO app extension. These apps include browsers like Safari and apps that use Safari web view APIs.

  For these non-MSAL apps, add the application bundle ID or prefix to the extension configuration in your Intune SSO app extension policy \(in this article\).

  For example, to allow a Microsoft app that doesn't support MSAL, add `com.microsoft.` to the **AppPrefixAllowList** property in your Intune policy. Be careful with the apps you allow, they can bypass interactive sign-in prompts for the signed in user.

  For more information, go to [Microsoft Enterprise SSO plug-in for Apple devices - apps that don't use MSAL](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#applications-that-dont-use-msal).

## Prerequisites

To use the Microsoft Enterprise SSO plug-in on macOS devices:

- [Intune](#tabpanel_1_prereq-intune)
- [Jamf Pro](#tabpanel_1_prereq-jamf-pro)
- [Other MDMs](#tabpanel_1_prereq-other-mdm)

- The device is MDM managed by Intune.
- The device must support the plug-in:

  - macOS 10.15 and newer

- The Microsoft Company Portal app must be installed and configured on the device.
- The Enterprise SSO plug-in requirements are configured, including the [Apple network configuration URLs](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#requirements).

- The device is managed by Jamf Pro.
- The device must support the plug-in:

  - macOS 10.15 and newer

- The Microsoft Company Portal app must be installed on the device.

  Users can install the Company Portal app manually. Or, admins can deploy the app using Jamf Pro. For a list of options on how to install the Company Portal app, go to [Package Management - Adding a Package to Jamf Admin](https://learn.jamf.com/bundle/jamf-pro-documentation-current/page/Package_Management.html#ariaid-title4) \(opens Jamf Pro's web site\).

  Note

  On macOS devices, Apple requires the Company Portal app be installed. Users don't need to use or configure the Company Portal app, it just needs to be installed on the device.
- The Enterprise SSO plug-in requirements are configured, including the [Apple network configuration URLs](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#requirements).

- The device is managed by a mobile device management \(MDM\) provider solution.
- The MDM solution must support configuring the [Single Sign-on MDM payload settings for Apple devices](https://support.apple.com/guide/deployment/extensible-single-sign-on-payload-settings-depfd9cdf845/web) \(opens Apple's web site\) with a device policy.
- The device must support the plug-in:

  - macOS 10.15 and newer

- The Microsoft Company Portal app must be installed on the device.

  Users can install the Company Portal app manually. Or, admins can deploy the app using an MDM policy. You can [download the Company Portal app installer package](https://go.microsoft.com/fwlink/?linkid=853070).

  Note

  On macOS devices, Apple requires the Company Portal app be installed. Users don't need to use or configure the Company Portal app, it just needs to be installed on the device.
- The Enterprise SSO plug-in requirements are configured, including the [Apple network configuration URLs](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#requirements).

## Microsoft Enterprise SSO plug-in vs. Kerberos SSO extension

When you use the SSO app extension, you use the **SSO** or **Kerberos** Payload Type for authentication. The SSO app extension is designed to improve the sign-in experience for apps and websites that use these authentication methods.

The Microsoft Enterprise SSO plug-in uses the **SSO** Payload Type with **Redirect** authentication. The SSO Redirect and Kerberos extension types can both be used on a device at the same time. Be sure to create separate device profiles for each extension type you plan to use on your devices.

To determine the correct SSO extension type for your scenario, use the following table:

---

| Microsoft Enterprise SSO plug-in for Apple Devices | Single sign-on app extension with Kerberos |
| --- | --- |
| Uses the **Microsoft Entra ID** SSO app extension type | Uses the **Kerberos** SSO app extension type |
| Supports the following apps:  <br>- Microsoft 365  <br>- Apps, websites or services integrated with Microsoft Entra ID | Supports the following apps:  <br>- Apps, websites or services integrated with AD  <br>  <br> |

For more information on the SSO app extension, go to [SSO overview and options for Apple devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/enterprise-sso-plugin).

## Create a single sign-on app extension configuration policy

This section shows how to create an SSO app extension policy. For information on platform SSO, go to [Configure platform SSO for macOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-macos).

- [Intune](#tabpanel_2_create-profile-intune)
- [Jamf Pro](#tabpanel_2_create-profile-jamf-pro)
- [Other MDMs](#tabpanel_2_create-profile-other-mdm)

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), create a device configuration profile. This profile includes the settings to configure the SSO app extension on devices.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

   - **Platform**: Select **macOS**.
   - **Profile type**: Select **Templates** > **Device features**.

4. Select **Create**:

   ![Screenshot that shows how to create a device features configuration profile for macOS in Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/macos-create-device-features.png)
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **macOS-SSO app extension**.
   - **Description**: Enter a description for the policy. This setting is optional, but recommended.

6. Select **Next**.
7. In **Configuration settings**, select **Single sign-on app extension**, and configure the following properties:

   - **SSO app extension type**: Select **Microsoft Entra ID**:

     ![Screenshot that shows the SSO app extension type and Microsoft Entra ID for macOS in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/macos-device-features-sso-extension-type.png)
   - **App bundle ID**: Enter a list of bundle IDs for apps that don't support MSAL **and** are allowed to use SSO. For more information, go to [Applications that don't use MSAL](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#enable-sso-for-apps-that-dont-use-a-microsoft-identity-platform-library).
   - **Additional configuration**: To customize the end user experience, you can add the following properties. These properties are the default values used by the SSO app extension, but they can be customized for your organization needs:
     | Key | Type | Description |
     | --- | --- | --- |
     | **AppPrefixAllowList** | String | **Recommended value**: `com.microsoft.,com.apple.`  <br>  <br>Enter a list of prefixes for apps that don't support MSAL **and** are allowed to use SSO. For example, enter `com.microsoft.,com.apple.` to allow all Microsoft and Apple apps.  <br>  <br>Be sure these apps [meet the allowlist requirements](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#enable-sso-for-apps-that-dont-use-msal). |
     | **browser\_sso\_interaction\_enabled** | Integer | **Recommended value**: `1`  <br>  <br>When set to `1`, users can sign in from Safari browser, and from apps that don't support MSAL. Enabling this setting allows users to bootstrap the extension from Safari or other apps. |
     | **disable\_explicit\_app\_prompt** | Integer | **Recommended value**: `1`  <br>  <br>Some apps might incorrectly enforce end-user prompts at the protocol layer. If you see this problem, users are prompted to sign in, even though the Microsoft Enterprise SSO plug-in works for other apps.  <br>  <br>When set to `1` \(one\), you reduce these prompts. |


     Tip


     For more information on these properties, and other properties you can configure, go to [Microsoft Enterprise SSO plug-in for Apple devices](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#more-configuration-options).


     When you're done configuring the recommended settings, the settings look similar to the following values in your Intune configuration profile:


     ![Screenshot that shows the end user experience configuration options for the Enterprise SSO app extension plug-in on macOS devices in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/macos-sso-extension-additional-configuration.png)

8. Continue creating the profile, and assign the profile to the users or groups that receive these settings. For the specific steps, go to [Create the profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-device-features-apple#create-the-profile).

   For guidance on assigning profiles, go to [Assign user and device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).

When the policy is ready, you assign the policy to your users. Microsoft recommends you assign the policy when the device enrolls in Intune. But, it can be assigned at any time, including on existing devices. When the device checks in with the Intune service, it receives this profile. For more information, go to [Policy refresh intervals](https://learn.microsoft.com/en-us/intune/device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).

To check that the profile deployed correctly, in the Intune admin center, go to **Devices** > **Manage devices** > **Configuration** > select the profile you created and generate a report:

![Screenshot that shows the macOS device configuration profile deployment report in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/macos-enterprise-sso-profile-report.png)

In the Jamf Pro portal, you create a Computer configuration profile. This profile includes the settings to configure the SSO app extension on devices.

1. Sign in to the Jamf Pro portal.
2. To create a macOS profile, select **Computers** > **Configuration profiles** > **New**:

   ![Screenshot that shows the Jamf Pro portal and how to create a configuration profile for macOS devices.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/jamf-pro-configuration-profiles.png)
3. In **Name**, enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is: **macOS-Microsoft Enterprise SSO plug-in**.
4. In the **Options** column, scroll down and select **Single Sign-On Extensions** > **Add**:

   ![Screenshot that shows the Jamf Pro portal. Select the configuration profiles SSO option and select add for macOS devices.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/sso-extension-creation.png)
5. Enter the following properties:

   - **Payload Type**: Select **SSO**.
   - **Extension Identifier**: Enter `com.microsoft.CompanyPortalMac.ssoextension`.
   - **Team Identifier**: Enter `UBF8T346G9`.
   - **Sign-On Type**: Select **Redirect**.
   - **URLs**: Enter the following URLs, one at a time:

     - `https://login.microsoftonline.com`
     - `https://login.microsoft.com`
     - `https://sts.windows.net`
     - `https://login.partner.microsoftonline.cn`
     - `https://login.chinacloudapi.cn`
     - `https://login.microsoftonline.us`
     - `https://login-us.microsoftonline.com`


   ![Screenshot that shows the Jamf Pro portal and the payload type, extension identifier, team identifier, and SSO type settings for macOS devices.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/sso-extension-basic-settings-1.png)


   ![Screenshot that shows the Jamf Pro portal and the SSO URLs for macOS devices.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/sso-extension-basic-settings-2.png)

6. In **Custom Configuration**, you define other required properties. Jamf Pro requires that these properties are configured using an uploaded PLIST file. To see the full list of configurable properties, go to [Microsoft Enterprise SSO plug-in for Apple devices documentation](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#manual-configuration-for-other-mdm-services).

   The following example is a recommended PLIST file that meets the needs of most organizations:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <plist version="1.0">
   <dict>
       <key>AppPrefixAllowList</key>
       <string>com.microsoft.,com.apple.,com.jamf.,com.jamfsoftware.</string>
       <key>browser_sso_interaction_enabled</key>
       <integer>1</integer>
       <key>disable_explicit_app_prompt</key>
       <integer>1</integer>
   </dict>
   </plist>
   ```


   ![Screenshot that shows a sample custom configuration with a PLIST file for Jamf Pro.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/sso-extension-custom-configuration-plist.png)


   These PLIST settings configure the following SSO Extension options. These properties are the default values used by the SSO app extension, but they can be customized for your organization needs:


   | Key | Type | Description |
   | --- | --- | --- |
   | **AppPrefixAllowList** | String | **Recommended value**: `com.microsoft.,com.apple.,com.jamf.,com.jamfsoftware.`  <br>  <br>Enter a list of prefixes for apps that don't support MSAL **and** are allowed to use SSO. For example, enter `com.microsoft.,com.apple.,com.jamf.,com.jamfsoftware.` to allow all Microsoft, Apple, and Jamf Pro apps.  <br>  <br>Be sure these apps [meet the allowlist requirements](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#enable-sso-for-apps-that-dont-use-msal). |
   | **disable\_explicit\_app\_prompt** | Integer | **Recommended value**: `1`  <br>  <br>Some apps might incorrectly enforce end-user prompts at the protocol layer. If you see this problem, users are prompted to sign in, even though the Microsoft Enterprise SSO plug-in works for other apps.  <br>  <br>When set to `1` \(one\), you reduce these prompts. |


   Tip


   For more information on these properties, and other properties you can configure, go to [Microsoft Enterprise SSO plug-in for Apple devices](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#more-configuration-options).

7. Select the **Scope** tab. Enter the computers or devices that should be targeted to receive the SSO Extension MDM profile.
8. Select **Save**.

When the device checks in with the Jamf Pro service, it receives this profile.

Tip

If you use Jamf Connect, it is recommended that you follow the [latest Jamf guidance on integrating Jamf Connect with Microsoft Entra ID](https://learn.jamf.com/bundle/jamf-connect-documentation-current/page/Jamf_Connect_and_Microsoft_Conditional_Access.html) \(opens Jamf Pro's web site\). The recommended integration pattern ensures that Jamf Connect works properly with your Conditional Access policies and Microsoft Entra ID Protection.

In the MDM portal, create a device configuration profile. This profile includes the settings to configure the SSO app extension on devices.

1. Sign in to the MDM portal.
2. Create a new device configuration profile.
3. Select an option called **Single Sign-On Extensions** or **SSO extension**. The name can vary depending on your MDM service.
4. Enter the following properties:
   | **Key** | **Value** |
   | --- | --- |
   | Payload Type | SSO |
   | Extension Identifier | `com.microsoft.CompanyPortalMac.ssoextension` |
   | Team Identifier | `UBF8T346G9` |
   | Sign-On Type | Redirect |
   | URLs | - `https://login.microsoftonline.com`  <br>- `https://login.microsoft.com`  <br>- `https://sts.windows.net`  <br>- `https://login.partner.microsoftonline.cn`  <br>- `https://login.chinacloudapi.cn`  <br>- `https://login.microsoftonline.us`  <br>- `https://login-us.microsoftonline.com` |
5. Optionally, you can configure other properties. These properties are the default values used by the SSO app extension, but they can be customized for your organization needs:
   | Key | Type | Description |
   | --- | --- | --- |
   | **AppPrefixAllowList** | String | **Recommended value**: `com.microsoft.,com.apple.`  <br>  <br>Enter a list of prefixes for apps that don't support MSAL **and** are allowed to use SSO. For example, enter `com.microsoft.,com.apple.` to allow all Microsoft and Apple apps.  <br>  <br>Be sure these apps [meet the allowlist requirements](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#enable-sso-for-apps-that-dont-use-msal). |
   | **browser\_sso\_interaction\_enabled** | Integer | **Recommended value**: `1`  <br>  <br>When set to `1`, users can sign in from Safari browser, and from apps that don't support MSAL. Enabling this setting allows users to bootstrap the extension from Safari or other apps. |
   | **disable\_explicit\_app\_prompt** | Integer | **Recommended value**: `1`  <br>  <br>Some apps might incorrectly enforce end-user prompts at the protocol layer. If you see this problem, users are prompted to sign in, even though the Microsoft Enterprise SSO plug-in works for other apps.  <br>  <br>When set to `1` \(one\), you reduce these prompts. |


   Tip


   For more information on these properties, and other properties you can configure, go to [Microsoft Enterprise SSO plug-in for Apple devices](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin#more-configuration-options).

6. Assign the new policy to the devices that should be targeted to receive the SSO Extension MDM profile.

When the device checks in with the MDM service, it receives this profile.

## End user experience

![End user flow chart when installing SSO app app extension on macOS devices in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/flow-chart-end-user-macos.png)

- If you don't deploy the Company Portal app by using an app policy, users must install it manually. Users don't need to use the Company Portal app, it just needs to be installed on the device.
- Users sign in to any supported app or website to bootstrap the extension. Bootstrap is the process of signing in for the first time, which sets up the extension.
- After users sign in successfully, the extension is automatically used to sign in to any other supported app or website.

You can test single sign-on by opening [Safari in private mode](https://support.apple.com/guide/safari/browse-privately-ibrw1069/mac) \(opens Apple's web site\) and opening the `https://portal.office.com` site. No username and password are required.

![Users signs in to app or website to bootstrap the SSO app extension on iOS/iPadOS and macOS devices in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/macos-sso-animated.gif)

On macOS, when users sign in to a work or school app, they're prompted to opt in or out of SSO. They can select **Don't ask me again** to opt out of SSO and block future requests.

Users can also manage their SSO preferences in the Company Portal app for macOS. To edit preferences, go to the Company Portal app menu bar > **Company Portal** > **Settings**. They can select or deselect **Don't ask me to sign in with single sign-on for this device**.

![Don't ask me to sign in with single sign-on for this device.](https://learn.microsoft.com/en-us/intune/device-configuration/media/enterprise-sso-plugin/macos-sso-dont-ask.png)

Tip

Learn more about how the SSO plug-in works and how to troubleshoot the Microsoft Enterprise SSO Extension with the [SSO troubleshooting guide for Apple devices](https://learn.microsoft.com/en-us/entra/identity/devices/troubleshoot-mac-sso-extension-plugin).

## Related articles

- For information about the Microsoft Enterprise SSO plug-in, go to [Microsoft Enterprise SSO plug-in for Apple devices](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin).
- For information from Apple on the single sign-on extension payload, go to [single sign-on extensions payload settings](https://support.apple.com/guide/deployment/extensible-single-sign-on-payload-settings-depfd9cdf845/web) \(opens Apple's web site\).
- For information on troubleshooting the Microsoft Enterprise SSO Extension, go to [Troubleshooting the Microsoft Enterprise SSO Extension plugin on Apple devices](https://learn.microsoft.com/en-us/entra/identity/devices/troubleshoot-mac-sso-extension-plugin).
