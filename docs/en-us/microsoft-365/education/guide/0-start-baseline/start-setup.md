<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-baseline/start-setup -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Tenant setup and deployment guide for Microsoft 365 for education baseline configurations

![Image showing symbol for baseline configuration.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

This article provides a checklist for the steps to configure your baseline Microsoft 365 education tenant and set up a solid foundation for your organization's productivity and collaboration. By following this guide, you're able to establish a baseline setup that includes essential services like OneDrive, SharePoint, Exchange Online, and Microsoft Teams.

This tenant setup configures the base tenant, including sign-up, tenant creation, network, security, global administrators, and services.

## Required Microsoft products

- Microsoft 365 A1
- Microsoft Entra ID Free

## Deployment guide steps

### Create your Office 365 accounts

Verification that you're an education organization.

|  | Step |
| --- | --- |
| ☐ | [Verify that you're eligible for and Education Organization tenant licenses.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-domains#create-your-tenant) |
| ☐ | [Verify domain to use. A domain can't be used across more than one tenant.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-domains#create-your-tenant) |
| ☐ | [Configure your tenant via the Admin Center.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-admin-settings#step-2-configure-tenant-security-center-admin-settings) |
| ☐ | [Additional admin center configurations for applications and services.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-admin-settings#other-admin-centers) |

### Secure and configure your network

In order to complete this step, you need to plan for the following configurations:

|  | Step |
| --- | --- |
| ☐ | [Internet connection](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-network#internet-connection) |
| ☐ | [Network design](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-network#network-design) |
| ☐ | [Bandwidth planning](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-network#network-planning-and-assessment) |
| ☐ | [Endpoint and IP ranges](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-network#endpoints-and-ip-ranges) |
| ☐ | [Performance tuning](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-network#performance-tuning) |

### Sync your Active Directory \(Hybrid\)

There are two ways to move your identities to Microsoft 365.

|  | Step |
| --- | --- |
| ☐ | [Sync on-premises Active Directory](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad#step-4-sync-your-on-premises-active-directory) |
| ☐ | [Install Microsoft Entra Connect Sync](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad#install-microsoft-entra-connect-sync) |
| ☐ | [Configure Active Directory Federated Services \(AD FS\)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad#configure-active-directory-federated-services-ad-fs) |

### Sync your Student Information System \(SIS\) using School Data Sync \(SDS\)

Using School Data Sync \(SDS\) to sync data from Student Information Systems \(SIS\) to tenant.

|  | Step |
| --- | --- |
| ☐ | [Types of users](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-user-provisioning#step-5-provision-users) |
| ☐ | [User provisioning](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-user-provisioning#user-provisioning) |
|  | ╶ Manual input via Management Console with Microsoft 365 or Microsoft Entra |
|  | ╶ School Data Sync \(SDS\) |
|  | ╶ Deploying SDS |
|  | ╶ SDS requirements |
|  | ╶ Via Graph API or PowerShell |

### License users

Add the required licenses to your user in your tenant.

|  | Step |
| --- | --- |
| ☐ | [Assign licenses](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-license#step-7---license-users) |
| ☐ | [Microsoft 365 Management Console](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-license#assign-a-license-to-groups-in-microsoft-entra-admin-center) |
| ☐ | [Azure Management Portal](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-license) |
| ☐ | [Assign to users](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-license#assign-licenses-to-individual-users-in-microsoft-entra-admin-center) |
| ☐ | [Assign to groups](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-license#assign-a-license-to-groups-in-microsoft-entra-admin-center) |
| ☐ | [Office 365 PowerShell](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-license) |

### Set Tenant Identifier

Microsoft Education tenants should be classified as either K12 or Higher Education using the new Microsoft Education Tenant Identifier.

|  | Step |
| --- | --- |
| ☐ | [Tenant identifier settings](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-identifier#tenant-identifier-settings) |
| ☐ | [How to set the education tenant identifier](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-identifier#how-to-set-the-education-tenant-identifier) |

### Set Student Age Groups

Add student age groups to your users in a tenant.

|  | Step |
| --- | --- |
| ☐ | [Overview](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-set-student-age-group#overview) |
| ☐ | [Setting age group in bulk](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-set-student-age-group#set-age-group-in-bulk) |
| ☐ | [Setting age group for individual users](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-set-student-age-group#set-age-group-for-individual-users) |
| ☐ | [Setting age group in School Data Sync](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-set-student-age-group#set-age-group-in-school-data-sync) |
| ☐ | [Values for the age group attribute](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-set-student-age-group#values-for-the-age-group-attribute) |

## Next steps

Next, you're ready to set up your tenant.

[Next: Create your Office 365 accounts>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-domains)
