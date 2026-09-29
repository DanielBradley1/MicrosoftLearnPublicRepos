<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-device-groups -->
<!-- Sitemap-Last-Modified: 2026-09-19 -->

# Set up device groups for Microsoft Defender for Endpoint in Jamf Pro

Use static or smart computer groups in Jamf Pro to target Microsoft Defender for Endpoint configuration profiles and deployment policies to specific macOS devices.

Jamf Pro is a separate product that isn't part of Defender for Endpoint and isn't included with Defender for Endpoint subscriptions. To use these procedures, your organization needs a separate Jamf Pro subscription. For product and subscription information, see [Jamf Pro](https://www.jamf.com/products/jamf-pro/). If your organization doesn't use Jamf Pro, you can [deploy Defender for Endpoint with Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune) or [use another MDM solution](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm).

Important

Microsoft provides information about Jamf Pro to support integration scenarios but doesn't provide troubleshooting support for this third-party product. For issues specific to Jamf Pro, contact Jamf support.

Note

These deployment instructions apply to Defender for Endpoint Plan 1 and Plan 2.

## Prerequisites

Before you create computer groups, make sure you meet the following requirements:

- You can sign in to your organization's Jamf Pro instance.
- Your Jamf Pro account has permission to create and manage computer groups.
- You identified the macOS devices that should receive the Defender for Endpoint configuration profiles and deployment policies.

## Create computer groups in Jamf Pro

Create one or more computer groups for the macOS devices where you plan to deploy Defender for Endpoint. Choose the group type that fits how you manage membership:

- **Static computer group**: Manually assign a fixed set of computers. For current Jamf Pro instructions, see [Creating a Static Group](https://learn.jamf.com/r/jamf-pro-documentation-current/Creating_a_Static_Group).
- **Smart computer group**: Define criteria that Jamf Pro uses to determine membership. For current Jamf Pro instructions, see [Creating a Smart Group](https://learn.jamf.com/r/jamf-pro-documentation-current/Creating_a_Smart_Group).

Use the computer groups as the scope when you [deploy and configure Defender for Endpoint on macOS with Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies).

For the initial deployment, don't base smart group membership on whether Defender for Endpoint is installed. The required configuration profiles must be delivered before the Defender for Endpoint package is installed.

## Next step

After you set up computer groups, [deploy and configure Microsoft Defender for Endpoint on macOS with Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies).
