<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/configure-settings -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Configure and secure devices with Microsoft Intune

With Intune, you can configure settings for devices in the school, to ensure that they comply with specific policies. For example, you may need to secure your devices, ensuring that they are kept up to date. Or you may need to configure all the devices with the same look and feel.

Settings can be assigned to groups:

- If you target settings to a **group of users**, those settings apply, regardless of what managed devices the targeted users sign in to
- If you target settings to a **group of devices**, those settings apply regardless of who is using the devices

## Introduction

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Learn about the different types of settings

- [Intune](#tabpanel_1_intune)
- [Intune For Education](#tabpanel_1_intune-for-education)

Device profiles allow you to add and configure settings, and then push these settings to devices in your organization. You have some options when creating policies:

- **Baselines**: Baselines include preconfigured security settings. If you want to create security policy using recommendations by Microsoft security teams, then security baselines are for you.

  For more information, see [Security baselines](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview).
- **Settings catalog**: Use the settings catalog to see all the available settings, and in one location. For example, you can see all the settings that apply to BitLocker, and create a policy that just focuses on BitLocker.

  For more information, see [Settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/).
- **Templates**: Templates include a logical grouping of settings that configure a feature or concept, such as VPN, email, kiosk devices, and more. If you're familiar with creating device configuration policies in Microsoft Intune, then you're already using these templates.

  For more information, including the available templates, see [Apply features and settings on your devices using device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

Tip

You can find a list of common configurations used in K-12 organizations at [Common Education configuration overview](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-common-settings).

There are two ways to manage settings in Intune for Education:

- **Express Configuration.** This option is used to configure a selection of settings that are commonly used in school environments
- **Group settings.** This option is used to configure all settings offered by Intune for Education

Note

Express Configuration is ideal when you are getting started. Settings are pre-configured to Microsoft-recommended values, but can be changed to fit your school's needs.

With Express Configuration, you can get Intune for Education up and running in just a few steps. You can select a group of devices or users, select applications to distribute, and choose settings from the most commonly used in schools.

- [Intune](#tabpanel_2_intune)
- [Intune For Education](#tabpanel_2_intune-for-education)

Device profiles allow you to add and configure settings, and then push these settings to devices in your organization. You have some options when creating policies:

- **Settings catalog**: Use the settings catalog to see all the available settings, and in one location. For example, you can see all the settings that apply to Networking, and create a policy that just focuses on Network.

  For more information, see [Settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/).
- **Templates**: Templates include a logical grouping of settings that configure a feature or concept, such as VPN, email, kiosk devices, and more. If you're familiar with creating device configuration policies in Microsoft Intune, then you're already using these templates.

  For more information, including the available templates, see [Apply features and settings on your devices using device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

There are two ways to manage settings in Intune for Education:

- **Express Configuration.** This option is used to configure a selection of settings that are commonly used in school environments.
- **Group settings.** This option is used to configure all settings that are offered by Intune for Education.

Note

Express Configuration is ideal when you are getting started. Settings are pre-configured to Microsoft-recommended values, but can be changed to fit your school's needs.

With Express Configuration, you can get Intune for Education up and running in just a few steps. You can select a group of devices or users, select applications to distribute, and choose settings from the most commonly used in schools.

## Device settings

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Configure settings and assign them to devices

- [Intune](#tabpanel_3_intune)
- [Intune For Education](#tabpanel_3_intune-for-education)

To create a device configuration profile in Microsoft Intune, you need to follow these steps:

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- Go to **Devices** > **Manage devices** > **Configuration** > **+ Create profile**.
- Select **Platform** as **Windows 10 and later**.
- Select **Profile type**:

  - For general settings, select [**Settings Catalog**](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/).
  - For templates including certificates, Wi-Fi, and VPN, select **Templates** and then choose the required template.

- Follow the steps to create and configure the profile as necessary.

Groups are used to manage users and devices with similar management needs, allowing you to apply changes to many devices or users at once. To review the available group settings:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Groups** > Pick a group to manage.
3. Select **Windows device settings**.
4. Expand the different categories and review information about individual settings.

Settings that are commonly configured for student devices include:

- Wallpaper and lock screen background. See [Lock screen and desktop](https://learn.microsoft.com/en-us/intune-education/all-edu-settings-windows#lock-screen-and-desktop).
- Wi-Fi connections. See [Add Wi-Fi profiles](https://learn.microsoft.com/en-us/intune-education/add-wi-fi-profile).
- Enablement of the integrated testing and assessment solution *Take a Test*. See [Add Take a Test profile](https://learn.microsoft.com/en-us/intune-education/take-a-test-profiles).

For more information, see [Windows device settings in Intune for Education](https://learn.microsoft.com/en-us/intune-education/all-edu-settings-windows).

Note

If you require more sophisticated device settings, you can create them in Microsoft Intune. For more information, see [Apply features and settings on your devices using device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

- [Intune](#tabpanel_4_intune)
- [Intune For Education](#tabpanel_4_intune-for-education)

To create a device configuration profile in Microsoft Intune, you need to follow these steps:

- Sign in to the Microsoft Intune admin center.
- Go to **Devices** > **Manage devices** > **Configuration** > **+ Create profile**.
- Select **Platform** as **iOS/iPadOS**.
- Select **Profile type**:

  - For general settings, select **Settings Catalog**.
  - For templates including certificates, Wi-Fi, and VPN, select **Templates** and then choose the required template.

- Follow the steps to create and configure the profile as necessary.

Groups are used to manage users and devices with similar management needs, allowing you to apply changes to many devices or users at once. To review the available group settings:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com/).
2. Select **Groups** > Pick a group to manage.
3. Select **iOS device settings**.
4. Expand the different categories and review information about individual settings.

Settings that are commonly configured for student devices include:

- Lock screen and wallpaper. See [Lock screen and wallpaper](https://learn.microsoft.com/en-us/intune-education/all-edu-settings-ios#lock-screen-and-wallpaper).
- Wi-Fi connections. See [Add Wi-Fi profiles](https://learn.microsoft.com/en-us/intune-education/add-wi-fi-profile).

For more information, see [iOS device settings in Intune for Education](https://learn.microsoft.com/en-us/intune-education/all-edu-settings-ios).

Note

If you require more sophisticated device settings, you can create them in Microsoft Intune. For more information, see [Apply features and settings on your devices using device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

## Update policies

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Configure update policies and assign to devices

- [Intune](#tabpanel_5_intune)
- [Intune For Education](#tabpanel_5_intune-for-education)

It is important to keep Windows devices up to date with the latest security updates. You can create Windows Update policies using Intune.

- [What is Windows Update client policies?](https://learn.microsoft.com/en-us/windows/deployment/update/waas-manage-updates-wufb)
- [Manage Windows software updates in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows)

It is important to keep Windows devices up to date with the latest security updates. You can create Windows Update policies using Intune for Education.

To create a Windows Update policy:

1. Select **Groups** > Pick a group to manage.
2. Select **Windows device settings**.
3. Expand the category **Update and upgrade**.
4. Configure the required settings as needed.

For more information, see [Updates and upgrade](https://learn.microsoft.com/en-us/intune-education/all-edu-settings-windows#updates-and-upgrade).

Note

If you require a more complex Windows Update policy, you can create it in Microsoft Intune. For more information:

- [What is Windows Update client policies?](https://learn.microsoft.com/en-us/windows/deployment/update/waas-manage-updates-wufb)
- [Manage Windows software updates in Intune](https://learn.microsoft.com/en-us/intune/device-updates/windows)

- [Intune](#tabpanel_6_intune)
- [Intune For Education](#tabpanel_6_intune-for-education)

It is important to keep iOS devices up to date with the latest security updates. You can create control updates with Intune using three different methods:

- **Option 1** - iOS and iPadOS 17.0 and newer devices \(recommended\) - [Managed software update policy](https://learn.microsoft.com/en-us/intune/device-updates/apple/).
- **Option 2** - iOS and iPadOS 17.0 and older \(recommended\) - [Software update policy](https://learn.microsoft.com/en-us/intune/device-updates/apple/deprecated-mdm-policies-ios).
- **Option 3** \(not recommended\) - End users manually install the updates.

At **Devices** > **Manage devices** > **Configuration** > **Create** > **Settings catalog** > **Restrictions**, you can use the following settings to delay how long after an update is released that users can manually install the updates.

- **Defer software updates**: Yes/No
- **Delay default visibility of software updates**: 0-90

Tip

The **Settings Catalog** > **Declarative Device Management** > **Software Update** settings take precedence over the **Settings Catalog** > **Restrictions** settings. For more information, go to [Precedence of settings in iOS updates policy](https://learn.microsoft.com/en-us/intune/device-updates/apple/).

For more information, see [Software updates planning guide and scenarios for supervised iOS/iPadOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-updates/apple/planning-guide-ios-ipados).

It is important to keep iOS devices up to date with the latest security updates. You can control when Intune triggers iOS devices to update using Intune for Education.

To create a iOS update restrictions policy:

1. Select **Groups** > Pick a group to manage.
2. Select **iOS device settings**.
3. Expand the category **Update restrictions**.
4. Configure the required settings as needed.

For more information about the other update options in the Intune console, see [Software updates planning guide and scenarios for supervised iOS/iPadOS devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-updates/apple/planning-guide-ios-ipados).

## Security policies

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Configure security policies and assign them to devices

- [Intune](#tabpanel_7_intune)
- [Intune For Education](#tabpanel_7_intune-for-education)

It is critical to ensure that the devices you manage are secured using the different security technologies available in Windows.

- [Antivirus](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/antivirus)
- [Disk encryption](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows)
- [Firewall](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/firewall)
- [Endpoint detection and response](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/deploy-edr)
- [Attack surface reduction](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/attack-surface-reduction)
- [Account protection](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/account-protection)
- [Security Baselines](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview)
- [Local Administrator Password Solution](https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-overview)
- [Web Content Filtering on Edge](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-web-content-filtering)

Microsoft recommmends phishing resistant credentials and using Windows Hello for Business on Windows devices where possible. For more information, and to find out how to do this for students, see [Passwordless for Students](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/protect-passwordless-students?tabs=windows).

It is critical to ensure that the devices you manage are secured using the different security technologies available in Windows. Intune for Education provides different settings to secure devices.

To create a security policy:

1. Select **Groups** > Pick a group to manage.
2. Select **Windows device settings**.
3. Expand the category **Security**.
4. Configure the required settings as needed, including:

   - Windows Defender
   - Windows Encryption
   - Windows SmartScreen

For more information, see [Security](https://learn.microsoft.com/en-us/intune-education/all-edu-settings-windows#security).

Note

If you require more sophisticated security policies, you can create them in Microsoft Intune. For more information, see:

- [Antivirus](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/antivirus)
- [Disk encryption](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows)
- [Firewall](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/firewall)
- [Endpoint detection and response](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/deploy-edr)
- [Attack surface reduction](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/attack-surface-reduction)
- [Account protection](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/account-protection)
- [Security Baselines](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview)
- [Local Administrator Password Solution](https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-overview)
- [Web Content Filtering on Edge](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-web-content-filtering)

- [Intune](#tabpanel_8_intune)
- [Intune For Education](#tabpanel_8_intune-for-education)

In Intune, you can configure iOS security settings using Settings Catalog.

To create a settings catalog device configuration profile in Microsoft Intune, you need to follow these steps:

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- Go to **Devices** > **Manage devices** > **Configuration** > **+ Create profile**.
- Select **Platform** as **iOS/iPadOS**.
- Select **Profile type**.
- Select **Settings Catalog**.
- Follow the steps to create and configure the profile as necessary.

Common areas for security include:

- Restrictions
- Security

In Intune for Education, you can configure iOS security settings using Groups.

1. Select **Groups** > Pick a group to manage.
2. Select **iOS device settings**.
3. Configure the required settings as needed.

Common areas for security include:

- Device restrictions
- Passcode, Touch ID, and Face ID

Note

If you require more sophisticated security settings, you can create them in Microsoft Intune. For more information, see [Apply features and settings on your devices using device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

## Storage policies

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Configure storage policies and assign them to devices

In the educational sector, devices with limited storage capacity are sometimes deployed due to cost and portability considerations. It is essential to manage storage effectively to ensure that Windows devices remain up to date at all times. Storage Sense is a Windows feature that helps automatically free up disk space by deleting unnecessary files. For more information about Storage Sense, see [Configure Storage Sense](https://learn.microsoft.com/en-us/windows/configuration/storage/storage-sense).

---

## Next steps

Now that you've configured your device settings, you can configure applications to deploy to your students' and teachers' devices.

[Next: Configure applications >](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/configure-apps)
