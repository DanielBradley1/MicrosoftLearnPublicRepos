<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager -->
<!-- Sitemap-Last-Modified: 2026-05-05 -->

# Set up device enrollment with Apple School Manager

Set up Microsoft Intune to enroll Apple mobile devices purchased through [Apple School Manager](https://school.apple.com/). Using Intune with Apple School Manager, you can enroll large numbers of devices without ever touching them. When a student or teacher turns on the device, Apple Setup Assistant runs with preconfigured settings and the device enrolls into management.

## Prerequisites

To enable Apple School Manager enrollment, you use both the Microsoft Intune admin center and Apple School Manager portal.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This enrollment method supports the following platforms:
> 
> - iOS/iPadOS
> - tvOS
> - visionOS
> 
> Devices must be added to [Apple School Manager](http://school.apple.com). You need a list of serial numbers or a purchase order number to assign devices in Apple School Manager. tvOS and visionOS devices enroll without user affinity and are enrolled as corporate-owned devices with configuration delivered through custom configuration profiles.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/tenant-administration.svg) **Tenant configuration requirements**

> - Get an [Apple mobile device management \(MDM\) push certificate](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/create-mdm-push-certificate).
> - Set up the [MDM Authority](https://learn.microsoft.com/en-us/intune/fundamentals/setup-mdm-authority).
> - If using Active Directory Federation Services \(AD FS\), user affinity requires [WS-Trust 1.3 Username/Mixed endpoint](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff608241\(v=ws.10\)). For more information, see [Get ADFS endpoint](https://learn.microsoft.com/en-us/powershell/module/adfs/get-adfsendpoint).

Apple School Manager enrollment can't be used with the [device enrollment manager](https://learn.microsoft.com/en-us/intune/device-enrollment/setup-enrollment-manager) account.

## Next steps

This series of articles describes how to set up Microsoft Intune for devices purchased through Apple School Manager.

1. 🡺 Prerequisites \(*You are here*\)
2. [Get an Apple token for school devices](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-1)
3. [Create an Apple enrollment policy](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-2)
4. [Sync and distribute devices](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-3)
