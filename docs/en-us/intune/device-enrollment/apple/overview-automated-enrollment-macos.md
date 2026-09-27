<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/overview-automated-enrollment-macos -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Overview of Apple Automated Device Enrollment for macOS

Automated device enrollment \(ADE\) is an Apple enrollment method for corporate-owned Mac computers purchased through Apple Business or Apple School Manager. With ADE, you configure and deploy enrollment policies to devices over the air — without touching the devices. When someone turns on a device for the first time, Apple Setup Assistant guides them through setup and enrollment automatically.

Note

The steps in ADE articles are the same whether you're using Apple Business or Apple School Manager. For brevity, those articles refer to *Apple Business* only, except where clarification is necessary.

## Supported platforms

Intune supports automated device enrollment for macOS.

| Platform | Setup article |
| --- | --- |
| macOS | [Set up an enrollment policy for macOS](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-macos) |

For iOS/iPadOS, tvOS, and visionOS, see [Overview of Apple Automated Device Enrollment for Apple mobile](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/overview-automated-enrollment-apple).

## Supported scenarios

| Scenario | Supported |
| --- | --- |
| Supervised mode | ✅ ADE devices are supervised by default, giving you more management control. |
| Corporate-owned devices | ✅ Designed for devices purchased through Apple Business or Apple School Manager. |
| Zero-touch deployment | ✅ Devices can ship directly to users. Enrollment starts when they turn on the device. |
| Bulk enrollment | ✅ Enroll a few devices or thousands using a single enrollment policy. |
| Devices with a single assigned user | ✅ Supported on macOS. |
| Userless devices \(kiosk, shared-use\) | ✅ Supported on macOS. |
| BYOD or personal devices | ❌ Not supported. |
| Device enrollment manager \(DEM\) accounts | ❌ Not supported. |
| Devices managed by another MDM provider | ❌ Users must unenroll from their current MDM provider before enrolling in Intune. For help migrating devices, see [Apple making device migration to Microsoft Intune easy with upcoming OS 26 release](https://techcommunity.microsoft.com/blog/IntuneCustomerSuccess/apple-making-device-migration-to-microsoft-intune-easy-with-upcoming-os-26-relea/4439895) on the Microsoft Community Hub. |

## How ADE works

Setting up ADE in Intune involves three main tasks:

1. **Get an enrollment program token**: Create a trust relationship between Intune and Apple Business. This is typically a one-time setup task per token. For steps, see [Set up a macOS ADE token](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-macos-token).
2. **Create and assign an enrollment policy**: Configure the enrollment experience for your Mac devices, including user affinity and Setup Assistant screens. Then assign the policy to device groups. For steps, see [Set up an enrollment policy for macOS](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-macos).
3. **Sync and distribute devices**: Sync device records from Apple Business to Intune, then distribute devices to users. Enrollment starts automatically through Apple Setup Assistant when a device is turned on. For steps, see [Manage macOS ADE devices and tokens](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/manage-devices-tokens-macos).

## Certificates

ADE supports the Automated Certificate Management Environment \(ACME\) protocol. When new devices enroll, the management profile from Intune receives an ACME certificate. ACME provides better protection than the SCEP protocol against unauthorized certificate issuance through robust validation mechanisms and automated processes, which helps reduce errors in certificate management.

Devices that are already enrolled don't receive an ACME certificate unless they re-enroll into Microsoft Intune. ACME is supported on macOS 13.1 or later.

## Before you begin

Before setting up ADE for macOS, ensure the following are in place:

- Access to [Apple Business](https://business.apple.com/) or [Apple School Manager](https://school.apple.com/).
- The [mobile device management authority](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/mdm-authority-set) set to Intune in your tenant.
- An [Apple MDM push certificate](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/create-mdm-push-certificate) in Intune.

## Next steps

- [Set up a macOS ADE token](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-macos-token)
- [Set up an enrollment policy for macOS](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-macos)
