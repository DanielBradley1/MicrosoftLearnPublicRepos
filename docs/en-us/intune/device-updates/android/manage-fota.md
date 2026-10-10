<!-- Source: https://learn.microsoft.com/en-us/intune/device-updates/android/manage-fota -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# Manage Firmware Over-the-Air updates on Android

Firmware Over-the-Air \(FOTA\) updates let you remotely update device firmware over a wireless connection. A FOTA update can include software and security patches, feature updates, and other changes to the device's firmware. This method is more efficient, convenient, and more secure than manual updates and can be performed on a scheduled or on-demand basis.

In the context of FOTA, a *deployment* is an update policy that includes instructions about the firmware update to be deployed to devices and other update-related settings. For example, Schedule type, and charging requirements.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> FOTA updates are supported on Android Enterprise devices enrolled in Intune. This includes the following enrollment types:
> 
> - Android Enterprise corporate-owned dedicated \(COSU\)
> - Android Enterprise corporate-owned fully managed \(COBO\)
> - Android Enterprise corporate-owned with a work profile \(COPE\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> This feature requires Microsoft Intune Plan 2 or an additional subscription. For licensing options, see [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) and [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

## Manage FOTA updates

You have two ways to manage software updates:

- Use Firmware Over-the-Air \(FOTA\), which works for some OEMs.

  Note

  If Zebra updated the available firmware list in the last 24 hours, then the list of firmware available might take up to 24 hours to populate.
- If FOTA isn't available you can use Device restrictions profiles, which work for all OEMs.

### FOTA update management for specific OEMs

Manufacturer-specific FOTA support might offer more controls beyond what device restrictions profiles offer.

Intune supports FOTA update management for supported devices from the following manufacturers:

- **Samsung**: Samsung Knox E-FOTA integration is supported in the public cloud and in U.S. Government Community Cloud \(GCC\) High. For Samsung devices, see [Samsung Knox E-FOTA integration with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-updates/android/setup-samsung-knox).
- **Zebra**: For Zebra devices, see [LifeGuard Over-the-Air Integration with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-updates/android/setup-zebra-lifeguard).

### Use device restrictions profiles to manage FOTA updates

Device restrictions profiles offer control over how the device handles over-the-air updates and allow you to set a freeze period for these updates. A freeze period is a specified time frame during which over-the-air updates are blocked from being installed on the device. This can be useful for organizations that want to prevent updates from being installed during critical business periods or when devices are in use.

Note

Not all device manufacturers support over-the-air updates.

To manage FOTA updates using device restrictions profiles:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > **Android**.
2. Select **Manage devices** > **Configuration** > **Create** > **New policy**
3. Under **Platform**, select **Android Enterprise**.
4. Under **Policy type**, select **Templates**.
5. Under **Fully Managed, Dedicated, and Corporate-Owned Work Profile**, select **Device restrictions** > **Create**.
6. Configure the system update settings as needed. For more information about these settings, see [Device restrictions for Android Enterprise](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise).
