<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-m365-web-apps?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Data Residency for Office for the web

## Overview

Service documentation: [Office for the web](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-online-service-description/office-online-service-description)

Capability summary: Office for the web \(formerly Office Web Apps\) opens Word, Excel, and PowerPoint documents in your web browser. Office for the web makes it easier to work and share Office files from anywhere with an internet connection, from almost any device. Microsoft 365 customers with Word, Excel, or PowerPoint can view, create, and edit files on the go.

## Data Residency commitments available

### Advanced Data Residency add-on

Required Conditions:

1. [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) has a sign-up country/region included in a [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions).
2. *Tenant* has a valid [*Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) subscription for all users in the *Tenant*.
3. The Office for the web subscription [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) is provisioned in a *Local Region Geography*.

**Commitment:**

Refer to the [ADR data commitments page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide#office-for-the-web) for the specific customer [*Data at Rest*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) commitment for Office for the web.

### Migration

The cache for documents isn't migrated to the new [*Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions), and will be reestablished as users work on documents.

### How can I determine customer data location?

Microsoft is updating the Microsoft 365 admin center to display the actual data location. After the update, Global Tenant Admins will be able to view the location of in-scope data for their *Tenant* by going to **Admin** > **Settings** > **Org settings** > **Organization profile** > **Data location**. Until then, Global Tenant Admins should use the Exchange Online or SharePoint location information to determine where this service stores in-scope data.
