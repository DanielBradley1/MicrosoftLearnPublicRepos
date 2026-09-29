<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/fasttrack/cross-tenant-migration -->
<!-- Sitemap-Last-Modified: 2026-05-04 -->

# Cross-Tenant Migration

## Access FastTrack Portal

To explore the FastTrack Migration Learning Center and review the migration prerequisites, please sign in using this link: [https://aka.ms/FastTrack-Migration](https://aka.ms/FastTrack-Migration)

Important

Some Migration Learning Center links require authentication. If you are redirected to a registration page, sign in and then open the link again.

Cross-tenant migration is the process of migrating workloads from one Microsoft 365 tenancy to another. This process can involve the migration of one or many workloads \(including Exchange Online, SharePoint, and OneDrive\).

Cross-tenant migrations are normally part of customers considering Mergers, Acquisition, and Divestitures \(MAD\). Beginning in late 2024, FastTrack offers a preview for cross-tenant migration services to customers migrating Exchange Online, SharePoint, and OneDrive.

Note

This service is done on an invitation-only basis and requires a minimum licensing purchase of 150 licenses. A Cross-Tenant User Data Migration SKU is required in order to qualify for the FastTrack cross-tenant migration service.

Note

The following products and features aren't supported for this service: Microsoft Teams, Microsoft 365 Groups, Microsoft Planner, Skype, Microsoft Stream, Microsoft Flow, Power Apps, device management, and client configuration.

## Considerations

- We require appropriate access and permissions to your source environments and Microsoft 365 tenant to provide data migration services.
- Our data migration services aren't designed or intended for data subject to special legal or regulatory requirements.

Note

US Government and Education \(EDU\) customers aren't currently supported.

- We can't guarantee the speed of mail or file migrations.
- Unforeseen issues \(like unreadable or corrupt items in the source environment\) might prevent our ability to migrate some of your data items.
- External factors beyond our control can result in changes to, delays in, or suspension of our data migration services.

### Migration service availability

**For Commercial customers:** We provide data migration services 24 hours a day, seven \(7\) days a week \(24x7\) \(English only\).

## Migration to Exchange Online

When you choose to use FastTrack to migrate your email from source tenant to target tenant, we provide migration guidance and data migration services. We provide guidance to help you plan your migration, configure your source and target tenant relationship, and use our data migration services to migrate your mailboxes. You create and schedule your migration events. We launch migration events in accordance with your schedule, monitor their progress, and provide status reports. When your migration events are complete, you can expect mail from appropriately scheduled and eligible source mailboxes of your source tenant to have been moved to your target tenant.

Note

The FastTrack cross-tenant migration service is designed exclusively for data migration. It does not include architecture planning, solution design, or post-migration orchestration activities, which fall outside of the scope of FastTrack. For tasks like orchestration, identity management, and post-migration processes, FastTrack recommends FastTrack-partner engagement.

### Considerations

- Before migration, you must complete FastTrack core onboarding for Exchange Online.

  - If you performed onboarding yourself, you must pass the required checks and prerequisites Refer to [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/office-365#exchange-online) for details.

- FastTrack migrates only to active Office 365 mailboxes.
- Distribution lists \(*MailEnabledGroup* objects\) and external contacts \(*MailEnabledContact* objects\) that exist in your source tenant aren't a part of mailbox data migration. You must pre-create them in the target tenant before the migration.

### Migration details

The following table presents **Exchange Online** tenant-to-tenant migration details:

| **What migrates** | **What doesn't migrate** |
| --- | --- |
| - Emails.<br>- Exchange Online server-side mailbox rules.<br>- Exchange Online server-side stored contacts.<br>- Delegate permissions \(if both migrated\).<br>- Calendar.<br>- Tasks.<br>- Archived mailbox migrated with the user's mailbox.<br>- Recoverable items.<br>- Conference rooms and Equipment mailboxes.<br>- Microsoft rights-managed emails.<br>- Microsoft encrypted emails. | - Public folders.<br>- Any email that exceeds the message size limit.<br>- Journaling archive or any non-Microsoft archive solution.<br>- Corrupted items.<br>- Client-side mailbox rules.<br>- Teams messages.<br>- Mailboxes with any kind of hold applied.<br>- Mailboxes with more than 12 auxiliary archives<br>- Outlook profiles.<br>- Microsoft Entra ID permissions.<br>- Send-as emails.<br>- Send-on-behalf emails.<br>- Auto-mapping profiles used for full-access permissions. |

The migration results might be unreadable depending on the source encryption. We recommend the encryption be removed before migration to ensure data is readable in the target. For more information, see [Mergers and Spinoffs](https://go.microsoft.com/fwlink/?linkid=2291703).

### FastTrack responsibilities for Exchange Online migrations

Our FastTrack Specialists perform standard activities during the migration project. Refer to the data migration responsibilities information in [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/office-365#exchange-online) for details.

Our FastTrack Specialists also perform the following activities specific to Exchange Online migrations:

- Provide guidance to help you enable SMTP mail routing coexistence between your source and target tenant if applicable.

### Your responsibilities

You perform standard activities during the migration project. Refer to the data migration responsibilities information in [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/office-365#exchange-online) for details.

You also perform the following activities, specific to Exchange Online migrations:

- Complete FastTrack core onboarding for Exchange Online. If you performed onboarding yourself, you must pass the required checks and prerequisites. Refer to [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/office-365#exchange-online) for details.
- Install the appropriate level of client software as per Office 365 guidelines.
- Migrate client-side data if desired. This data includes, but isn't limited to, local address books, data in local Outlook Data Files \(PSTs\), Outlook rules, and local Outlook settings.
- Assist your end-users with remediation of client-side migration issues.

## Migration to SharePoint and OneDrive

When you choose to use FastTrack to migrate SharePoint and OneDrive sites from tenant-to-tenant, we provide migration guidance and data migration services. We provide guidance to help you plan your migration, configure your source and target tenant relationship, and use our data migration services to migrate your data. We launch migration events in accordance with your schedule, monitor their progress, and provide status reports. When your migration events are complete, you can expect files from your source tenant to have been moved to your target tenant.

### Considerations

- All migrations are subject to SharePoint quotas. Refer to [SharePoint limits](https://go.microsoft.com/fwlink/?LinkId=698855) for details.
- We recommend that you limit the overall amount of migrated data to 75 percent \(%\) of the overall SharePoint storage quota to which you're entitled \(including the extra storage you might have purchased separately\).
- FastTrack migrates only to active OneDrive sites.

### Migration details

The following table presents **SharePoint** tenant-to-tenant migration details.

| **What migrates** | **What doesn't migrate** |
| --- | --- |
| - Microsoft 365 group-connected sites, including those sites associated with Microsoft Teams.<br>- Modern sites without a Microsoft 365 group association.<br>- Classic SharePoint sites.<br>- Communication sites.<br>- Documents.<br>- File and folder structure.<br>- User-level file and folder permissions.<br>- Group-level file and folder permissions.<br>- Sharing links.<br>- Ownership history and previous versions.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by. | - SharePoint sites with over five \(5\) TB of content or one \(1\) million items in total.<br>- Inaccessible or corrupted documents.<br>- Path limits exceeding 400 characters.<br>- SharePoint workflows.<br>- Apps.<br>- Power Apps and automation tasks. |

The following table presents **OneDrive** tenant-to-tenant migration details:

| **What migrates** | **What doesn't migrate** |
| --- | --- |
| - Documents.<br>- File and folder structure.<br>- User-level file and folder permissions.<br>- Group-level file and folder permissions.<br>- Sharing links.<br>- Ownership history and previous versions.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by. | - Inaccessible or corrupted documents.<br>- OneDrive accounts on legal hold.<br>- OneDrive accounts with over 5 TB of content or one \(1\) million items in total.<br>- Path limits exceeding 400 characters. |

### FastTrack responsibilities for SharePoint tenant-to-tenant migrations

Our FastTrack Specialists perform standard activities during the migration project. Refer to the data migration responsibilities information in [SharePoint and OneDrive](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/office-365#sharepoint-and-onedrive) for details.

### Your responsibilities

You perform standard activities during the migration project. Refer to the data migration responsibilities information in [SharePoint and OneDrive](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/office-365#sharepoint-and-onedrive) for details.

Other activities include:

#### For SharePoint tenant-to-tenant migrations

- [Pre-create users, groups, and Microsoft 365 groups on the target tenant](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-tenant-sharepoint-migration-step4).
- [Pre-create Microsoft 365 groups connect to SharePoint sites](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-tenant-sharepoint-migration-step4#pre-create-microsoft-365-groups-connect-to-sharepoint-sites).
- [Step 5: Identity mapping \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-tenant-sharepoint-migration-step5#create-the-identity-mapping-file).

#### For OneDrive tenant-to-tenant migrations

- [Pre-create users, groups, and Microsoft 365 groups on the target tenant](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-tenant-sharepoint-migration-step4#identify-users-and-groups-to-be-migrated).
- [Create the identity mapping file](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-tenant-onedrive-migration-step5#create-the-identity-mapping-file).
