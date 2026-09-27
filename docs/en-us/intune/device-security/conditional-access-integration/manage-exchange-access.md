<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/manage-exchange-access -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Protect Microsoft 365 Exchange Online without requiring device management

When you use Microsoft Intune, you can still manage employee access to their work email through Microsoft 365 Exchange Online without the overhead of enrolling their devices. This limited access through Exchange Online for unenrolled devices can be accomplished using app-based Conditional Access policies.

To complete the necessary steps, confirm you have licenses for Microsoft 365, or Microsoft Entra ID P1 and Intune. Employees need to have a [supported iOS/iPadOS or Android device](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms).

If you decide to set up a device management system, you can, as this type of app protection works independently of device management.

## Action plan

1. [Learn about Conditional Access](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/overview).
2. [Learn about app-based Conditional Access](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/app-based-policies).
3. [Set up app-based Conditional Access policies for Exchange Online](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/create-app-based-policy).
4. [Block apps that can't be managed](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/block-no-modern-auth). Specifically, block apps that don't use the Microsoft Authentication Library \(MSAL\).
5. \(Optional\) [Set up app-based Conditional Access policies for SharePoint Online](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/create-app-based-policy). These policies block access to your company data from apps that can't be managed and secured. The policies also limit access through SharePoint mobile.

## What to tell employees and students

- Ask your employees and students to download and install Microsoft Outlook or Microsoft SharePoint for iOS/iPadOS from the Apple App Store or for Android from the Google Play Store.
- If you block access to apps that don't use modern authentication, let the employees and students know of this restriction.

## Next steps

You have used app-based Conditional Access to increase the security of company data. As part of next steps, you can learn more about the other ways you can increase the protection of your company's data, including:

- Setting up app protection policies to help you protect your company data against intentional or accidental data leaks.
- Use of Azure Information Protection to protect company data outside your network.

Want help with enabling this or other EMS or Microsoft 365 scenarios? If you have at least 150 licenses for Microsoft 365, Enterprise Mobility + Security, or Microsoft Entra ID P1, use your [FastTrack benefits](https://learn.microsoft.com/en-us/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program).
