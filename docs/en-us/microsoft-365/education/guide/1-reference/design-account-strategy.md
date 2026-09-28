<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-account-strategy -->
<!-- Sitemap-Last-Modified: 2026-02-11 -->

# Design an account strategy

Large academic institutions need to consider how accounts for students, educators, and others are created. This section describes how to approach the creation of accounts in a large EDU that spans multiple Microsoft Entra tenants.

## Cloud-only accounts

We recommend using cloud-only identities when possible. Cloud-only identities are represented by user account objects that are created and maintained in Microsoft Entra ID. With cloud-only identities, all your users, groups, and contacts are stored in the Microsoft Entra tenant.

Cloud-only identities are best for organizations that don't use Active Directory Domain Services \(AD DS\) to manage local identities or have other on-premises identities. Its greatest benefit is its simplicity since there are no extra directory tools or servers required.

Creating cloud-only accounts is recommended for educational organizations that:

- have already integrated their SaaS applications with Microsoft Entra ID.
- don't rely on on-premises AD DS for managing identities.
- would like to use [School Data Sync \(SDS\)](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/school-data-sync) to create new cloud-only identities based on their online student information systems \(SIS\).

## Hybrid accounts

Hybrid identities are represented by user objects that are created in an on-premises AD DS, then synchronized to a Microsoft Entra tenant. These accounts create a common user identity for authentication and authorization. Hybrid accounts are commonly used when users require access to a mixture of on-premises and cloud applications.

Hybrid identities are best for organizations using AD DS. Their greatest benefit is that it enables users to use the same credentials when accessing on-premises or cloud-based resources.

Creating and maintaining hybrid accounts is more complex than managing cloud-only accounts and is only recommended for educational organizations that:

- need access to on-premises and cloud-based resources.
- create and manage user accounts using AD DS or another identity provider.

## How to enroll

In most countries/regions, there are no administrative actions your institution needs to take to enroll users. You can communicate the availability of Office 365 A1, or Office 365 A1 Plus, to your students, faculty and staff by using content from the [Office 365 Campus Marketing toolkit](https://www.microsoft.com/education/products/office-students-marketing-resources/default.aspx?ms.officeurl=getoffice365resources). The toolkit contains templated emails, posters, web banners and more to help you increase awareness among students, faculty, and staff. Contact your Microsoft representative with specific questions about the steps your school should take.

## Creating Microsoft 365 A1 accounts

There are multiple ways of creating Office 365 accounts for users. How you create the accounts depends on your current state.

![Picture 1.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-account-strategy-1.png)

### When Office 365 accounts already exist

If your school has an existing Office 365 environment in which students, faculty, or staff already have a work or school account, Microsoft will automatically activate and assign Office 365 EDU A1 licenses to existing accounts. After activation, the users will automatically be notified of the additional services available, including the ability to download Office 365 ProPlus if applicable. If the user already has an Office 365 A1 Plus account or any other Office 365 ProPlus license assigned through your school, they are redirected to sign in with their existing credentials and receive a notification that includes an Install now prompt.

### When users have on-premises accounts

Synchronization for hybrid accounts is a two-step process involving two components: Microsoft Entra Connect and School Data Sync.

[Microsoft Entra Connect](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/whatis-azure-ad-connect) is the Microsoft tool used to synchronize on-premises Active Directory users, groups, and other objects to Microsoft Entra ID. It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Microsoft Entra ID. Microsoft Entra Connect also provides the ability to filter which accounts are synchronized and whether to authenticate users using [password hash synchronization \(PHS\)](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/whatis-phs), [pass-through authentication \(PTA\)](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-pta), or using [federation](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-fed-whatis).

Note

We recommend Microsoft Entra Connect with PHS for authentication because it's the simplest way for hybrid accounts to authenticate with Microsoft Entra ID. You only have to manage one server, and get seamless single sign-on and cloud multifactor authentication. Some premium features of Microsoft Entra ID, like [Identity Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection) and [Microsoft Entra Domain Services](https://learn.microsoft.com/en-us/azure/active-directory-domain-services/tutorial-create-instance), require password hash synchronization, no matter which authentication method you choose. ​

Microsoft Entra Connect has two installation types for installation: Express and Custom. Express is the most common and was designed to provide a configuration that works for most customer scenarios. Express installation assumes you have a single forest with fewer than 100,000 objects in your on-premises Active Directory. PHS is automatically enabled with this option.

If you have more than 100,000 objects or multiple forests, use a Custom installation of Microsoft Entra Connect. Also use a Custom installation if you plan to use federation or PTA for user authentication.

For more information, see [Select which installation type to use for Microsoft Entra Connect](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-install-select-installation).

[School Data Sync](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/school-data-sync) \(SDS\) is a free service in Microsoft 365 Education that reads the data from a school’s Student Information System \(SIS\). It creates

- Teams for Education. SDS enables automatic Class Team creation based on SDS-created O365 Groups and Rostering.
- OneNote Class Notebooks. SDS enables automated OneNote Class Notebook provisioning within Teams for Education. When enabled, each Class Notebook has sections created and permissions set based on SDS class rostering data imported during sync.
- Exchange Online and SharePoint. SDS creates Office 365 Groups for online messaging, file sharing, and collaboration.
- Intune for Education. SDS creates schools-based Security Groups for granular device policy, and can also provide automated bulk licensing of Intune for Education for all students and teachers synced.
- SaaS apps. SDS integrates with numerous apps within the Microsoft Store and enables Rostering and single sign-on \(SSO\) app integration.

SDS is often deployed alongside on-premises Active Directory and Microsoft Entra Connect. ​You can use Microsoft Entra Connect to create users and groups from on-premises, then use SDS to sync additional student and teacher attributes from SIS to the account objects created by Microsoft Entra Connect.

Microsoft Entra Connect and SDS will never conflict, as SDS won't sync or overwrite any attribute managed by Microsoft Entra Connect. You can also create use SDS. Instead of using Microsoft Entra Connect, you can use SDS to sync and create users directly from your SIS.

For more information, see [Sync your SIS using School Data Sync \(SDS\)](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/school-data-sync).

**Syncing accounts from on-premises AD to Microsoft Entra tenants**

![Azure Ad Connect and SDS.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-account-strategy-2.png)

**Syncing accounts to Azure tenants with SDS and SIS**

![SDS and SIS sync.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-account-strategy-3.png)

### Create new accounts in bulk

In hybrid environments with existing on-premises Active Directory, use a [PowerShell script and CSV file](https://social.technet.microsoft.com/wiki/contents/articles/24541.powershell-bulk-create-ad-users-from-csv-file.aspx) to create users in bulk. Once created, admins can synchronize the accounts to Microsoft Entra ID using Microsoft Entra Connect.

In cloud-only environments, export or create [CSV files for School Data Sync](https://learn.microsoft.com/en-us/schooldatasync/school-data-sync-format-csv-files-for-sds) from your SIS data, set up a synchronization profile, and [upload the CSVs into SDS](https://learn.microsoft.com/en-us/schooldatasync/how-to-deploy-school-data-sync-by-using-csv-files) to create new cloud-only Microsoft Entra accounts in bulk.

## Challenges and limitations

While large EDUs benefit from a region-based multitenant architecture, it can present some challenges for users you should be aware of, including:

- Each tenant must have its own namespace. For example, region1.fineartsschool.edu.

  - Users need to be aware of their regional suffix, for example, @ region1.fineartsschool.edu.

- Users won't be able to collaborate across tenants using SharePoint, OneDrive, and Microsoft Teams unless enabled and configured by an administrator.
- Multitenant MFA

  - Users must register for MFA in each tenant.
  - Device state controls \(for example, compliant\) can’t be applied cross tenants.

## Licensing

Licenses should only be assigned to users when they're required to access a service like Exchange Online or SharePoint that require a license.

[Group-based licensing](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)​ is recommended for large EDU organizations that have:

- Paid or trial subscription for Microsoft Entra ID P1 and higher
- Paid or trial edition of Office 365 Enterprise E3, Office 365 A3, Office 365 GCC G3, Office 365 E3 for GCCH, or Office 365 E3 for DOD.

Licenses are assigned to all members of a group and when new members are added to the group, they'll also be assigned the appropriate licenses. ​

If you don't own one of the required licenses for group-based licensing, you can use PowerShell to assign licenses as described in [Assign Microsoft 365 licenses to user accounts with PowerShell](https://learn.microsoft.com/en-us/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell).

Another option is to use the Microsoft 365 [admin center](https://admin.microsoft.com/) to manually assign licenses to users. Manual assignment isn't recommended for large organizations.

## Next steps

- [Design identity governance](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-identity-governance)
