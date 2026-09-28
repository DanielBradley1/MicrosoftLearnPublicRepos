<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-school-data-sync -->
<!-- Sitemap-Last-Modified: 2025-10-03 -->

# Step 6: Sync your Student Information System using School Data Sync

School Data Sync \(SDS\) is a free service in Microsoft 365 for Education that reads the school and roster data from a school's Student Information System \(SIS\). SDS creates Microsoft 365 Groups for Exchange Online and SharePoint, class teams for Microsoft Teams, and OneNote Class notebooks. SDS also creates groups for Intune for Education, rostering and SSO integration for many other third-party applications, and more.

Key scenarios that SDS enables:

- **Teams for Education** – SDS enables automatic Class Team creation based the classes and rosters stored in the SIS, enabling the full Teams experience customized for Education.
- **OneNote Class Notebooks** – SDS enables automated OneNote Class Notebook provisioning within Teams for Education. When enabled, each Class Notebook has sections created and permissions set based on SDS class rostering data imported during sync.
- **Exchange Online and SharePoint** – SDS creates Microsoft 365 Groups based on the classes and rosters stored in the SIS, providing online messaging, file sharing, and collaboration within each group.
- **Intune for Education** – SDS creates several types of Security Groups from the SIS data, which helps with building granular and scoped device policy in Intune.
- **Microsoft Entra ID** – SDS can create users, license users, and create a variety of groups that are broadly useful across Microsoft Entra ID for features like group based licensing and Conditional Access policy. SDS also writes specific metadata in the form of extension attributes onto user and group objects which are accessible via MS Graph and PowerShell, which can be useful for both IT administration and app integration scenarios.
- **Purview** – SDS can create school based administrative units which are useful for configuring scoped role-based access control \(RBAC\) role assignments for delegated admins, as well as Purview Data Security and Compliance policy like DLP, Insider Risk Management, and Information Protection/Sensitivity Labels.
- **Microsoft Copilot** – SDS is incredibly useful for organizations using Microsoft Copilot, since all the data synced from SDS is written to Microsoft Entra ID and made available through MS Graph. Enriching the data available through MS Graph expands on the contextual information which can be retrieved in Microsoft Copilot Prompts and Queries. The same value applies to other AI based solutions outside of Copilot.
- **3rd Party Apps** – SDS links SIS data to enable integration through the Education Graph API with numerous apps within the Microsoft Store and enables Rostering and single sign-on \(SSO\) app integration.

If you have a hybrid Microsoft 365 deployment, once you created your tenant and enabled identity integration with on-premises AD, your next step is to enable [SDS](https://learn.microsoft.com/en-us/schooldatasync). For users synced from on premise, SDS will evolve them from basic users in the directory to become students and teachers, with associated grade, school, classes, and other education specific attributes. If you’re deploying Microsoft 365 as a stand-alone or cloud only platform, you can run SDS as soon as you created your tenant to start building out your directory.

[Benefits of using SDS for IT Admins, Teachers, Students, SIS Vendors, App Vendors, and SIs.](https://learn.microsoft.com/en-us/schooldatasync/#sds-customer-and-partner-benefits)

## Methods of integrating with your SIS

SDS offers two methods to connect data for directory sync operations.

- **Connect data using OneRoster API** – Seamless API integration with several SISs through 1EdTech \(formerly IMS Global\) [OneRoster API v1.1 standard](https://learn.microsoft.com/en-us/schooldatasync/oneroster-provider-overview#oneroster-providers-status-and-capabilities).
- **Connect data using CSV Files** – Any SIS that can export data to one of the supported CSV formats can be synced via SDS.

  - [SDS v1 CSV](https://learn.microsoft.com/en-us/schooldatasync/sds-v1-csv-file-format)
  - [SDS v2.1 CSV](https://learn.microsoft.com/en-us/schooldatasync/sds-v2.1-csv-file-format)

## SDS requirements

- A Microsoft 365 Education tenant account

## Deploying SDS

To deploy SDS:

1. Before deploying SDS, review these items:

   - [SDS Planning Checklist](https://learn.microsoft.com/en-us/schooldatasync/planning-checklist)
   - [SDS User Identity Rules](https://learn.microsoft.com/en-us/schooldatasync/identity-matching)

2. Connect your data to SDS:

   - [Connect data with SDS v2.1 CSV](https://learn.microsoft.com/en-us/schooldatasync/connect-data?tabs=sdsv21csv%2Ceditcsv)
   - [Connect data with SDS v1 CSV](https://learn.microsoft.com/en-us/schooldatasync/connect-data?tabs=sdsv1csv%2Ceditcsv)
   - [Connect data with OneRoster API](https://learn.microsoft.com/en-us/schooldatasync/connect-data?tabs=onerosterapi%2Ceditcsv)

3. Manage data with Microsoft 365:

   - [Manage data to improve learning outcomes](https://learn.microsoft.com/en-us/schooldatasync/manage-data-microsoft-365)

Now you're ready to license users.

[Next: License users>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-license)
