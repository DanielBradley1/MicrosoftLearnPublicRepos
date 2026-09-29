<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/conditional-access-app-control-how-to-overview -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Use Defender for Cloud Apps Conditional Access app control

Use Microsoft Defender for Cloud Apps Conditional Access app control to create access and session policies that monitor and control user access to cloud apps in real time. This guide walks through onboarding your apps, setting up a Conditional Access policy, and creating and testing your access and session policies. Before you begin, make sure you meet the [prerequisites](#prerequisites).

## Conditional Access app control usage flow \(Preview\)

The following image shows the high level process for configuring and implementing Conditional Access app control:

[![Diagram of the Conditional Access app control process flow.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/conditional-access-app-control-how-to-overview/conditional-access-policy-flow.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/conditional-access-app-control-how-to-overview/conditional-access-policy-flow.png#lightbox)

## Which identity provider are you using?

Before you start using Conditional Access app control, understand whether your apps are managed by Microsoft Entra or another identity provider \(IdP\).

- **Microsoft Entra apps** are automatically onboarded for Conditional Access app control and are immediately available for you to use in your access and session policy conditions \(Preview\). Microsoft Entra apps can also be manually onboarded before you select them in your access and session policy conditions.
- **Apps that use non-Microsoft IdPs** must be manually onboarded before you can select them in your access and session policy conditions.

  - If you're working with a catalog app from a non-Microsoft IdP, configure the integration between your IdP and Defender for Cloud Apps to onboard all catalog apps. For more information, see [Onboard non-Microsoft IdP catalog apps for Conditional Access app control](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-deployment-featured-idp).
  - If you're working with custom apps, you need to both configure the integration between your IdP and Defender for Cloud Apps, and also onboard each custom app. For more information, see [Onboard non-Microsoft IdP custom apps for Conditional Access app control](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-deployment-any-app-idp).

### Sample procedures

The following articles provide sample processes for configuring a non-Microsoft IdP to work with Defender for Cloud Apps:

- [PingOne as your IdP](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-idp-pingone)
- [Active Directory Federation Services \(AD FS\) as your IdP](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-idp-adfs)
- [Okta as your IdP](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-idp-okta)

## Prerequisites:

Before you configure Conditional Access app control, make sure the following prerequisites are met:

1. Make sure your firewall allows traffic from all IP addresses listed in [Network requirements](https://learn.microsoft.com/en-us/defender-cloud-apps/network-requirements).
2. Check that your app has a full certificate chain. Missing parts of the chain can cause unexpected app behavior with Conditional Access app control policies.

## Create a Microsoft Entra ID Conditional Access policy

Access and session policies need a Conditional Access policy in Microsoft Entra ID. This policy controls traffic to your cloud apps.

For steps to create one, see the [access policy](https://learn.microsoft.com/en-us/defender-cloud-apps/access-policy-aad) and [session policy](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad) guides.

To learn more, see [Conditional Access policies](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview) and [Building a Conditional Access policy](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policies).

## Create your access and session policies

After you've confirmed that your apps are onboarded, either automatically because they're Microsoft Entra ID apps, or manually, and you have a Microsoft Entra ID Conditional Access policy ready, you can continue with creating access and session policies for any scenario you need.

For more information, see:

- [Create a Defender for Cloud Apps access policy](https://learn.microsoft.com/en-us/defender-cloud-apps/access-policy-aad#create-a-defender-for-cloud-apps-access-policy)
- [Create a Defender for Cloud Apps session policy](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad#create-a-defender-for-cloud-apps-session-policy)

## Test your policies

Make sure to test your policies and update any conditions or settings as needed. For more information, see:

- [Test your access policy](https://learn.microsoft.com/en-us/defender-cloud-apps/access-policy-aad#test-your-policy)
- [Test your session policy](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad#test-your-policy)

## Related content

For more information, see [Protect apps with Microsoft Defender for Cloud Apps Conditional Access app control](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-intro-aad).
