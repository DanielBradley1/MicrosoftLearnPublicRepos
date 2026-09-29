<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/app-onboarding -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Automatically onboard Microsoft Entra ID apps to conditional access app control \(preview\)

All SaaS applications that exist in the Microsoft Entra ID catalog will be available automatically in the policy app filter. The following image shows the high-level process for configuring and implementing Conditional Access app control:

![Diagram of the process for configuring and implementing conditional access app control.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/caac-app-onboarding/process.png)

## Prerequisites

- Your organization must have the following licenses to use Conditional Access App Control:

  - Microsoft Defender for Cloud Apps

- Apps must be configured with single sign-on in Microsoft Entra ID

Fully performing and testing the procedures in this article requires that you have a session or access policy configured. For more information, see:

- [Create Microsoft Defender for Cloud Apps access policies](https://learn.microsoft.com/en-us/defender-cloud-apps/access-policy-aad)
- [Create Microsoft Defender for Cloud Apps session policies](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad)

## Supported Apps

All SaaS apps listed in the Microsoft Entra ID catalog will be available for filtering within the Microsoft Defender for Cloud Apps session and access policies. Each app chosen in the filter will automatically be onboarded into the system and will be controlled.

![Screenshot of the filter showing automatically onboarded apps.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/caac-app-onboarding/filter.png)

If an application isn't listed, you have the option to manually onboard it as outlined in the provided instructions.

**Note:** Dependency on Microsoft Entra ID Conditional Access policy:

All apps listed in the Microsoft Entra ID catalog will be available for filtering within Microsoft Defender for Cloud Apps session and access policies. However, only those applications that are included in Microsoft Entra ID's conditional policy with Microsoft Defender for Cloud Apps permissions will be actively managed within access or session policies.

When creating a policy, if the relevant Microsoft Entra ID's conditional policy is missing, an alert will appear, both during the policy creation process and upon saving the policy.

**Note:** To ensure that this policy runs as expected, we recommend checking the Microsoft Entra Conditional Access policies created in Microsoft Entra ID. You can see the full Microsoft Entra Conditional Access policies list in a banner on the create policy page.

![Screenshot of the recommendation shown in the portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/caac-app-onboarding/recommendation.png)

## Conditional Access App Control Configuration Page

Admins will be able to control app configurations such as:

- **Status:** App status - Disable or Enable
- **Policies:** Does at least one inline policy connect
- **IDP:** Onboarded app via IDP via Microsoft Entra or Non-MS IDP
- **Edit app:** Edit app configuration such as adding domains or disabling the app.

All apps that automatically onboarded will be set to "enabled" by default. Following the initial sign-in by a user, administrators will have the ability to view the application under **Settings** > **Connected apps** > **Conditional Access App Control apps**.

## Common App Misconfigurations

- [Second sign-in \(also known as 'second sign-in'\)](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-proxy#second-sign-in-also-known-as-second-login)
- [Missing domains](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-proxy#add-domains-for-your-app)
