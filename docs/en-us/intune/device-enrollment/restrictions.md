<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/restrictions -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# What are enrollment restrictions?

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Device enrollment restrictions let you restrict devices from enrolling in Intune based on certain device attributes. There are two types of device enrollment restrictions you can configure in Microsoft Intune:

- **Device platform restrictions**: Restrict devices based on device platform, version, manufacturer, or ownership type.
- **Device limit restrictions**: Restrict the number of devices a user can enroll in Intune.

Note

Enrollment restrictions are not security features. Compromised devices can misrepresent their character. These restrictions are a best-effort barrier for non-malicious users.

Each restriction type comes with one default policy that you can edit and customize as needed. Intune applies the default policy to all user and userless enrollments until you assign a higher-priority policy.

This article provides an overview of the available enrollment restrictions, and feature limitations. To start creating restrictions, skip to [Next steps](https://learn.microsoft.com/en-us/intune/device-enrollment/restrictions#next-steps) \(in this article\).

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> Enrollment restrictions are available for the following platforms:
> 
> - Android device administrator
> - Android Enterprise personally-owned devices with a work profile \(BYOD\)
> - iOS
> - macOS
> - Windows

Availability varies by restriction type.

## Available restrictions

You can configure the following restrictions in the admin center:

- Device limit
- Device platform
- OS version
- Device manufacturer
- Device ownership \(personally owned devices\)

### Device limit

Put a limit on the number of devices a person can enroll. You can set the device limit from 1 to 15.

This configuration is in the admin center under **Enrollment device limit restrictions**.

### Device platform

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

Block devices running on a specific device platform. You can apply this restriction to devices running:

- Android device administrator
- Android Enterprise personally-owned devices with a work profile \(BYOD\)
- iOS/iPadOS
- macOS
- Windows

In groups where both Android platforms are allowed, devices that support work profile will enroll with a work profile. Devices that don't support work profile will enroll on the Android device administrator platform. Neither work profile nor device administrator enrollment will work until you complete all prerequisites for Android enrollment.

This restriction is in the admin center under **Devices** > **Device onboarding** > **Enrollment** > **Device platform restriction**.

Note

Device platform enrollment restrictions use assignment filters. The update between Microsoft Entra and Intune that processes user, group, and filter assignments typically happens within 15 minutes. It's not instant. This amount of time can affect enrollment assignments. You should wait and enroll devices several minutes after adding the enrolling users to a group, not immediately after.

### OS version

This restriction enforces your maximum and minimum OS version requirements. This type of restriction works with the following operating systems:

- Android device administrator\*
- Android Enterprise personally-owned devices with a work profile \(BYOD\)\*
- iOS/iPadOS\*
- Windows

\* Version restrictions are supported on these operating systems for devices enrolled via Intune Company Portal only.

This restriction is in the admin center under **Devices** > **Device onboarding** > **Enrollment** > **Device platform restriction**.

### Device manufacturer

This restriction blocks devices made by specific manufacturers, and is applicable to Android devices only. It is in the admin center under **Devices** > **Device onboarding** > **Enrollment** > **Device platform restriction**.

### Personally owned devices

This restriction helps prevent device users from accidentally enrolling their personal devices, and applies to devices running:

- Android
- iOS/iPad OS
- macOS
- Windows

This restriction is in the admin center under **Devices** > **Device onboarding** > **Enrollment** > **Device platform restriction**.

#### Blocking personal Android devices

By default, until you manually make changes in the admin center, your Android Enterprise work profile device settings and Android device administrator device settings are the same.

If you block Android Enterprise work profile enrollment on personal devices, only corporate-owned devices can enroll with [personally owned work profiles](https://learn.microsoft.com/en-us/intune/app-management/protection/mam-vs-work-profiles-android#android-enterprise-personally-owned-work-profiles).

#### Blocking personal iOS/iPadOS devices

By default, Intune classifies iOS/iPadOS devices as personally owned. To be classified as corporate-owned, an iOS/iPadOS device must fulfill one of the following conditions:

- [Registered with a serial number or IMEI](https://learn.microsoft.com/en-us/intune/device-enrollment/add-corporate-identifiers).
- Enrolled by using Automated Device Enrollment \(formerly Device Enrollment Program\).

#### Blocking personal Macs

By default, Intune classifies macOS devices as personally owned. To be classified as corporate-owned, a Mac must fulfill one of the following conditions:

- [Registered with a serial number](https://learn.microsoft.com/en-us/intune/device-enrollment/add-corporate-identifiers).
- Enrolled via Apple Automated Device Enrollment \(ADE\).

#### Blocking personal Windows devices

If you block personally owned Windows devices from enrollment, Intune checks to make sure that each new Windows enrollment request has been authorized for corporate enrollment. Unauthorized enrollments are blocked.

The following enrollment methods are authorized for corporate enrollment:

- The device enrolls through [Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/enrollment-autopilot).
- The device enrolls through GPO, or [automatic enrollment from Configuration Manager for co-management](https://learn.microsoft.com/en-us/configmgr/comanage/quickstart-paths#bkmk_path1).
- The device enrolls through a [bulk provisioning package](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/create-bulk-package).
- The enrolling user is using a [device enrollment manager account](https://learn.microsoft.com/en-us/intune/device-enrollment/setup-enrollment-manager).

Note

Since a co-managed device enrolls in the Microsoft Intune service based on its Microsoft Entra device token, and not a user token, only the default Intune enrollment restriction will apply to it.

Intune marks devices going through the following types of enrollments as corporate-owned, and blocks them from enrolling \(unless registered with Windows Autopilot\) because these methods don't offer the Intune administrator per-device control:

- [Automatic MDM enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment) with [Microsoft Entra join during Windows setup](https://learn.microsoft.com/en-us/azure/active-directory/device-management-azuread-joined-devices-frx).
- [Automatic MDM enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment) with [Microsoft Entra join from Windows Settings](https://learn.microsoft.com/en-us/azure/active-directory/user-help/user-help-join-device-on-network).
- [Automatic MDM enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment) with Microsoft Entra join or hybrid Entra join via [Windows Autopilot for existing devices](https://learn.microsoft.com/en-us/autopilot/existing-devices).

Intune also blocks personal devices using these enrollment methods:

- [Automatic MDM enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment) with [Add Work Account from Windows Settings](https://learn.microsoft.com/en-us/azure/active-directory/user-help/user-help-register-device-on-network).
- [MDM enrollment only](https://learn.microsoft.com/en-us/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) option from Windows Settings.
- [Enrollment using the Intune Company Portal app](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-windows).
- Enrollment via a Microsoft 365 app, which occurs when users select the **Allow my organization to manage my device** option during app sign-in.

Important

Devices joined by Workplace Join could be blocked from enrolling if they were ever previously Microsoft Entra joined to the tenant. To avoid being blocked, deregister and remove the device's associated object in Microsoft Entra ID before attempting to join the device by Workplace Join.

## Limitations

- Enrollment restrictions are applied to enrollments that are user-driven. For enrollment scenarios that **aren't** user-driven, Intune enforces the default policy. For example, the following enrollment scenarios use the default policy because they **aren't** user-driven:

  - Windows Autopilot self-deploying mode and Windows Autopilot for pre-provisioned deployment
  - Bulk enrollment via Windows Configuration Designer
  - Co-managed enrollments
  - Userless Apple automated device enrollment \(without user-device affinity\)
  - Azure Virtual Desktop
  - Windows 365
  - Android Enterprise corporate-owned dedicated devices

- Device limit restrictions can't be applied to devices in the following Windows enrollment scenarios, because these scenarios utilize shared device mode:

  - Co-managed enrollments
  - Group Policy \(GPO\) enrollments
  - Microsoft Entra joined enrollments, including bulk enrollments
  - Windows Autopilot enrollments
  - Device enrollment manager enrollments


  Instead, you can configure a hard limit for these enrollment types in Microsoft Entra ID. For more information, see [Manage device identities by using the Azure portal](https://learn.microsoft.com/en-us/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).

## Next steps

Select the type of enrollment restriction you want to apply and create the profile:

- [Create device platform enrollment restrictions](https://learn.microsoft.com/en-us/intune/device-enrollment/create-platform-restrictions)
- [Create device limit enrollment restrictions](https://learn.microsoft.com/en-us/intune/device-enrollment/create-device-limit-restrictions)
