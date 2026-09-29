<!-- Source: https://learn.microsoft.com/en-us/defender-for-iot/discover-vulnerabilities-overview -->
<!-- Sitemap-Last-Modified: 2024-08-08 -->

# Overview of vulnerability management

With vulnerability management, Microsoft Defender for IoT in the Defender portal provides extended coverage for OT networks, gathers OT device data into one place, and displays the data with the other devices on your network.

The OT security administrator proactively manages network exposure based on the vulnerability details and recommended remediation actions.

Important

This article discusses Microsoft Defender for IoT in the Defender portal \(Preview\).

Some features are not yet available in the Defender portal. If you're interested in these features, or you're an existing customer working on the Azure portal, see the [Defender for IoT on Azure documentation](https://learn.microsoft.com/en-us/azure/defender-for-iot/organizations/overview).

Learn more about the [Defender for IoT management portals](https://learn.microsoft.com/en-us/defender-for-iot/microsoft-defender-iot#what-are-the-different-management-portals-for-microsoft-defender-for-iot).

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Vulnerability management capabilities

The key vulnerability management capabilities are:

| Capability | Description |
| --- | --- |
| Extended vulnerability coverage | Defender for IoT uses detailed OT device firmware information and discovers the device vendor, model, and version to identify known vulnerabilities. |
| [Security recommendations page](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation) | Offers actionable steps to update and mitigate vulnerable products. |
| [Weaknesses page](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-weaknesses) | Includes a detailed list of vulnerabilities like zero-days and known exploits. |
| [Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-weaknesses#view-common-vulnerabilities-and-exposures-cve-entries-in-other-places) | You can manage and control the vulnerabilities globally, per tenant or device group, per device from the device page, or per vulnerable product through the Inventory page. |
| [Exception handling](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation#file-for-exception) | Create exceptions for recommendations that can't be patched. |
| [Customizable Vulnerability Notifications](https://learn.microsoft.com/en-us/defender-endpoint/configure-vulnerability-email-notifications) | Alert key stakeholders with customizable notifications. |
| [Reporting Inaccuracies](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-weaknesses#report-inaccuracy) | Users can report inaccuracies on discovered CVEs or request support for new vulnerabilities. |

## Weaknesses page

The Microsoft Defender portal displays Microsoft Defender for IoT security vulnerabilities in the **Endpoints > Weaknesses** page.

Vulnerabilities are listed based on their publicly registered Common Vulnerability and Exposures\(CVEs\) ID.

The **Weaknesses** page lists the detected security vulnerabilities across all devices, endpoints, applications and other sources on your network. The data can be filtered according to device groups based on the created sites.

The OT security administrator uses the list of detected vulnerabilities in the **Weaknesses** page to send a remediation request for the relevant team to handle.

Learn more about the [Weaknesses page in the Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-weaknesses).

## Next steps

[Prioritize and investigate vulnerabilities](https://learn.microsoft.com/en-us/defender-for-iot/prioritize-vulnerabilities) in Microsoft Defender for IoT.
