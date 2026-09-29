<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-jamf -->
<!-- Sitemap-Last-Modified: 2026-09-19 -->

# Deploy Microsoft Defender for Endpoint on macOS with Jamf Pro

You can use Jamf Pro to deploy the Microsoft Defender for Endpoint installation package and required configuration profiles to organization-owned macOS devices.

Jamf Pro is a separate product that isn't part of Defender for Endpoint and isn't included with Defender for Endpoint subscriptions. To use these procedures, your organization needs a separate Jamf Pro subscription. For product and subscription information, see [Jamf Pro](https://www.jamf.com/products/jamf-pro/). To compare this method with [Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune), [another mobile device management \(MDM\) solution](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm), or [manual deployment](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-manually), see [Deploy Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac#deploy-defender-for-endpoint-on-macos).

Important

This article contains information about third-party tools. This is provided to help complete integration scenarios, however, Microsoft does not provide troubleshooting support for third-party tools.  
Contact the third-party vendor for support.

## Prerequisites

Before you begin the Jamf Pro deployment, make sure you meet the following requirements:

- Review the [Defender for Endpoint on macOS prerequisites](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites), including licensing, supported macOS versions, system extensions and permissions, and network connectivity.
- Verify that your organization has a Jamf Pro subscription.
- Verify that your Jamf Pro account can manage computer groups, configuration profiles, policies, packages, scripts, and enrollment.
- Sign in to your organization's Jamf Pro instance.

## Deploy Defender for Endpoint using Jamf Pro

Complete the deployment articles in this order:

1. [Set up device groups for Defender for Endpoint in Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-device-groups).
2. [Deploy and configure Defender for Endpoint on macOS with Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies).
3. [Enroll macOS devices in Jamf Pro for Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-enroll-devices).

Warning

Repackaging the Defender for Endpoint installation package is not a supported scenario. Doing so can negatively impact the integrity of the product and lead to adverse results, including but not limited to triggering tampering alerts and updates failing to apply.
