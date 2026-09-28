<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/multi-factor-authentication-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Frequently asked questions about Microsoft Entra multifactor authentication

This FAQ answers common questions about Microsoft Entra multifactor authentication and using the multifactor authentication service. It's broken down into questions about the service in general, billing models, user experiences, and troubleshooting.

## General

### What short codes are used for sending text messages to my users?

We use the short codes listed in the following table to send text messages to users for multifactor authentication. The short codes used depend on the country or region where the user is located.

| Country/Region | Short codes |
| --- | --- |
| United States of America | 26096  <br>51789  <br>69829  <br>85873  <br>87892  <br>97671  <br>99399  <br>673803 |
| Canada | 20873  <br>37107  <br>97671  <br>673803  <br>759731 |
| Italy | 39439000927  <br>394390009264 |

There's no guarantee of consistent text message or voice-based multifactor authentication prompt delivery by the same number. In the interest of our users, we may add or remove short codes at any time as we make route adjustments to improve text message deliverability.

We don't support short codes for countries or regions besides the United States and Canada.

### Does Microsoft Entra multifactor authentication throttle user sign-ins?

Yes, in certain cases that typically involve repeated authentication requests in a short time window, Microsoft Entra multifactor authentication throttles user sign-in attempts to protect telecommunication networks, mitigate MFA fatigue-style attacks and protect its own systems for the benefit of all customers.

Although we don't share specific throttling limits, they're based around reasonable usage.

### Is my organization charged for sending the phone calls and text messages that are used for authentication?

No, you're not charged for individual phone calls placed or text messages sent to users through Microsoft Entra multifactor authentication.

Your users might be charged for the phone calls or text messages they receive, according to their personal phone service.

## Manage and support user accounts

### What should I tell my users to do if they don't receive a response on their phone?

Have your users attempt up to five times in 5 minutes to get a phone call or text message for authentication. Microsoft uses multiple providers for delivering calls and text messages. If this approach doesn't work, open a support case to troubleshoot further.

Third-party security apps may also block the verification code text message or phone call. If using a third-party security app, try disabling the protection, then request another MFA verification code be sent.

If the prior steps don't work, check if users are configured for more than one verification method. Try signing in again, but select a different verification method on the sign-in page.

For more information, see the [end-user troubleshooting guide](https://support.microsoft.com/account-billing/common-problems-with-two-step-verification-for-a-work-or-school-account-63acbb9b-16a1-47b9-8619-6a865e8071a5).

### What should I do if one of my users can't get in to their account?

You can reset the user's account by making them to go through the registration process again. Learn more about [managing user and device settings with Microsoft Entra multifactor authentication in the cloud](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-userdevicesettings).

### My users say that sometimes they don't receive the text message or the verification times out.

Delivery of text messages isn't guaranteed because uncontrollable factors might affect the reliability of the service. These factors include the destination country or region, the mobile phone carrier, and the signal strength.

Third-party security apps may also block the verification code text message or phone call. If using a third-party security app, try disabling the protection, then request another MFA verification code be sent.

If your users often have problems with reliably receiving text messages, tell them to use the Microsoft Authenticator app or phone call method instead. The Microsoft Authenticator can receive notifications both over cellular and Wi-Fi connections. In addition, the mobile app can generate verification codes even when the device has no signal at all. The Microsoft Authenticator app is available for [Android](https://go.microsoft.com/fwlink/?Linkid=825072), [iOS](https://go.microsoft.com/fwlink/?Linkid=825073), and [Windows Phone](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6).

### Why are my users being prompted to register their security information?

There are several reasons that users could be prompted to register their security information:

- The user has been enabled for MFA by their administrator in Microsoft Entra ID, but doesn't have security information registered for their account yet.
- The user has been enabled for self-service password reset in Microsoft Entra ID. The security information will help them reset their password in the future if they ever forget it.
- The user accessed an application that has a Conditional Access policy to require MFA and hasn't previously registered for MFA.
- The user is registering a device with Microsoft Entra ID \(including Microsoft Entra join\), and your organization requires MFA for device registration, but the user hasn't previously registered for MFA.
- The user is generating Windows Hello for Business in Windows 10 \(which requires MFA\) and hasn't previously registered for MFA.
- The organization has created and enabled an MFA Registration policy that has been applied to the user.
- The user previously registered for MFA, but chose a verification method that an administrator has since disabled. The user must therefore go through MFA registration again to select a new default verification method.

## Errors

### What should users do if they see an "Authentication request isn't for an activated account" error message when using mobile app notifications?

Ask the user to complete the following procedure to remove their account from the Microsoft Authenticator, then add it again:

1. Go to [their account profile](https://account.activedirectory.windowsazure.com/profile/) and sign in with an organizational account.
2. Select **Additional Security Verification**.
3. Remove the existing account from the Microsoft Authenticator app.
4. Select **Configure**, and then follow the instructions to reconfigure the Microsoft Authenticator.

### What should users do if they see a 0x800434D4L error message when signing in to a nonbrowser application?

The *0x800434D4L* error occurs when you try to sign in to a nonbrowser application, installed on a local computer, that doesn't work with accounts that require two-step verification.

A workaround for this error is to have separate user accounts for admin-related and nonadmin operations. Later, you can link mailboxes between your admin account and nonadmin account so that you can sign in to Outlook by using your nonadmin account. For more details about this solution, learn how to [give an administrator the ability to open and view the contents of a user's mailbox](https://help.outlook.com/141/gg709759.aspx?sl=1).

## Next steps

If your question isn't answered here, the following support options are available:

- Search the [Microsoft Support Knowledge Base](https://support.microsoft.com) for solutions to common technical issues.
- Search for and browse technical questions and answers from the community, or ask your own question in the [Microsoft Entra Q&A](https://learn.microsoft.com/en-us/answers/topics/azure-active-directory.html).
- Contact Microsoft professional through [Multifactor Authentication Server support](https://support.microsoft.com/oas/default.aspx?prid=14947). When contacting us, it's helpful if you can include as much information about your issue as possible. Information you can supply includes the page where you saw the error, the specific error code, the specific session ID, and the ID of the user who saw the error.
