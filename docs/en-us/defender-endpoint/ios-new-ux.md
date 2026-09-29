<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/ios-new-ux -->
<!-- Sitemap-Last-Modified: 2026-07-22 -->

# User Experiences in Microsoft Defender for Endpoint on iOS

As part of our ongoing commitment to deliver exceptional user experiences, we're excited to announce a series of upcoming changes to the user interface and overall experience of our **Microsoft Defender for Endpoint** mobile app.

The new enhancements are designed to improve usability, streamline navigation, and ensure our app meets the evolving needs of our users.

## Key changes - November 2025

In this release, we've made it easier for users to share feedback, including logs, to the Microsoft Defender team. The changes include:

- [A new bottom pane that makes it easier for users to share feedback and logs](#bottom-pane-experience)
- [A new **Send logs to Microsoft** option that enables users to quickly send logs to Microsoft](#one-click-send-logs-experience)

### Bottom pane experience

When users select **Help and Feedback** in the left navigation pane \(Screen 1, accessible by tapping the profile picture\), a new bottom feedback pane opens \(Screen 2\). This pane has been updated to improve readability and make it easier for users to share feedback.

The **Send feedback** option in the updated bottom pane enables users to share positive or negative feedback, along with Microsoft Defender and authenticator logs, which will be accessible to the Microsoft Defender team. When a user selects **Send feedback**, they're redirected to a new screen \(Screen 3\) where they can include logs along with their feedback submission.

![Screenshots showing how to send feedback and logs from the Microsoft Defender mobile app options menu.](https://learn.microsoft.com/en-us/defender-endpoint/media/ios-new-ux/bottom-experience-ios.png)

### One-click *Send Logs* experience

A new **Send logs to Microsoft** option has been added directly to the left navigation pane \(Screen 1\). This enables users to quickly send logs to Microsoft. It redirects them to the logs submission page \(Screen 2\). This option is particularly useful when a support case has been created and a support engineer is assigned, providing a convenient way for users to submit logs. Because this option doesn't allow users to include written feedback, the Defender team won't have access to the logs unless the incident ID is explicitly shared via mail or support request. This option only collects logs from the Defender app - it won't include logs from the Authenticator app.

![Screenshots showing how to send logs directly to Microsoft from the Microsoft Defender mobile app options menu.](https://learn.microsoft.com/en-us/defender-endpoint/media/ios-new-ux/one-click-feedback-ios.png)

## Key changes - Previous

We're pleased to introduce the **Device Protection** feature card for our enterprise users that includes Web Protection, Device Health and Jail break feature that has been designed to be more user-friendly and accessible. The updated feature cards now include recommendation cards. The first recommendation card will prominently display any active alerts, ensuring you stay informed. Additionally, a list of features will now be presented in the form of tiles as a part of L2 screens enhancing ease of use and navigation.

**The main changes involved are**:

- [Main dashboard changes](#main-dashboard-changes)
- [List the features inside one feature card](#list-the-features-inside-one-feature-card)
- [Detailed features experience](#detailed-feature-experience)
- [Recommendation cards for alerts](#recommendation-cards-for-alerts)
- [Onboarding screens](#onboarding-screens)

### Main Dashboard changes

The main Dashboard screen that appears for enterprise users as per our latest rollout of enhancements to the application.

[![Screenshot that shows the Microsoft Defender for Endpoint Mobile Dashboard on iOS devices before the new update.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-main-dash-new.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-main-dash-new.png#lightbox)

### List the features inside one feature card

One feature card called **Device Protection** lists Web Protection, Device Health, and Jail Break. Previously, the dashboard had one card for each set of capabilities. In the new experience, only the Device Protection card changes.

[![Screenshot that shows the Microsoft Defender for Endpoint Feature Card.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-list-new.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-list-new.png#lightbox)

### Detailed feature experience

We updated all the subordinating screens associated with the **Device Protection** feature

1. **Web Protection**

   [![Screenshot that shows the web protection feature on the Defender for Endpoint on iOS app.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-web-protection-new.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-web-protection-new.png#lightbox)
2. **Device Health**

   Note

   Microsoft is deprecating the Device Health feature. Deprecation begins in mid-July 2026 and finishes by late July 2026.

   [![Screenshot that shows the new device health feature on the Defender for Endpoint on iOS app.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-device-health-new.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-device-health-new.png#lightbox)

### Recommendation cards for alerts

The structure of the dashboard is updated to include a recommendation card that contains active alerts \(if any\). In case there are multiple alerts, resolving the top alert brings forward the next one. Recommendation cards are implemented to provide a more cohesive user experience. These cards are designed to display important alerts and notifications prominently on the dashboard. Here are a few examples:

1. **Web Protection**

   [![Screenshot that shows the web protection recommendation card feature on the Defender for Endpoint on iOS app.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-web-protection-rec-card.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-web-protection-rec-card.png#lightbox)
2. **Device Health \(iOS Update\)**

   Note

   Starting late July 2026, the Device Health \(iOS Update\) recommendation card no longer appears.

   [![Screenshot that shows the device health recommendation card feature on the MDE iOS app.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-device-health-rec-card.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-device-health-rec-card.png#lightbox)

### Onboarding screens

This section details these changes:

- VPN Permission flow while Onboarding
- VPN Permission flow after Onboarding
- TVM EUPI Screen

### VPN permission flow while onboarding

This is the main VPN Permission screen that appears to the enterprise's users as per our latest rollout of enhancements in the application.

#### Before

[![Screenshot that shows the Microsoft Defender for Endpoint mobile iOS setup before the new update.](https://learn.microsoft.com/en-us/defender-endpoint/media/ios-vpn-before.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-main-dash-new.png#lightbox)

#### Now

[![Screenshot that shows the Microsoft Defender for Endpoint mobile iOS setup after the new update.](https://learn.microsoft.com/en-us/defender-endpoint/media/ios-vpn-after.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-main-dash-new.png#lightbox)

### VPN permission flow after onboarding

This screen is seen when the VPN configuration is deleted from user's device, and the VPN needs to be re-enabled.

[![Screenshot that shows the Microsoft Defender for Endpoint mobile iOS re-enable screen.](https://learn.microsoft.com/en-us/defender-endpoint/media/ios-vpn-re-enable.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-list-new.png#lightbox)

### TVM EUPI screen

We've enhanced the TVM EUPI screen as made it align with our current code flow.

#### Before

[![Screenshot that shows the Microsoft Defender for Endpoint mobile iOS TVM EUPI screen before the new update.](https://learn.microsoft.com/en-us/defender-endpoint/media/ios-tvm-before.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-main-dash-new.png#lightbox)

#### Now

[![Screenshot that shows the Microsoft Defender for Endpoint mobile iOS TVM EUPI after the new update.](https://learn.microsoft.com/en-us/defender-endpoint/media/ios-tvm-after.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-ios-main-dash-new.png#lightbox)
