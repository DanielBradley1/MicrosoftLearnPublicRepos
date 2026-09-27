<!-- Source: https://learn.microsoft.com/en-us/intune/privacy/personal-data/data-visibility -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# View and correct personal data

Based on their access permissions, Intune admins can view some personal data that's been collected by Intune but can't change that data. Only end users can change their device's personal data that has been collected by Intune.

Note

If you're interested in viewing or deleting personal data, see the [Azure Data Subject Requests for the GDPR](https://learn.microsoft.com/en-us/microsoft-365/compliance/gdpr-dsr-azure) article. If you're looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## View personal data

Admins can see end user personal information in various Nodes of the Intune UI in the Microsoft Intune admin center. The following articles explain what information admins do and don't have access to:

- [See device details](https://learn.microsoft.com/en-us/intune/device-management/inventory-and-status/device-details) in Intune explains how you can review details about an end user's device.
- [Monitor app information and assignments](https://learn.microsoft.com/en-us/intune/app-management/monitor-assignments) explains how to see details about apps installed on an end user's device.
- The [What information can my company see when I enroll my device? article](https://learn.microsoft.com/en-us/intune/user-help/enrollment/data-visibility) gives end users a list of data that their company can and can't see. It's best to clearly tell your users what kind of data you're collecting and why you're collecting it. This article can be the first step in that transparency.

### Who can view the data?

Microsoft uses strict controls to govern access to customer data, granting the lowest level of access required to complete key tasks and revoking access when it's no longer needed.

You can secure and control access to end user personal data by using role-based administration control \(RBAC\). For more information, see [RBAC with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

You can learn more about Microsoft data practices by reading the Online Services Terms and [Microsoft Online Services Privacy Statement](https://go.microsoft.com/fwlink/p/?linkid=131004&clcid=0x409).

## Correct end user personal data

Admins can't update device or app specific information. If an end user wants to correct any personal data \(like the device name\), they must do so directly on their device. Such changes are synchronized the next time they connect to Intune.

## Next steps

Find out how to [audit, export, or delete](https://learn.microsoft.com/en-us/intune/privacy/personal-data/manage-data-requests) personal data in Intune.
