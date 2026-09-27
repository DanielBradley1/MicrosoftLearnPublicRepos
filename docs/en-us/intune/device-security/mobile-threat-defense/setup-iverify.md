<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-iverify -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Integrate iVerify Enterprise with Microsoft Intune

Complete the following steps to integrate the iVerify Enterprise platform with Intune.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Before you begin

Before starting the process of integrating iVerify Enterprise with Intune, make sure you have the following configurations:

- **Microsoft Intune Plan 1 subscription**
- **Microsoft Entra admin credentials** to grant the following permissions:

  - Sign in and read user profile
  - Access the directory as the signed-in user
  - Read directory data
  - Send device information to Intune

- **Admin credentials** to access the iVerify Admin Console

## iVerify Enterprise app authorization

The iVerify Enterprise app authorization process consists of the following steps:

1. Sign in to the **iVerify Enterprise Admin Console**.
2. Navigate to **Integrations** and select **Microsoft Intune Mobile Threat Defense**.
3. When prompted, choose **Accept** to authorize the iVerify MTD app to communicate with Intune and Microsoft Entra ID.
4. Once authorization is complete, configure device policies within the **iVerify Enterprise Admin Console** to define and manage device threat levels across your fleet.

## To set up iVerify Enterprise integration

For step-by-step setup guidance, see [Connecting iVerify Enterprise with Microsoft Intune](https://edr.iverify.io/docs/iverify-portal-guide/Integrations/intune-mtd) in the iVerify documentation.

Note

You'll need to sign in with your iVerify Admin Console credentials to view the documentation.

## Related content

- [Mobile Threat Defense with Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/overview)
- [Enable mobile threat connectors in Intune](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector)
