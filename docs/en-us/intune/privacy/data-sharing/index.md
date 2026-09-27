<!-- Source: https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# Data security and sharing in Intune

## Data security

Microsoft Intune is a key component of the Microsoft Enterprise Mobility and Security Suite cloud service offering. To support the [data governance strategy](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx), all Microsoft cloud services are developed with [Microsoft Privacy](https://www.microsoft.com/en-us/trustcenter/privacy) and [Microsoft Security](https://www.microsoft.com/en-us/trustcenter/security/) methodologies.

Microsoft Intune follows the same technical and organizational measures that the Microsoft Azure service teams take for securing against data breach processes.

For more information, see the [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp).

### Data breach reporting

When a Customer-Reportable Security Incident \(CRSI\) is identified, customers are notified. This process includes working with the Microsoft 365 team to communicate breach notification for any Microsoft 365 customers using Intune.

## Data sharing

When tenant admins turn on certain functionality \(like the Apple Device Enrollment Program\), Microsoft Intune obtains admin consent for sharing data with the appropriate third parties. In such cases, Intune may share personal data with:

- Third parties acting as Microsoft's agents.
- Third parties not acting as Microsoft's agents, but only when tenant admins explicitly grant Intune permission to do so.

All third parties acting as Microsoft agents are included in the [Online Services Subcontractor list](https://aka.ms/Online_Serv_Subcontractor_List).

Sharing data with such entities is done to aid customer and technical support, service maintenance, and other operations.

A tenant's contract with the third party governs the Intune personal data held in the third party's service. It also grants Intune the permission to transmit data to the third party service.

For information about data shared with certain third parties, see the following articles:

- [Data Intune sends to Apple](https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-intune-to-apple)
- [Data Intune sends to Google](https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-intune-to-google)
- [Data Apple sends to Intune](https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-apple-to-intune)
- [Data Google sends to Intune](https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-google-to-intune)
- [Data Jamf Pro sends to Intune](https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-jamf-to-intune)

### Microsoft Configuration Manager data sharing

Microsoft Intune doesn't share any data with Configuration Manager. Configuration Manager is an on-premise product deployed, managed, and operated directly by the customer. The diagnostics and usage data that is collected by Configuration Manager are only to improve the installation experience, quality, and security of future releases.

To learn more, see [Diagnostics and usage data for Configuration Manager](https://learn.microsoft.com/en-us/configmgr/core/plan-design/diagnostics/diagnostics-and-usage-data).

## Next steps

Find out how to [view and correct](https://learn.microsoft.com/en-us/intune/privacy/personal-data/data-visibility) personal data in Intune.
