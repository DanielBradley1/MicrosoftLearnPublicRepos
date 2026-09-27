<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/ref-policy-map-configurations -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Configurations policy mapping from Basic Mobility and Security to Intune

You can move from Basic Mobility and Security to Microsoft Intune.

Use this article to map the settings in Microsoft Purview compliance portal configuration policies to the equivalent settings in Intune.

Intune offers more policy flexibility. So, each Office policy translates into multiple Intune and Microsoft Entra policies to achieve the same result.

To see these settings in the Microsoft Purview compliance portal, sign in to the [Purview compliance portal](https://protection.office.com/devicev2). Then, select **Device security policies** > policy name > **Edit policy** > **Configurations**.

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- To configure the settings in an Intune policy, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). [Role-based access control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) lists and describes the built-in roles that can create policies.

## Require encrypted backup

This setting was never supported for Windows or Android in Basic Mobility and Security.

One Intune configuration profile:

- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Compliance settings Edit** > **Cloud and Storage** > **Force encrypted backup**

## Block cloud backup

This setting was never supported for Windows or Android in Basic Mobility and Security.

This setting is only supported on supervices iOS devices.

One Intune configuration profile:

- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **Cloud and Storage** > various **Block iCloud** settings

## Block document synchronization

This setting was never supported for Windows or Android in Basic Mobility and Security.

This setting is only supported on supervices iOS devices.

One Intune configuration profile:

- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **Cloud and Storage** > **Block iCloud document and data sync**

## Block photo synchronization

This setting was never supported for Windows or Android in Basic Mobility and Security.

One Intune configuration profile:

- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **Cloud and Storage** > **Block My Photo Stream**

## Block screen capture

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

Three Intune configuration profiles:

- **Devices** > **By platform** > **Windows** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **General** > **Screen capture \(mobile only\)**
- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **General** > **Block screenshots and screen recording**
- **Devices** > **By platform** > **Android** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **General** > **Screen capture \(Samsung KNOX only\)**

## Block video conferences on device

This setting was never supported for Windows or Android in Basic Mobility and Security.

This setting is only supported on supervised iOS devices.

One Intune configuration profile:

- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **Built-in Apps** > **Block FaceTime**

## Block sending diagnostic data from device

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

For Windows devices, the most restrictive value prevents sending security-related data.

Three Intune configuration profiles:

- **Devices** > **By platform** > **Windows** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **Reporting and Telemetry** > **Share usage data**
  | Block sending diagnostic data from device value | Share usage data value |
  | --- | --- |
  | Selected | Security |
  | Not selected | Not configured |
- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **General** > **Block sending diagnostic and usage data to Apple**
- **Devices** > **By platform** > **Android** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **General** > **Diagnostic data \(Samsung Knox only\)**

## Block access to application store

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

For iOS, this setting is only supported on supervised iOS devices.

Three Intune configuration profiles:

- **Devices** > **By platform** > **Windows** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **App store** > **App store \(mobile only\)**
- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **App store, Doc Viewing, Gaming** > **Block App store**
- **Devices** > **By platform** > **Android** > **Manage devices** > **Configuration** > choose a profile with type **Device administrator** > **Properties** > **Configuration settings Edit** > **Google Play Store** > **Google Play store \(Samsung Knox only\)**

## Require password when accessing application store

This setting was never supported for Windows or Android in Basic Mobility and Security.

Apple doesn't block accessing the app store without a password, but blocks purchases without a password.

One Intune configuration profile:

- **Devices** > **By platform** > **iOS/iPadOS** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **App store, Doc Viewing, Gaming** > **Require iTunes Store password for all purchases**

## Block connection with removable storage

This setting was never supported for iOS/iPadOS in Basic Mobility and Security.

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

Two Intune configuration profiles:

- **Devices** > **By platform** > **Windows** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > **General** > **Removable storage**
- **Devices** > **By platform** > **Android** > **Manage devices** > **Configuration** > choose a profile with type **Device administrator** > **Properties** > **Configuration settings Edit** > **Cloud and Storage** > **Removable storage \(Samsung Knox only\)**

## Block Bluetooth connection

This setting was never supported for iOS/iPadOS in Basic Mobility and Security.

For Android devices, this setting is only supported on Samsung Knox devices in Basic Mobility and Security.

Two Intune configuration profiles:

- **Devices** > **By platform** > **Windows** > **Manage devices** > **Configuration** > profile name > **Properties** > **Configuration settings Edit** > > **Cellular and connectivity** > **Bluetooth**
- **Devices** > **By platform** > **Android** > **Manage devices** > **Configuration** > choose a profile with type **Device administrator** > **Properties** > **Configuration settings Edit** > **Cellular and connectivity** > **Bluetooth \(Samsung Knox only\)**

## Related article

- [Move from Basic Mobility and Security to Intune](https://learn.microsoft.com/en-us/intune/fundamentals/migrate-from-other-mdm)
