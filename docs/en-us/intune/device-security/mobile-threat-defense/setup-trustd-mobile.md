<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-trustd-mobile -->
<!-- Sitemap-Last-Modified: 2026-09-14 -->

# Integrate Trustd Mobile with Microsoft Intune

Complete the following steps to integrate the Trustd Mobile solution with Intune. The instructions in this article are performed in the [Trustd Mobile console](https://control.traced.app/devices/zero-trust/intune).

## Before you begin

Before starting the process of integrating Trustd Mobile with Intune, make sure you have the following configurations:

- Microsoft Intune Plan 1 subscription
- Microsoft Entra admin credentials to grant the following permissions:

  - Sign in and read user profile
  - Access the directory as the signed-in user
  - Read directory data
  - Send device information to Intune

- Admin credentials to access the Trustd Mobile console

## Trustd Mobile app authorization

The Trustd Mobile app authorization process consists of the following steps:

1. Go to the [Trustd Mobile console](https://control.traced.app/devices/zero-trust/intune) and sign in with your credentials.
2. Choose **Settings** from the top bar.
3. Choose **Integrations** from the left bar.
4. Under **Microsoft Intune**, select **Authorise now**.
5. Authenticate to Microsoft and add the Trustd Mobile Intune Connector app.

Important

To perform the Trustd Mobile integration setup, you must sign in with a Microsoft Entra user who has the Global Administrator role. This one-time setup operation uses the Global Administrator rights to grant permission in your organization for the Trustd Mobile apps to communicate with Intune.

## Set up Trustd Mobile integration

For step-by-step setup guidance, see [Microsoft Intune – Zero Trust Conditional Access](https://traced.app/getting-started-guide-unmanaged-customer/#step12) in the Trustd Mobile documentation.

## Related content

- [Mobile Threat Defense with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/overview)
- [Enable mobile threat connectors in Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)
