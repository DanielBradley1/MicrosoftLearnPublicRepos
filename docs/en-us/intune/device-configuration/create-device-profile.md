<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/create-device-profile -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Create a device configuration profile in Microsoft Intune

Device configuration profiles allow you to add and configure device settings, and then push these settings to devices in your organization. You have some options when creating policies:

- **Baselines**: On Windows devices, these baselines include preconfigured security settings. If you want to create security policy using recommendations by Microsoft security teams, then use security baselines.

  For more information, go to [Security baselines](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview).
- **Settings catalog**: On your Apple, Android, and Windows devices, you can use the settings catalog to configure device features and settings. The settings catalog has all the available settings, and in one location. For example, you can see all the settings that apply to BitLocker, and create a policy that just focuses on BitLocker. On macOS devices, use the settings catalog to configure Microsoft Edge version 77 and settings.

  More settings are continually being added to the settings catalog. For more information, go to [Settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/).
- **Templates**: On your devices, you can use the built-in templates. Each template includes a logical grouping of settings that configure a feature or concept, such as VPN, email, kiosk devices, and more. If you're familiar with creating device configuration policies in Microsoft Intune, then you're already using these templates.

  For more information, including the available templates, go to [Apply features and settings on your devices using device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

This article:

- Lists the steps to create a profile.
- Shows you how to add a scope tag to "filter" your policies.
- Describes applicability rules on Windows client devices, and shows you how to create a rule.
- Has more information on the check-in refresh cycle times when devices receive profiles and any profile updates.

This feature applies to:

- Android
- iOS/iPadOS
- macOS
- Windows

## Prerequisites

- At a minimum, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the **Policy and Profile manager** role. For information on the built-in roles in Intune, and what they can do, go to [Role-based access control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).
- Enroll your devices in Intune. To learn more about your enrollment options, see [Microsoft Intune enrollment guide](https://learn.microsoft.com/en-us/intune/device-enrollment/guide).

## Create the profile

In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices**. You have the following options:

[![Screenshot that shows how to select Devices to see what you can configure and manage in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/create-device-profile/devices-overview.png)](https://learn.microsoft.com/en-us/intune/device-configuration/media/create-device-profile/devices-overview.png#lightbox)

- **Overview**: Lists the status of some of your profiles, and provides more details on the profiles you assigned to users and devices.
- **Monitor**: Lists all device monitoring reports. Use these reports to check configuration policy assignment failures, incomplete user enrollments, noncompliant devices, update installation failures, and more.
- **By platform**: Expand this option to get a list of supported platforms, like Android and Linux. When you select a platform, you can create and view policies and profiles for the platform you choose.

  This view can also show features specific to the platform. For example, select **Windows**. You see Windows-specific features, like **Scripts and remediations** and **Group policy analytics**.
- **Manage devices**: Expand this option to see the policies you can create, like compliance and configuration policies.

When you create a profile \(**Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**\), choose your platform:

- **Android device administrator**
- **Android \(AOSP\)**
- **Android Enterprise**
- **iOS/iPadOS**
- **macOS**
- **Windows 10 and later**
- **Windows 8.1 and later**

Then, choose your profile type. Depending on the platform you choose, the profile types are different. The following articles describe the different profiles:

- [Settings catalog](#tabpanel_1_sc)
- [Properties catalog](#tabpanel_1_prop)
- [Templates](#tabpanel_1_templates)

- [Settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) - Includes a list of all available settings for Android Enterprise, iOS/iPadOS, macOS, and Windows. You can search and filter on specific settings and areas, like OneDrive or Microsoft Edge.

- [Properties catalog](https://learn.microsoft.com/en-us/intune/device-configuration/collect-device-properties) - Includes a list of available device properties for Windows devices, like CPU manufacturer, network adapter identifier, and more.

Each template is a logical group of settings grouped together, like Email, VPN, and Wi-Fi.

- [BIOS configuration and other settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-bios-windows)
- [Custom](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings)
- [Delivery Optimization \(Windows\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-delivery-optimization-windows)
- [Derived credential \(Android Enterprise, iOS, iPadOS\)](https://learn.microsoft.com/en-us/intune/device-security/certificates/derived-credentials)
- [Device features \(macOS, iOS, iPadOS\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-device-features-apple)
- [Device firmware configuration interface \(DFCI\) \(Windows\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-dfci-windows)
- [Device restrictions](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-device-restrictions)
- [Domain join \(Windows\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-domain-join-windows)
- [Edition upgrade and mode switch \(Windows\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-edition-upgrade-windows)
- [Education \(iOS, iPadOS\)](https://learn.microsoft.com/en-us/intune/solutions/education/ref-classroom-settings-ios)
- [Email](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-email)
- [Endpoint protection \(macOS, Windows\)](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/configure-endpoint-protection)
- [Extensions \(macOS\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-kernel-extensions-macos)
- [Kiosk](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-kiosk)
- [Microsoft Defender for Endpoint \(Windows\)](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/overview)
- [Mobility Extensions \(MX\) profile \(Android device administrator\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-zebra-mx-android)
- [Network boundary \(Windows\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/create-network-boundary-windows)
- [OEMConfig \(Android Enterprise\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-oemconfig-android)
- [PKCS certificate](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/pkcs-profiles)
- [PKCS imported certificate](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/imported-pfx-profiles)
- [Preference file \(macOS\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-preference-file-macos)
- [SCEP certificate](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/scep-infrastructure)
- [Secure assessment \(Education\) \(Windows\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-education-settings)
- [Shared multi-user device \(Windows\)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-shared-device)
- [Trusted certificate](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview)
- [VPN](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-vpn)
- [Wi-Fi](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi)
- [Windows health monitoring](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-health-monitoring-windows)
- [Wired networks](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wired-networks)

For example, if you select Windows for the platform, your options look similar to the following profile:

![Screenshot that shows how to create a Windows device configuration policy and profile in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/create-device-profile/windows-create-device-profile.png)

## Scope tags

After you add the settings, you can also add a scope tag to the profile. Scope tags filter profiles to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. And, are used in distributed IT.

For more information about scope tags, and what you can do, go to [Use RBAC and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

## Applicability rules

Applies to:

- Windows

Applicability rules allow administrators to target devices in a group that meet specific criteria. For example, you create a device restrictions profile that applies to the **All Windows devices** group. And, you only want the profile assigned to devices running Windows Enterprise.

To do this task, create an **applicability rule**. These rules are great for the following scenarios:

- At Bellows College, you want to target all Windows devices running Windows 11, version 24H2.
- You want to target all users in Human Resources at Contoso, but only want Windows Professional or Enterprise devices.

To approach these scenarios, you:

- Create a devices group that includes all devices at Bellows College. In the profile, add an applicability rule so it applies if the OS minimum version is `10.0.26100` and the maximum version is `10.0.26200`. Assign this profile to the Bellows College devices group.

  When the profile is assigned, it applies to devices between the minimum and maximum versions you enter. For devices that aren't between the minimum and maximum versions you enter, their status shows as **Not applicable**.
- Create a users group that includes all users in Human Resources \(HR\) at Contoso. In the profile, add an applicability rule so it applies to devices running Windows Professional or Enterprise. Assign this profile to the HR users group.

  When the profile is assigned, it applies to devices running Windows Professional or Enterprise. For devices that aren't running these editions, their status shows as **Not applicable**.
- If there are two profiles with the exact same settings, then the profile without an applicability rule is applied.

  For example, ProfileA targets the Windows devices group, enables BitLocker, and doesn't have an applicability rule. ProfileB targets the same Windows devices group, enables BitLocker, and has an applicability rule to only apply the profile to the Windows Enterprise edition.

  When both profiles are assigned, ProfileA is applied because it doesn't have an applicability rule.

When you assign the profile to the groups, the applicability rules act as a filter, and only target the devices that meet your criteria.

### Add a rule

Use the following steps to create an applicability rule.

1. In your policy, select **Applicability Rules**. You can choose the **Rule**, and **Property**:

   [![Screenshot that shows how to add an applicability rule to a Windows device configuration profile in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/create-device-profile/applicability-rules.png)](https://learn.microsoft.com/en-us/intune/device-configuration/media/create-device-profile/applicability-rules.png#lightbox)
2. In **Rule**, choose if you want to include or exclude users or groups. Your options:

   - **Assign profile if**: Includes users or groups that meet the criteria you enter.
   - **Don't assign profile if**: Excludes users or groups that meet the criteria you enter.

3. In **Property**, choose your filter. Your options:

   - **OS edition**: In the list, check the Windows client editions you want to include \(or exclude\) in your rule.
   - **OS version**: Enter the **min** and **max** Windows client version numbers of you want to include \(or exclude\) in your rule. Both values are required.

     For example, you can enter `10.0.16299.0` \(RS3 or 1709\) for minimum version and `10.0.17134.0` \(RS4 or 1803\) for maximum version. Or, you can be more granular and enter `10.0.16299.001` for minimum version and `10.0.17134.319` for maximum version.

     For more version numbers, go to [Windows client release information](https://learn.microsoft.com/en-us/windows/release-health/release-information).

4. Select **Add** to save your changes.

## Policy refresh cycle times

Intune uses different refresh cycles to check for updates to configuration profiles. If the device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](https://learn.microsoft.com/en-us/intune/device-configuration/troubleshoot-device-profiles#policy-refresh-intervals) lists the estimated refresh times.

At any time, users can open the Company Portal app, and sync the device to immediately check for profile updates.

## Recommendations

When creating profiles, consider the following recommendations:

- Name your policies so you know what they are, and what they do. All [compliance policies](https://learn.microsoft.com/en-us/intune/device-security/compliance/create-policy) and [configuration profiles](https://learn.microsoft.com/en-us/intune/device-configuration/create-device-profile) have an optional **Description** property. In **Description**, be specific and include information so others know what the policy does.

  Some configuration profile examples include:

  **Profile name**: OneDrive configuration profile for all Windows users  
  **Profile description**: OneDrive profile that includes the minimum and base settings for all Windows users. Created by `user@contoso.com` to prevent users from sharing organizational data to personal OneDrive accounts.

  **Profile name**: VPN profile for all iOS/iPadOS users  
  **Profile description**: VPN profile that includes the minimum and base settings for all iOS/iPadOS users to connect to Contoso VPN. Created by `user@contoso.com` so users automatically authenticate to VPN, instead of prompting users for their username and password.
- Create your profile by its task, such as configure Microsoft Edge settings, enable Microsoft Defender anti-virus settings, block iOS/iPadOS jailbroken devices, and so on.
- Create profiles that apply to specific groups, such as Marketing, Sales, IT Administrators, or by location or school system. Use the built-in features, including:

  - [Use role-based access control \(RBAC\) and scope tags for distributed IT in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags)
  - [Distributed IT with many admins in the same Intune tenant](https://learn.microsoft.com/en-us/intune/fundamentals/scale-guidelines)
  - [Use filters when assigning your apps, policies, and profiles in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview)

- Separate user policies from device policies.

  For example, the [Intune settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) has thousands of settings. These settings show if a setting applies to users or devices. When creating the policy, assign your user settings to a users group, and assign your device settings to a devices group.

  The following image shows an example of some settings that can apply to users, apply to devices, or apply to both:

  [![Screenshot that shows an Intune admin template that applies to user and devices in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/create-device-profile/setting-applies-to-user-and-device.png)](https://learn.microsoft.com/en-us/intune/device-configuration/media/create-device-profile/setting-applies-to-user-and-device.png#lightbox)
- Use Microsoft Copilot in Intune to evaluate your policies, learn more about a policy setting & its effect on your users & security, and compare policies between two devices.

  For more information, go to [Microsoft Copilot in Intune](https://learn.microsoft.com/en-us/intune/copilot/).
- Every time you create a restrictive policy, communicate this change to your users. For example, if you're changing the passcode requirement from four \(4\) characters to six \(6\) characters, let your users know before your assign the policy.

## Related content

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).
- [Monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
