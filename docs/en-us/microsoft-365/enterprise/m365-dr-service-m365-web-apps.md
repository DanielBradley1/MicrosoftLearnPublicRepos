<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-m365-web-apps?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-02-19 -->

# Data Residency for Microsoft 365 web apps \(formerly known as "Office for the Web"\)

## Overview

Service documentation: [Microsoft 365 web apps Service Description](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-online-service-description/office-online-service-description)

Capability summary: Microsoft 365 web apps \(formerly known as "Office for the Web"\) opens Word, Excel, and PowerPoint documents in your web browser. Microsoft 365 web apps makes it easier to work and share Office files from anywhere with an internet connection, from almost any device. Microsoft 365 customers with Word, Excel, or PowerPoint can view, create, and edit files on the go.

## Data Residency commitments available

### Advanced Data Residency add-on

Required Conditions:

1. *Tenant* has a sign-up country/region included in a *Local Region Geography*.
2. *Tenant* has a valid *Advanced Data Residency* subscription for all users in the *Tenant*.
3. The Microsoft 365 web apps subscription customer data is provisioned in a *Local Region Geography*.

**Commitment:**

Refer to the [ADR Commitment page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-commitments?view=o365-worldwide#microsoft-365-web-apps-formerly-known-as-office-for-the-web) for the specific customer data at rest commitment for Microsoft 365 web apps.

### Migration

The cache for documents isn't migrated to the new *Geography*, and will be reestablished as users work on documents.

### How can I determine customer data location?

We are in the process of updating the actual data location in *Tenant* Admin Center. When this change is complete the tenant will be able to see the actual data location, for in scope data, by navigating to **Admin \| Settings \| Org Settings \| Organization Profile \| Data Location**. Until that change is visible, you can view the Exchange Online data or SharePoint location information in order to understand where the in scope data is stored for this service.
