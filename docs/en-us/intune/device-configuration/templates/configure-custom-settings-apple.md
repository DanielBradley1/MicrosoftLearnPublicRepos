<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings-apple -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Use custom settings for Apple devices in Microsoft Intune

Using Microsoft Intune, you can add or create custom settings for your iOS/iPadOS and macOS devices using **custom profiles**. Custom profiles are a feature in Intune. They're designed to add device settings and features that aren't built in to Intune.

This article describes the properties you can configure and provides some guidance on the Apple tools, like Apple Configurator.

The Intune settings catalog has many settings, and more are continually added. Before you create this template profile, look for the settings in the [Intune settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/). It's possible you don't need a custom profile.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This feature supports the following platforms:
> 
> - iOS/iPadOS
> - macOS

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> - Create a [custom device configuration profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings).

## Before you begin

- Don't use custom configuration profiles for sensitive information, such as Wi-Fi connections or authenticating apps, sites, and more. Instead, use the built-in profiles for sensitive information, as they're designed and configured to handle sensitive information.

  For example, use the built-in [Wi-Fi profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi) to deploy a Wi-Fi connection. Use the built-in [certificates profile](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview) for authentication.

- When you use iOS/iPadOS devices, there are tools to help you get custom settings into Intune:

  - [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) \(opens Apple's website\)
  - [Apple Profile Manager](https://support.apple.com/guide/server/intro-to-profile-manager-apd0e2214c6/5.12/mac) \(opens Apple's website\)


  You can use these tools to export settings to a configuration profile. In Intune, you import this file, and then assign the profile to your iOS/iPadOS users and devices. Once assigned, the settings are distributed. They also create a baseline or standard for iOS/iPadOS in your organization.

- When you use **Apple Configurator** to create the configuration profile, be sure the settings you export are compatible with the iOS/iPadOS version on the devices. For information on resolving incompatible settings, search for **Configuration Profile Reference** and **Mobile Device Management Protocol Reference** on the [Apple Developer](https://developer.apple.com/) website.
- When you use **Apple Profile Manager**:

  - In Apple Profile Manager, enable [mobile device management](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C).
  - In Apple Profile Manager, add [iOS/iPadOS devices](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984).
  - After you add a device in Apple Profile Manager, go to **Under the Library** > **Devices** > select your device > **Settings**. Enter the general settings for the device.

    Download and save this file. You enter this file in the Intune profile.
  - Be sure the settings you export from the Apple Profile Manager are compatible with the iOS/iPadOS version on the devices. For information on resolving incompatible settings, search for **Configuration Profile Reference** and **Mobile Device Management Protocol Reference** on the [Apple Developer](https://developer.apple.com/) website.

- For macOS devices, the settings must be in an `.xml` or `.mobileconfig` file.

  You might be able to use **Apple Configurator** to export existing macOS settings to an `.xml` or `.mobileconfig` file. Apple Configurator is designed for the iOS/iPadOS platform, not the macOS platform. So, make sure the settings you export are compatible with the macOS version on the devices.

  For information on resolving incompatible settings, search for **Configuration Profile Reference** and **Mobile Device Management Protocol Reference** on the [Apple Developer](https://developer.apple.com/) website.

- For information on Apple's device management and payload keys, go to:

  - [Apple Device Management](https://developer.apple.com/documentation/devicemanagement) \(opens Apple's web site\)
  - [Profile-Specific Payload Keys](https://developer.apple.com/documentation/devicemanagement/profile-specific_payload_keys) \(opens Apple's web site\)

## Custom configuration profile settings

When you configure the profile, enter the following settings:

- **Custom configuration profile name**: Enter a name for the policy. The device and Intune status show this name.
- **Configuration profile file**: Browse to the configuration profile you created by using the Apple Configurator or Apple Profile Manager. The max file size is `1000000` bytes \(just under 1 MB\). The **File contents** area shows the imported file.

  You can also add device tokens to your custom configuration files. Use device tokens to add device-specific information. For example, to show the serial number, enter `{{serialnumber}}`. On the device, the text shows similar to `123456789ABC`, which is unique to each device.

  When entering variables, be sure to use curly brackets `{{ }}`. [App configuration tokens](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-ios#tokens-used-in-the-property-list) includes a list of variables that you can use. You can also use `deviceid` or any other device-specific value.

- **Configuration profile name**: Enter a name for the policy. This name is shown on the device, and in the Intune status in the Intune admin center.
- **Deployment channel**: Select the channel you want to use to deploy your configuration profile. If you send the profile to the wrong channel, deployment can fail. After you select a channel and save the profile, you can't change the channel. To select a different channel, create a new profile.

  User-targeted payloads don't apply to devices enrolled without user affinity. For more information on whether a payload can be used for a device configuration profile or a user configuration profile, see [Profile-Specific Payload Keys](https://developer.apple.com/documentation/devicemanagement/profile-specific_payload_keys) \(opens Apple's developer website\).
- **Configuration profile file**: Browse to the `.xml` or `.mobileconfig` file you created. The max file size is `1000000` bytes \(just under 1 MB\). The imported file is shown. You can also **Remove** a file after you add it.

  You can also add device tokens to your `.mobileconfig` files. Use device tokens to add device-specific information. For example, to show the serial number, enter `{{serialnumber}}`. On the device, the text shows similar to `123456789ABC`, which is unique to each device. When entering variables, be sure to use curly brackets `{{ }}`.

  [App configuration tokens](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-ios#tokens-used-in-the-property-list) includes a list of variables that can be used. You can also use `deviceid` or any other device-specific value.

Note

The UI doesn't validate variables, and they're case sensitive. As a result, you might see profiles saved with incorrect input. For example, if you enter `{{DeviceID}}` instead of `{{deviceid}}`, the literal string shows instead of the device's unique ID. Be sure to enter the correct information.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- Learn about [custom profiles](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings).
