<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/filters/ref-supported-workloads -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# List of platforms, policies, and app types supported by assignment filters in Microsoft Intune

[Assignment filters in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) help you target policies to specific devices and apps based on criteria, like OS version or device properties. You can use filters when assigning apps, compliance policies, device configuration profiles, and app configuration policies to **managed devices** \(devices enrolled in Intune\) and **managed apps** \(apps managed by Intune\).

This article lists the app types, compliance policies, device configuration profiles, and app configuration policies that support assignment filters. It also lists the workloads that aren't supported.

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) : Supports assignment filters.
- ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) : Doesn't support assignment filters.
- N/A: Doesn't apply to the platform.

Important

On October 14, 2025, [Windows 10 reached end of support](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

## Supported app types for managed devices

You can use assignment filters for some common app policies on the following platforms. For a list of what's not supported on managed devices, go to [not supported](#not-supported-on-managed-devices) \(in this article\).

- [Windows](#tabpanel_1_windows-apps)
- [Android](#tabpanel_1_android-apps)
- [Apple](#tabpanel_1_apple-apps)

### Windows

| App type | Supported |
| --- | --- |
| Store app | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft 365 apps | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft Edge version 77 and newer | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft Defender for Endpoint | N/A |
| Web link | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) |
| Windows web link | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Line-of-business apps | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Windows app \(Win32\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft Store for Business | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |

### Android Enterprise

| App type | Supported |
| --- | --- |
| Store app | N/A |
| Microsoft 365 apps | N/A |
| Microsoft Edge version 77 and newer | N/A |
| Microsoft Defender for Endpoint | N/A |
| Web link | N/A |
| Line-of-business apps | N/A |
| Android Enterprise system app | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Managed Google Play store app | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Managed Google Play web link | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Managed Android line-of-business app | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |

Note

Assignment filters aren't supported on Android Enterprise personally-owned devices with work profile \(BYOD\) when used in "Available" app assignments. If users are targeted with an "Available" app intent, then the app continues to show as available to install from the Google managed play store. Any include or exclude filtering is ignored.

### Android device administrator

| App type | Supported |
| --- | --- |
| Store app | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft 365 apps | N/A |
| Microsoft Edge version 77 and newer | N/A |
| Microsoft Defender for Endpoint | N/A |
| Web link | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) |
| Line-of-business apps | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

### iOS/iPadOS

| App type | Supported |
| --- | --- |
| Store app | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft 365 apps | N/A |
| Microsoft Edge version 77 and newer | N/A |
| Microsoft Defender for Endpoint | N/A |
| Web link | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) |
| iOS/iPadOS web clip | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Line-of-business apps | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| iOS/iPadOS volume purchase program \(VPP\) app | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |

### macOS

| App type | Supported |
| --- | --- |
| Store app | N/A |
| Microsoft 365 apps | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft Edge version 77 and newer | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft Defender for Endpoint | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Web link | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) |
| Line-of-business apps | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |

## [App configuration policies](https://learn.microsoft.com/en-us/intune/app-management/configuration/overview)

- For **managed apps**, you can use assignment filters for app configuration policies on the following platforms:

  - Android
  - iOS/iPadOS
  - Windows

- For **managed devices**, you can use assignment filters for app configuration policies on the following platforms:

  - Android Enterprise
  - iOS/iPadOS

## [App protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/overview)

- For **managed apps**, you can use assignment filters for app protection policies on the following platforms:

  - Android
  - iOS/iPadOS
  - Windows

- For **managed devices**, assignment filters aren't supported for app protection policies. For other features not supported on managed devices, go to [not supported](#not-supported-on-managed-devices) \(in this article\).

## Compliance policies

- For **managed apps**, assignment filters aren't supported for compliance policies.
- For **managed devices**, you can use assignment filters for all compliance policies on the following platforms:

  - Android device administrator
  - Android Enterprise
  - Android \(AOSP\)
  - iOS/iPadOS
  - macOS
  - Windows

## Device configuration profiles and Endpoint security

- For **managed apps**, assignment filters aren't supported for device configuration profiles and endpoint security policies.
- On **managed devices**, you can use filters for some common device configuration policies on the platforms listed in the following tables. For a list of what's not supported, go to [not supported](#not-supported-on-managed-devices) \(in this article\).

Note

Some profile types are only available for specific platforms. For example, the **Device features** profile type includes settings that are only available for iOS/iPadOS and macOS devices.

For a list of all device configuration profiles, and the platforms they apply to, go to [Apply features and settings on your devices](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

- [Windows](#tabpanel_2_windows-device-configuration)
- [Android](#tabpanel_2_android-device-configuration)
- [Apple](#tabpanel_2_apple-device-configuration)

### Windows

| Profile type | Supported |
| --- | --- |
| Update rings for Windows | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
|  |  |
| **Device configuration profile** |  |
| Custom | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Derived credential | N/A |
| Delivery optimization | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device Restrictions \(Windows 10 Team\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device Features | N/A |
| Device Firmware Configuration Interface \(DFCI\) on Windows on supported UEFI | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Domain Join | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Edition upgrade and S mode switch | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Email | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Endpoint analytics Remediations scripts | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Endpoint Protection | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Enrollment device platform restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg)  <br>Support for a subset of filter properties including device `osVersion`, `operatingSystemSKU`, and `enrollmentProfileName` |
| Kiosk | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Network boundary | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS imported certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| SCEP certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Secure assessment \(Education\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Settings catalog | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Shared multi-user device | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Trusted certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| VPN | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Wi-Fi | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Wired network | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) |
| Windows health monitoring | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg)  <br>**Account protection**, **Local user group membership**, and **Local admin password solution \(Windows LAPS\)** |
| Antivirus | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Attack surface reduction | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg)  <br>Excludes **Web protection \(Microsoft Edge Legacy\)**, **Application control**, and **App and browser isolation** |
| Disk encryption | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Endpoint detection and response | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Endpoint Privilege Management \(EPM\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Firewall | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Microsoft Defender for Endpoint \(Windows Desktop\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Security baselines | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) |

### Android Enterprise

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Custom | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Derived credential | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device Restrictions \(Windows 10 Team\) | N/A |
| Device Features | N/A |
| Email | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Endpoint Protection | N/A |
| Enrollment device platform restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) |
| OEMConfig | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS imported certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| SCEP certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Settings catalog | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Trusted certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| VPN | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Wi-Fi | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | N/A |
| Antivirus | N/A |
| Attack surface reduction | N/A |
| Disk encryption | N/A |
| Endpoint detection and response | N/A |
| Firewall | N/A |
| Security baselines | N/A |

### Android \(AOSP\)

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Device restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| SCEP certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Settings catalog | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Trusted certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |

### Android device administrator

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Custom | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Derived credential | N/A |
| Device restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device restrictions \(Windows 10 Team\) | N/A |
| Device features | N/A |
| Email | N/A |
| Email \(Samsung KNOX only\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Endpoint Protection | N/A |
| Enrollment device platform restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) |
| MX profile \(Zebra only\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS imported certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| SCEP certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Settings catalog | N/A |
| Trusted certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| VPN | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Wi-Fi | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | N/A |
| Antivirus | N/A |
| Attack surface reduction | N/A |
| Disk encryption | N/A |
| Endpoint detection and response | N/A |
| Firewall | N/A |
| Security baselines | N/A |

### iOS/iPadOS

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Custom | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Derived credential | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device Restrictions \(Windows 10 Team\) | N/A |
| Device Features | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Email | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Endpoint Protection | N/A |
| Enrollment device platform restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS imported certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| SCEP certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Settings catalog \(MDM\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Settings catalog \(DDM\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Trusted certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| VPN | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Wi-Fi | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | N/A |
| Antivirus | N/A |
| Attack surface reduction | N/A |
| Disk encryption | N/A |
| Endpoint detection and response | N/A |
| Firewall | N/A |
| Security baselines | N/A |

### macOS

| Profile type | Supported |
| --- | --- |
| **Device configuration profile** |  |
| Custom | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Derived credential | N/A |
| Device restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Device restrictions \(Windows 10 Team\) | N/A |
| Device features | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Email | N/A |
| Endpoint Protection | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Enrollment device platform restrictions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Extensions | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| PKCS imported certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Preference file | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| SCEP certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Settings catalog \(MDM\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Settings catalog \(DDM\) | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Trusted certificate | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| VPN | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Wi-Fi | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Wired network | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
|  |  |
| **Endpoint Security profile** |  |
| Account protection | N/A |
| Antivirus | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Attack surface reduction | N/A |
| Disk encryption | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Endpoint detection and response | N/A |
| Firewall | ![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| Security baselines | N/A |

## Not supported on managed devices

The following features on managed devices don't support using assignment filters:

- Custom compliance policies for Windows \(preview\)
- App protection policies for Android and iOS/iPadOS

  You can use assignment filters on app protection policies for managed apps. For more information on managed apps, go to [Use filters when assigning your apps, policies, and profiles in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview).
- End user experiences customization policies
- Enrollment notifications
- Feature updates for Windows
- iOS/iPadOS app provisioning profiles
- Linux platform workloads
- Partner device management
- Policies for Office apps
- Policy sets
- PowerShell scripts for Windows
- S mode supplemental policies for Windows
- Shell scripts for macOS
- Terms and conditions
- Update policies MDM template for iOS/iPadOS \(deprecated\)
- Devices that are targeted with Endpoint Security configuration using Microsoft Defender for Endpoint integration, such as servers. These devices aren't enrolled in Intune.

## Related content

- [Use filters when assigning your apps, policies, and profiles](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview)
- [Supported device properties when creating assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/ref-device-properties)
