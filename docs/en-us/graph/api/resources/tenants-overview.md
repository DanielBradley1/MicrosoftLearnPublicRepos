<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenants-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Overview of tenant management APIs in Microsoft Graph

Tenants are the foundation of your organization's cloud environment, providing the boundaries for collaboration, identity, access, and resource management. Microsoft Graph provides a growing set of APIs to programmatically manage, configure, and govern those tenants at scale - from maintaining consistent settings to establishing cross-tenant governance relationships.

## Available services and APIs

---

![](https://learn.microsoft.com/en-us/graph/images/tenants/backup-icon.svg)

### [Backup and restore](https://learn.microsoft.com/en-us/graph/api/resources/tenants-backup-recovery-overview)

The backup and restore APIs provide a programmatic surface for building business continuity into applications and managed service offerings.

Currently, only the **Microsoft 365 Backup Storage** APIs are generally available. These APIs protect SharePoint sites, OneDrive accounts, and Exchange mailboxes with up to one year of retention and recovery points every ten minutes. Backups use append-only, immutable storage that prevents ransomware and compromised accounts from corrupting historical data. Restores are free, and data never leaves the Microsoft 365 trust boundary.

---

![](https://learn.microsoft.com/en-us/graph/images/tenants/configuration-icon.svg)

### [Configuration management](https://learn.microsoft.com/en-us/graph/api/resources/unified-tenant-configuration-management-api-overview)

Define a baseline of your tenant configuration settings and monitor them over time. Detect and resolve configuration drift across workloads such as Conditional Access policies, security defaults, and identity providers.

---

### [Tenant information](https://learn.microsoft.com/en-us/graph/api/resources/tenantinformation)

![](https://learn.microsoft.com/en-us/graph/images/tenants/tenant-information-icon.svg)

Look up a tenant's publicly shared Microsoft Entra details, such as the display name, default domain name, federation brand name, and tenant ID. Use this resource to find a tenant by domain name or tenant ID for cross-tenant discovery and directory lookup scenarios.

---

![](https://learn.microsoft.com/en-us/graph/images/tenants/cross-tenant-access-icon.svg)

### [Cross-tenant access](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy-overview)

Define and control the external organizations that your users can collaborate with for seamless and secure collaboration. Configure cross-tenant access policies to specify:

- Which organizations and in what Microsoft Azure clouds can your users collaborate with?
- Is the collaboration limited to specific users in the organizations?
- What authentication controls are applied to users from the organizations?

---

![](https://learn.microsoft.com/en-us/graph/images/tenants/multitenant-org-icon.svg)

### [Multitenant organizations](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization-overview)

Define and manage an organization that spans multiple Microsoft Entra tenants. Add or remove member tenants, configure roles, and set up cross-tenant access and synchronization templates so all tenants collaborate as a single entity.

---
