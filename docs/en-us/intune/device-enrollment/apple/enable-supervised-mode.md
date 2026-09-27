<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/enable-supervised-mode -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Turn on iOS/iPadOS supervised mode

Apple iOS/iPadOS supervised mode gives administrators more options when managing Apple devices, making it useful for corporate-owned devices deployed at scale. For example, you can restrict AirDrop or prevent users from changing the name of the device. For a list of settings which require supervised mode, see [iOS device restriction settings in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-apple).

Intune supports supervised mode as part of the Apple [Device Enrollment Program \(DEP\)](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-ios).

For a list of Apple controls that require supervision, see Apple's [Payload settings reference](https://support.apple.com/guide/deployment/dep2c1b2a43a/web).

## Turn on supervised mode after enrollment

After enrollment, the only way to turn on supervised mode is to connect an iOS/iPadOS device to a Mac and [use the Apple Configurator](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-configurator-ios) \(which will reset the device\). You can't configure a device for supervised mode in Intune after enrollment.

Apple Configurator for iPhone can also be used to supervise devices. For more information, see the [Apple support doc](https://support.apple.com/apple-configurator).

## Identify a supervised device

To determine if a device is supervised, check the **Settings** app.

Users are notified that their devices are supervised in the **Settings** app. In the app at the top of the screen, a static message shows the message **This iPhone is supervised and managed by *`<your organization>`***.

## Next steps

For other device management options, see [What is Microsoft Intune?](https://learn.microsoft.com/en-us/intune/fundamentals/what-is-intune)
