<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-odsp-planning -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 1: Plan for your OneDrive and SharePoint deployment in education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Microsoft OneDrive and SharePoint \(ODSP\) are key components of the education offering for the Microsoft ecosystem. This article describes requirements and best practices to consider when planning for OneDrive and Sharepoint in educational environments.

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Network utilization

Various factors can affect the amount of network bandwidth used by SharePoint and OneDrive. For the best experience, we recommend that you assess this impact before you start your rollout. The article [Network utilization planning for the OneDrive sync app](https://learn.microsoft.com/en-us/onedrive/network-utilization-planning) includes the recommended process for determining your network bandwidth needs for OneDrive. Be sure to include this assessment as part of your deployment plan.

These references can also help with planning your rollout:

- [Networking roadmap for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/networking-roadmap-microsoft-365)
- [Office 365 URLs and IP address ranges](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges)
- [Use the Office 365 Content Delivery Network \(CDN\) with SharePoint Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/use-microsoft-365-cdn-with-spo)

## SharePoint admin role

Users assigned to this role have access to the Sharepoint admin center and can create and manage sites, designate site admins, manage sharing settings, and manage Microsoft 365 groups, including creating, deleting, and restoring groups, and changing group owners. [Learn more about the SharePoint admin role.](https://learn.microsoft.com/en-us/sharepoint/sharepoint-admin-role)

Key tasks of SharePoint admin:

- [Create sites](https://learn.microsoft.com/en-us/sharepoint/create-site-collection)
- [Delete sites](https://learn.microsoft.com/en-us/sharepoint/delete-site-collection)
- [Manage sharing settings at the organization level](https://learn.microsoft.com/en-us/sharepoint/turn-external-sharing-on-or-off)
- [Add and remove site admins](https://learn.microsoft.com/en-us/sharepoint/manage-site-collection-administrators)
- [Manage site storage limits](https://learn.microsoft.com/en-us/sharepoint/manage-site-collection-storage-limits)

## OneDrive users and storage

Consider the following when planning for OneDrive users and storage:

- **[Pre-provision accounts](https://learn.microsoft.com/en-us/sharepoint/pre-provision-accounts)**

  By default, OneDrive is automatically pre-provisioned for new users. In an educational organization, this means that students, faculty, any user in the directory automatically get a OneDrive provisioned before they access OneDrive.
- **[Set default storage space](https://learn.microsoft.com/en-us/sharepoint/set-default-storage-space)**

  Education organizations should follow the guidelines for storage allocations \[More Here\]\(Add Athens link for storage considerations\)
- **[Change user storage](https://learn.microsoft.com/en-us/sharepoint/change-user-storage)**

  You can set OneDrive storage space for a specific user.
- **[Set retention](https://learn.microsoft.com/en-us/sharepoint/set-retention)**

  If a user's Microsoft 365 account is deleted, their OneDrive files are preserved for a period of time. You can set this time period.
- **[Restore deleted OneDrives](https://learn.microsoft.com/en-us/sharepoint/restore-deleted-onedrive)**

  When you delete a user in the Microsoft 365 admin center \(or when a user is removed through Active Directory synchronization\), the user's OneDrive is retained for the number of days you specify in the SharePoint admin center. The default is 30 days. During this time, other users can still access shared content. At the end of the time period, the OneDrive remains in a deleted state for 93 days and can only be restored by a SharePoint Administrator.
- **[Retention and deletion](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion)**

  You can manage a user's OneDrive when you delete the user's Microsoft 365 account for your organization. Some steps happen automatically.
- **[List OneDrive URLs](https://learn.microsoft.com/en-us/sharepoint/list-onedrive-urls)**

  As a SharePoint administrator, you can confirm OneDrive URLs for specific users in your organization.
- **[Effects of username changes](https://learn.microsoft.com/en-us/sharepoint/upn-changes)**

  A User Principal Name \(UPN\) is made up of two parts, the prefix \(user account name\) and the suffix \(DNS domain name\). For example:

  `user1@contoso.com`

  In this case, the prefix is "user1" and the suffix is "contoso.com."

## Next steps

Now that you completed the OneDrive/SharePoint planning section, you're ready for the OneDrive/SharePoint sharing section.

[Next: Sharing >](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-odsp-sharing)
