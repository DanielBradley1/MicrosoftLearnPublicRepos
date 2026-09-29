<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mtd -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# Microsoft Defender for Endpoint mobile threat defense on Android and iOS

Microsoft Defender for Endpoint on Android and iOS is our **mobile threat defense \(MTD\)** solution. Companies are often proactive in protecting computers from vulnerabilities and attacks, but mobile devices often go unmonitored and unprotected. Although mobile platforms have some built-in protection \(for example, app isolation and vetted consumer app stores\), these platforms remain vulnerable to web-based or other sophisticated attacks. As more people use devices to access sensitive work information, it's imperative that companies deploy an MTD solution to protect devices and resources.

Note

This overview covers the Microsoft Defender for Endpoint mobile threat defense solution. Don't confuse it with the Android Mobile Threat Defense \(MTD\) Role, which is an Android Enterprise platform role that you assign to Defender for Endpoint for additional platform-level protections. For more information, see [Android Mobile Threat Defense \(MTD\) Role for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/android-mobile-threat-defense-role).

Microsoft Defender for Endpoint on Android and iOS provides the following key capabilities:

| Capability | Description |
| --- | --- |
| Web Protection | Anti-phishing, blocking unsafe network connections, and support for custom indicators for URLs and domains. \(File and IP indicators aren't currently supported.\) |
| Malware Protection \(Android-only\) | Scanning for malicious apps, APK files, and non-APK files, such as documents, archives, and scripts. For more information, see [Configure non-APK file scanning](https://learn.microsoft.com/en-us/defender-endpoint/android-configure#configure-non-apk-file-scanning). |
| Jailbreak Detection \(iOS-only\) | Detection of jailbroken devices. |
| Root Detection \(Android - Preview\) | Detection of rooted devices. |
| Microsoft Defender Vulnerability Management \(MDVM\) | Vulnerability assessment of onboarded mobile devices. Includes OS and Apps vulnerabilities assessment for both Android and iOS. For more information, see [What is Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management). |
| Network Protection | Protection against rogue Wi-Fi related threats and rogue certificates; ability to add to the "allow" list the root CA and private root CA certificates in Intune; establish trust with endpoints. |
| Unified alerting | Alerts from all platforms in the unified Microsoft Defender portal. |
| Conditional Access, Conditional launch | Blocking risky devices from accessing corporate resources. Defender for Endpoint risk signals can also be added to app protection policies \(MAM\). |
| Privacy Controls | Configure privacy in the threat reports by controlling the data sent by Microsoft Defender for Endpoint. Privacy controls are available for admin and end users. It's there for enrolled and unenrolled devices as well. |
| Integration with Microsoft Tunnel | Integration with Microsoft Tunnel, a VPN gateway solution to enable security and connectivity in a single app. Available on both Android and iOS. |

These capabilities are available for Microsoft Defender for Endpoint license holders. For more information, see [Licensing requirements](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements).

For information about the latest features and benefits, read our [announcements](https://aka.ms/mdeblog).

## Overview and Deploy

The procedures in this article require Microsoft Intune. Intune is a separate product that isn't part of Microsoft Defender for Endpoint, and it isn't included in all subscriptions. To use Intune, you need a subscription that includes it, or you can buy it separately as a standalone subscription or add-on. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses).

Watch this video for a quick overview of MTD capabilities and deployment:

<iframe src="https://learn-video.azurefd.net/vod/player?id=c944a31c-0017-4707-a1bc-afff9e2f2e00" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

### Onboarding devices already enrolled in Intune

Devices that are already enrolled in Microsoft Intune can be onboarded to Microsoft Defender for Endpoint without requiring re-enrollment. After you install the Defender app and assign the required configuration profiles, the device automatically completes onboarding.

#### Android \(Intune-enrolled devices\)

1. Ensure the device is already enrolled in Intune under one of the supported Android Enterprise scenarios.
2. Deploy the Microsoft Defender for Endpoint app through Intune.
3. Assign the Microsoft Defender for Endpoint configuration profile:

   - Web protection
   - Network protection
   - App protection \(if applicable\)


   The device automatically onboards when the Defender app receives the configuration.

4. Use Conditional Access to enforce user onboarding as required.

#### iOS/iPadOS \(Intune-enrolled devices\)

1. Ensure the device is enrolled using ADE<sup>\*</sup>, Apple Configurator<sup>\*</sup>, device enrollment, or user enrollment.
2. Deploy Microsoft Defender for Endpoint through Intune.
3. Assign the Defender for Endpoint configuration policies for:

   - Web protection
   - Network protection
   - Zero-touch onboarding \(for supervised devices\)

<sup>\*</sup> After the policies are delivered, the app automatically configures and onboards the device without user interaction.

Note

You don't need to re-enroll existing Intune-enrolled devices. Onboarding occurs automatically after the Defender app and MTD configuration policies are delivered to the device.

### Deploy

The following table summarizes how to deploy Microsoft Defender for Endpoint on Android and iOS. For detailed documentation, see the following articles:

- [Overview of Microsoft Defender for Endpoint on Android](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-android), and
- [Overview of Microsoft Defender for Endpoint on iOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-ios)

## Supported Android enrollment scenarios

| Scenarios | Company portal app required on the device? | Protection Profile/Prerequisites | How to deploy |
| --- | --- | --- | --- |
| Android Enterprise personally owned devices using a work profile | Yes | Protects only the work profile section. [Learn more about the work profile](https://learn.microsoft.com/en-us/intune/intune-service/apps/android-deployment-scenarios-app-protection-work-profiles) | [Microsoft Intune: Deploy and configure Microsoft Defender for Endpoint on Android](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-deploy-android) |
| Android Enterprise personally owned devices using a personal profile | Yes | Protects the personal profile. When a customer also has a work profile, it protects the entire device.<br><br>- The company portal app must be enabled on personal profile.<br>- Microsoft Defender must be already installed and active in the work profile to enable Microsoft Defender in the personal profile. | [Microsoft Intune: Deploy and configure Microsoft Defender for Endpoint on Android](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-deploy-android) |
| Android Enterprise corporate owned work profile \(COPE\) | Yes | Protects only the work profile section. The Company Portal app and Microsoft Intune app both are automatically installed. | [Microsoft Intune: Deploy and configure Microsoft Defender for Endpoint on Android](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-deploy-android) |
| Android Enterprise corporate owned fully managed - no work profile \(COBO\) | Yes | Protects the entire device. The Company Portal app and Microsoft Intune app both are automatically installed. | [Microsoft Intune: Deploy and configure Microsoft Defender for Endpoint on Android](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-deploy-android) |
| MAM | Yes \(installed; setup isn't required\) | Protects only enrolled apps. MAM supports with/without Device enrollment or enrolled with non-Microsoft Enterprise Mobility Management. | [Configure Microsoft Defender for Endpoint on Android risk signals using App Protection Policies \(MAM\)](https://learn.microsoft.com/en-us/defender-endpoint/android-configure-mam) |
| Device Administrator \(Deprecated on 31 December 2024\) | Yes | Intune and Defender for Endpoint ended support for Android device administrator management on devices with access to Google Mobile Services \(GMS\) in December 2024. | [Microsoft Intune: Deploy and configure Microsoft Defender for Endpoint on Android](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-deploy-android) |

### Unsupported Android enrollment scenarios

These scenarios aren't currently supported:

- **Android Enterprise corporate-owned Personal profile**
- **Android Enterprise corporate owned dedicated devices \(COSU\) \(Kiosk/Shared\)**
- **Android Open-Source Project \(AOSP\)**

### Android low touch onboarding supported scenarios

- Android Enterprise personally owned devices using a work profile.
- Android Enterprise corporate owned work profile \(COPE\).
- Android Enterprise corporate owned fully managed - No work profile \(COBO\).

## Supported iOS enrollment scenarios

| Scenarios | Company portal app required on the device? | Protection Profile/Prerequisites | How to deploy |
| --- | --- | --- | --- |
| Supervised Devices \(ADE and Apple Configurator Enrollment\) | Yes | Protects the entire device. For ADE, if users who use Just in Time \(JIT\) registration, the Company portal app isn't required because app enrolls the device automatically by connecting to Intune server | [Deploy Microsoft Defender for Endpoint on iOS with Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/ios-install#deployment-steps-applicable-for-both-supervised-and-unsupervised-devices) |
| Unsupervised Devices \(Device Enrollment\) | Yes | Protects the entire device. For web-based device enrollment, the company portal app isn't required because after the managed app signs in, the app downloads configuration policies directly and not the company portal app | [Deploy Microsoft Defender for Endpoint on iOS with Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/ios-install#deployment-steps-applicable-for-both-supervised-and-unsupervised-devices) |
| Unsupervised Devices \(User Enrollment\) | Yes | Protects the entire device. The exception is TVM capability, where only the work apps pushed by the admin are protected. Web protection works at device level and scans network traffic from all apps. | [Deploy Microsoft Defender for Endpoint on iOS with Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/ios-install#user-enrollment-setup-only-for-intune-user-enrolled-devices) |
| MAM | No | Protects only enrolled apps. The VPN has access to entire device and can scan all app traffic | [Deploy Microsoft Defender for Endpoint on iOS with Mobile Application Management](https://learn.microsoft.com/en-us/defender-endpoint/ios-install-unmanaged) |

### Unsupported iOS enrollment scenarios

iOS Dedicated/shared/kiosk device enrollment isn't supported.

### iOS zero touch onboarding supported scenarios

- Supervised devices \(ADE and Apple Configurator Enrollment\)
- Unsupervised devices \(Device Enrollment\)

### End-user onboarding

- [Configure Zero-touch onboard for iOS enrolled devices](https://learn.microsoft.com/en-us/defender-endpoint/ios-install#zero-touch-silent-onboarding-to-defender-for-endpoint): Admins can configure zero-touch install to silently onboard Microsoft Defender for Endpoint on enrolled iOS devices without requiring the user to open the app.
- [Configure Conditional Access to enforce user onboarding](https://learn.microsoft.com/en-us/defender-endpoint/android-configure#conditional-access-with-defender-for-endpoint-on-android): You can apply Conditional Access ensure users onboard to the Microsoft Defender for Endpoint app after deploying. Watch this video for a quick demo on configuring conditional access with Defender for Endpoint risk signals.

  <iframe src="https://learn-video.azurefd.net/vod/player?id=eac95cd5-17b0-47ca-8819-41d7d5247af9" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

### Simplify onboarding

- [iOS - Zero-Touch Onboard](https://learn.microsoft.com/en-us/defender-endpoint/ios-install#zero-touch-silent-onboarding-to-defender-for-endpoint)
- [Microsoft Intune: Android Enterprise - Setup Always-on VPN](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-deploy-android#set-up-always-on-vpn)
- [iOS - Autosetup of VPN profile](https://learn.microsoft.com/en-us/defender-endpoint/ios-install#auto-onboarding-of-vpn-profile-simplified-onboarding)

## Pilot evaluation

While evaluating mobile threat defense with Microsoft Defender for Endpoint, you can verify that certain criteria is met before proceeding to deploy the service to a larger set of devices. You can define the exit criteria and ensure that they're satisfied before deploying widely.

This method helps reduce potential issues that could arise while rolling out the service. Here are some tests and exit criteria that might help:

- Devices show up in the device inventory list: After successful onboarding of Defender for Endpoint on the mobile device, verify that the device is listed in the Device Inventory in the [Microsoft Defender portal](https://security.microsoft.com).

- Run a phishing test: Browse to `https://smartscreentestratings2.net` and verify that it gets blocked by Microsoft Defender for Endpoint. On Android Enterprise with a work profile, only the work profile is supported.
- Alerts appear in dashboard: Verify that alerts for the detection tests mentioned earlier appear in the [Microsoft Defender portal](https://security.microsoft.com).

Need help with deploying or configuring Defender for Endpoint on Android & iOS? If you have at least 150 licenses for the product, use your [FastTrack benefits](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/introduction). Learn more about FastTrack at [Microsoft FastTrack](https://fasttrack.microsoft.com/).

## Configure

- [Configure Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
- [Configure Web Protection without VPN for supervised iOS devices](https://learn.microsoft.com/en-us/defender-endpoint/ios-install#complete-deployment-for-supervised-devices)

## Resources

- [Android Mobile Threat Defense \(MTD\) Role for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/android-mobile-threat-defense-role)
- [Microsoft Defender for Endpoint on Android](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-android)
- [Microsoft Defender for Endpoint on iOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-ios)
- Stay informed about upcoming releases by reading our [announcements](https://aka.ms/mdeblog).
