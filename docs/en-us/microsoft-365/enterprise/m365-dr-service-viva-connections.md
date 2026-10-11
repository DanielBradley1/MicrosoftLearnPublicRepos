<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-viva-connections?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Data Residency for Viva Connections

## Overview

Service documentation: [Overview: Viva Connections](https://learn.microsoft.com/en-us/viva/connections/viva-connections-overview)

Capability Summary: Microsoft Viva Connections is your gateway to a modern employee experience designed to keep everyone engaged and informed. Viva Connections is a customizable app in Microsoft Teams that gives everyone a personalized destination to discover relevant news, conversations, and the tools they need to succeed. Data storage is related to the following Viva Connections Components: Dashboard and feed.

## Data Residency Commitments Available

### Advanced Data Residency add-on

Required Conditions:

1. [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) has a sign-up country/region included in [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) or *Expanded Local Region Geography*.
2. *Tenant* has a valid Advanced Data Residency subscription for all users in the *Tenant*.
3. The Viva Connections subscription [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) is provisioned in *Local Region Geography* or *Expanded Local Region Geography*.

**Commitment:**

Refer to the [ADR data commitments page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide#viva-connections) for the specific customer [*Data at Rest*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) commitment for Viva Connections.

### Migration

Data is stored within Exchange Online, SharePoint and Microsoft Teams. Migration processes are handled by the applicable/relevant workloads.

### How can I determine customer data location?

You can find the actual data location in Tenant Admin Center. As a tenant administrator you can find the actual data location, for committed data, by navigating to **Admin -> Settings -> Org Settings -> Organization Profile -> Data Location**.
