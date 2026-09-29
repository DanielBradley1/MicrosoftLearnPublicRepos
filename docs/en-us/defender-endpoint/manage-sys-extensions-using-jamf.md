<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-sys-extensions-using-jamf -->
<!-- Sitemap-Last-Modified: 2026-09-19 -->

# Configure Microsoft Defender for Endpoint system extensions using Jamf Pro

Microsoft Defender for Endpoint on macOS requires configuration profiles for Full Disk Access, system extensions, and the network extension. Use the Microsoft-maintained profiles and current Jamf Pro upload procedure instead of manually recreating the payloads.

Jamf Pro is a separate product that isn't part of Defender for Endpoint and isn't included with Defender for Endpoint subscriptions. To use these procedures, your organization needs a separate Jamf Pro subscription. For product and subscription information, see [Jamf Pro](https://www.jamf.com/products/jamf-pro/). If your organization doesn't use Jamf Pro, you can [deploy Defender for Endpoint with Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune) or [use another mobile device management \(MDM\) solution](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm).

Important

Microsoft provides information about Jamf Pro to support integration scenarios but doesn't provide troubleshooting support for this third-party product. For issues specific to Jamf Pro, contact Jamf support.

## Prerequisites

Before you configure the required profiles, review the [Defender for Endpoint on macOS prerequisites](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites). Verify that your Jamf Pro account can upload and scope computer configuration profiles.

## Configure system extensions in Jamf Pro

The maintained Jamf Pro deployment article contains the current profile downloads, Defender-specific identifiers, and Jamf documentation links.

### Grant Full Disk Access

Follow [Step 6: Grant Full Disk Access to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint). The current profile grants access to all required Defender components, including `com.microsoft.dlp.daemon`.

### Approve system extensions

Follow [Step 7: Approve system extensions for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies#step-7-approve-system-extensions-for-microsoft-defender-for-endpoint). The profile approves the endpoint security and network system extensions using Microsoft Team ID `UBF8T346G9`.

### Configure the network extension

Follow [Step 8: Configure the network extension](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies#step-8-configure-network-extension). Use the current Microsoft-maintained `netfilter.mobileconfig` profile and the current Jamf Pro configuration-profile upload instructions linked from that section.
