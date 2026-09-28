<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/frontline/flw-setup-frontline-personal-devices?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-10 -->

# Set up frontline Teams on personal devices

Note

This feature will be retired on August 17, 2026. For more information please refer to Message Center post 1430529 in the Microsoft 365 admin center.

Note

Use a new test user account to evaluate this feature and validate your organization's first-time setup experience.

## Overview

The frontline Teams onboarding experience helps frontline workers set up Teams on their personal devices. This onboarding experience is available on the web and is intended for use on a desktop kiosk or shared PC at your work site. The steps in the experience update dynamically based on the security policies defined in your organization. If your policies change over time, the experience adapts automatically.

## How it works

<iframe src="https://www.youtube-nocookie.com/embed/Yz52WdwsbBs?si=bfBY3lbQ9vbgI2rs" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Scenarios supported

- You want to set up Microsoft Teams on a personal device. Supported devices include Android and iOS.
- MFA is required to access Teams on a personal device. The experiences optimizes for setting up Authenticator push notifications as the primary MFA method.
- App protection or configuration policies are enforced to access Teams on a personal device.

## Before you begin

Make sure you have:

- Your work username and password
- Access to a desktop kiosk or shared PC
- Your mobile phone

## Step 1: start onboarding

Note

For best results, use a private browsing session and close it after each setup.

On the desktop kiosk or back-office PC, open a web browser and navigate to [aka.ms/getfrontlineteams](https://flworchestrator.teams.microsoft.com/frontlinebyod?source=docs).

![Screenshot shows the user interface for the setup guide landing page.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/get-started.png?view=o365-worldwide)

Choose the device type that you're onboarding.

![Screenshot shows the user interface where you can select the Android or iOS device.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/choose-device.png?view=o365-worldwide)

Sign in with your work credentials.

Reset your default password if prompted.

## Step 2: download required apps

You could need to download extra apps such as Microsoft Authenticator and/or Company Portal based on your organization's security policies. These scenarios are supported by the setup experience:

#### Multifactor authentication \(MFA\)

1. You don't require MFA to access Teams.

   1. You'll skip the MFA setup step.

2. You'll require MFA to access Teams and you already have an MFA method setup.
3. You'll skip the MFA setup step.

   You require MFA to access Teams and the web experience is being accessed from a device that doesn't require MFA.

   ![Screenshot shows a QR code to download the Microsoft Authenticator app.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/get-authenticator.png?view=o365-worldwide)

   1. Download Microsoft Teams using the QR code.

4. You'll open the Microsoft Authenticator app and allow notifications.
5. You'll sign in with your work account and complete setup.
6. You'll come back and select next on the screen.
7. You require MFA to access Teams and the web experience is being access on a device that requires MFA.

   1. Follow the on-screen steps to set up MFA with the Microsoft Authenticator app in the setup experience.

      ![Screenshot of a message that extra steps are needed to keep the account secure.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/keep-account-secure.png?view=o365-worldwide)

      ![Screenshot displays the steps required to download the Microsoft Authenticator app.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/download-authenticator.png?view=o365-worldwide)

      ![Screenshot of the next step to set up Microsoft Authenticator.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/setup-authenticator.png?view=o365-worldwide)

      ![Screenshot of a QR code to register Microsoft Authenticator multifactor authentication on a mobile phone.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/register-authenticator.png?view=o365-worldwide)

      ![Screenshot shows the experience of trying Microsoft Authenticator push notifications.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/try-authenticator.png?view=o365-worldwide)

      ![Screenshot indicates that Microsoft Authenticator is now set up.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/authenticator-added.png?view=o365-worldwide)

#### App protection policies and/or app configuration policies

If your organization uses app protection policies, app configuration policies, and/or conditional access policies with Microsoft Teams, you might need the Company Portal app on your device.

- If you have an iOS device, you won't see this step.
- If you have an Android device, you see a screen to download Company Portal.

  ![Screenshot displays a QR code along with instructions for downloading the Company Portal app.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/get-company-portal.png?view=o365-worldwide)

#### Download Microsoft Teams

Next, you'll see a screen to download Microsoft Teams.

- Download Microsoft Teams using the QR code.
- Sign in and click **Done** when finished.
- Sign out when prompted.
- Close the browser.

  ![Screenshot shows a QR code for downloading Microsoft Teams and includes sign-in instructions.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/setup-frontline-teams-on-personal-devices/get-teams.png?view=o365-worldwide)

## Troubleshooting

- If the QR code doesn't work, manually search for each app in your devices app store.

## FAQ

Q: Can this experience help me enroll my device in Intune?

A: No. This feature doesn't guide you through the device enrollment process. Follow the steps on your mobile phone.

Q: Can I go backward in the setup experience?

A: You should always move forward in the setup experience. Navigating backward can cause errors.
