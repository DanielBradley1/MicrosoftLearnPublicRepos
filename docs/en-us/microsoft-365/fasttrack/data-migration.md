<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/fasttrack/data-migration -->
<!-- Sitemap-Last-Modified: 2026-05-04 -->

# Data Migration

## Access FastTrack Portal

To explore FastTrack migrations, advanced migration guides, migration prerequisites, and to perform migration, visit the [Microsoft Admin Center](https://aka.ms/FTMAC) \(*MAC*\) and select the FastTrack migration assistance tab.

Important

Some Migration Learning Center links require authentication. If you are redirected to a registration page, sign in and then open the link again.

FastTrack can help you migrate mail and file data in your source environments to Office 365 \(Exchange Online, SharePoint, and OneDrive\).

For any customers with 150 or more eligible licenses, FastTrack provides guidance and data migration services. This guidance helps you plan your migration, configure your source environments and Microsoft 365 tenant, and use our data migration services to migrate your data. You create and schedule your migration events. FastTrack launches migration events in accordance with your schedule, monitors their progress, and provides status reports.

For more information, see [Eligibility](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/eligibility).

Note

To request guidance from FastTrack specialists with your Microsoft 365 deployment and migration efforts, visit [Raise RFA](https://learn.microsoft.com/en-us/microsoft-365/enterprise/request-fasttrack-assistance-microsoft-365).

GCC environments are currently being supported through the GCC FastTrack instance. GCC customers should visit the [GCC FastTrack portal](https://gcc.fasttrack.microsoft.com/signin).

Note

For education plans, your paid faculty/educator licenses are eligible for data migration services. A1 students are only eligible when migrating with paid faculty/educators and when also migrating from Exchange or Google Workspace. For education plans, your paid faculty/educator licenses are eligible for data migration services for content migrations. This includes data within Box, Dropbox, Google Drive, and file share.

### Considerations

- Your source environments must meet specific expectations in order to migrate data to Office 365. \(*For more information, see* [Source environments](#source-environments)\).
- We require appropriate access and permissions to your source environments and Office 365 tenant to provide data migration services.
- Our data migration services aren't designed or intended for data subject to special legal or regulatory requirements. As we migrate your data, it can be transferred to, stored, and processed anywhere that we maintain facilities \(except as otherwise provided for your FastTrack migration project\).
- We can’t guarantee the speed of mail or file migrations.
- Unforeseen issues \(like unreadable or corrupt items in the source environment\) might prevent our ability to migrate some of your data items.
- External factors beyond our control \(like changes to non-Microsoft application programming interfaces \(APIs\)\) can result in changes to, delays in, or suspension of our data migration services.

### Migration service availability

- **For Commercial customers:** We provide data migration services 24 hours a day, seven \(7\) days a week \(24x7\) \(English only\).
- **GCC Customers:** We provide data migration services 24 hours a day, five \(5\) business days a week \(24x5\).

Note

For GCC customers, Box, Google Drive, Gmail, Exchange, and file share migrations are supported. Dropbox migrations aren't supported.

## Migration to Exchange Online

When you choose to use FastTrack to migrate your email to Exchange Online, we provide migration guidance and data migration services. We provide guidance to help you plan your migration, configure your source environments and Exchange Online, and use our data migration services to migrate your mailboxes. You create and schedule your migration events. We launch migration events in accordance with your schedule, monitor their progress, and provide status reports. When your migration events complete, you can expect mail from appropriately scheduled and eligible source mailboxes of your migrated source environments to Exchange Online.

### Considerations

- Before migration, you must complete the set up and configuration of Exchange Online for your migration, and meet the [FastTrack Exchange migration prerequisites](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/Exchange/getting-started/prerequisites). \(***Important:** FastTrack requires authentication to access the FastTrack Migration Learning Center Migration page. If you land on a registration page after clicking the Learning Center link, come back and click the link again, to access the page after you authenticate.*\)

  - If you performed onboarding yourself, you must pass the required checks and prerequisites. Refer to [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/office-365#exchange-online) for details.

- FastTrack migrates only to active Office 365 mailboxes.
- You must satisfy specific requirements if you intend to migrate from an on-premises Exchange environment. Refer to [Hybrid deployment prerequisites](https://go.microsoft.com/fwlink/?LinkId=787528) for details.
- Each source environment must be on the latest service pack \(SP\) and rollup \(RU\)/cumulative update \(CU\) level for the respective product in the source environment.
- Distribution lists \(*MailEnabledGroup* objects\) and external contacts \(*MailEnabledContact* objects\) that exist in your on-premises Active Directory aren’t a part of mailbox data migration. However, you can synchronize them using Microsoft Entra Connect.

## Source environments

Our data migration service migrates data from these source environments:

- A single or multiple Active Directory forests with single or multiple Exchange organizations \(each source Exchange server must meet the requirements for a [hybrid deployment](https://go.microsoft.com/fwlink/?LinkId=787528)\).
- Google Workspace environment \(Gmail, Contacts, and Calendar only\).

The following table presents migration details specific to each source environment:

| **Source environment** | **Type of migration** | **What migrates** | **What doesn’t migrate** |
| --- | --- | --- | --- |
| **Exchange Server \(on-premises\)**  <br>  <br>**Note:** Your source Exchange server must meet the requirements for a hybrid deployment. For on-premises Exchange dependencies, see [Hybrid deployment prerequisites](https://go.microsoft.com/fwlink/?LinkId=787528). | Migration with hybrid deployment | - Emails.<br>- Server-side mailbox rules.<br>- Delegates.<br>- Mailbox contacts.<br>- Calendar.<br>- Tasks.<br>- Rights-managed emails.<br>- Encrypted emails.<br>- Signatures.<br>- Personal archive migrated with the user's mailbox.<br>- Recoverable items. | - Public folders.<br>- Any email that exceeds the message size limit.<br>- Journaling archive or any non-Microsoft archive solution.<br>- Blocked or inactive users.<br>- Archive data from Personal Storage Table \(PST\) files.<br>- Corrupted items.<br>- Inactive mailboxes.<br>- Client-side mailbox rules. |
| **Google Workspace environment \(Gmail, Contacts, and Calendar only\)**  <br>  <br>**Note:** Your Google Workspace environment must meet the prerequisites described in [Perform a Google Workspace migration](https://learn.microsoft.com/en-us/exchange/mailbox-migration/perform-g-suite-migration). | Cutover or staged | - Emails.<br>- Mailbox contacts \(a maximum of three \(3\) email addresses per contact are migrated\).<br>- Calendar.<br>- Labels.<br>- Rules.<br>- Cloud attachments.<br>- Delegates.<br>- Tasks. | - Signatures.<br>- Any email or attachment that exceeds the message size limit.<br>- Blocked or inactive users.<br>- Archive data from PST files or any non-Microsoft archive solution \(for example, Google Vault\).<br>- Rights managed or encrypted emails.<br>- Corrupted items.<br>- Google Hangouts.\*\*<br>- Google Groups.<br>- Resource mailboxes.<br>- Inactive mailboxes.<br>- Vacation settings and automatic reply settings.<br>- Shared calendars, Google Hangout links, and event colors.<br><br>\*\*Hangout conversations saved with a label are migrated. |

## FastTrack responsibilities for Exchange Online migrations

FastTrack specialists perform standard activities during the migration project. For details about the data migration scope and responsibilities, see the Migration section of the **Exchange migration guide** in the [Microsoft 365 admin center](https://admin.cloud.microsoft/?Q=RecommendationsADGDashboard#/modernonboarding/exchangemigrationguide).

FastTrack Specialists also provide guidance to help you enable Simple Mail Transfer Protocol \(SMTP\) mail routing coexistence between your source environments and Exchange Online, if applicable.

### Your responsibilities

You perform standard activities during the migration project. Refer to the data migration scope and responsibilities information in the [FastTrack Migration Learning Center](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/Exchange/migration/migration-scope-and-responsibility) for details. \(***Important:** FastTrack requires authentication to access the FastTrack Migration Learning Center Migration page. If you land on a registration page after clicking the Learning Center link, come back and click the link again to access the page after you authenticate.*\)

You also perform the following activities, specific to Exchange migrations:

- Complete FastTrack core onboarding for Exchange Online. If you performed onboarding yourself, you must pass the required checks and prerequisites. Before migration, you must complete the set up and configuration of Exchange Online for your migration and meet the [FastTrack Exchange migration](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/Exchange/getting-started/prerequisites) prerequisites. \(***Important:** FastTrack requires authentication to access the FastTrack Migration Learning Center Migration page. If you land on a registration page after clicking the Learning Center link, come back and click the link again, to access the page after you authenticate.*\)
- Install the appropriate level of client software as per Office 365 guidelines.
- Satisfy specific requirements if you intend to migrate from an on-premises Exchange environment. Refer to [Hybrid deployment prerequisites](https://go.microsoft.com/fwlink/?LinkId=787528) for details.
- Ensure each source environment is on the latest service pack \(SP\) and rollup \(RU\)/cumulative update \(CU\) level, if applicable.
- Configure and validate SMTP mail routing coexistence between your source environments and Exchange Online, if applicable.
- Ensure your source mailbox size doesn’t exceed the target mailbox quota. Depending on the source platform, you might need to limit your source data to 85 percent \(%\) of the target mailbox quota.
- Migrate client-side data if desired. This includes, but isn’t limited to, local address books, data in local PST files, Outlook rules, and local Outlook settings.
- Assist your end-users with remediation of client-side migration issues.

## Migration to SharePoint

When you choose to use FastTrack to migrate your files to SharePoint, we provide migration guidance and data migration services. We provide guidance to help you plan your migration, configure your source environments and SharePoint, and use our data migration services to migrate your files. You create and schedule your migration events. We launch migration events in accordance with your schedule, monitor their progress, and provide status reports. When your migration events complete, you can expect files from appropriately scheduled and eligible sources of your migrated source environments to SharePoint.

### Considerations

- All migrations are subject to SharePoint quotas. Refer to [SharePoint limits](https://go.microsoft.com/fwlink/?LinkId=698855) for details.
- We recommend that you limit the overall migration data to 75% of the overall SharePoint storage quota \(including any extra storage you purchased separately\).

### Source environment details

Our data migration services migrate data from these source environments:

- File shares \(Server Message Block \(SMB\) file shares on devices supporting SMB 2.0 onward\).
- A single Google Workspace environment \(Google Drive only\).
- Box \(Starter, Business, Enterprise\).
- Dropbox for Teams \(Standard and Advanced\).

The following table presents migration details specific to each source environment:

| **Source environment** | **Type of migration** | **What migrates** | **What doesn’t migrate** |
| --- | --- | --- | --- |
| **Any file share device supporting SMB 2.0 onward** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level file and folder permissions.\*<br>- Group-level file and folder permissions.\*<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>\*Directory synchronization configuration required. Only NTFS permissions exposed to the Windows File Explorer are migrated. Permissions managed directly on file share devices aren't migrated. If data is stored on an SMB 2.0 device, the NTFS-equivalent permissions exposed by the SMB protocol are migrated. | - Ownership history and previous versions.<br>- Conversion of embedded URLs in content.<br>- Previous versions.<br>- Windows file and folder attributes \(like read-only and hidden\).<br>- Non-Windows New Technology File System \(NTFS\) and NTFS advanced permissions and special settings:<br>- Explicit deny permissions \(removed after migration, content subject to parallel permissions or permissions on parent folder\).<br>- NTFS auditing configuration.<br>- More file metadata provided by File Classification Infrastructure \(FCI\).<br>- Inaccessible or corrupted documents.<br>- Hidden shares.<br>- Sharing \(like permissions granted on the share level\).<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |
| **Single Google Workspace environment \(Google Drive only\)** | Single or multi-pass | - Google Docs, Sheets, and Slides \(files are converted to the equivalent Office format\), including files over 10 MB.<br>- File and folder structure.<br>- User-level folder permissions.<br>- Group-level folder permissions.<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared drives \(folders and files\).<br>- Shared content owned by the Google Drive account being migrated.<br>- Google Sheets are converted to Excel files, but custom scripts, formulas, and macros **aren't** migrated.<br>- Google Forms.<br>- File versions. | - Ownership history and comments.<br>- File and folder descriptions, folder colors.<br>- Advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Blocked or inactive users.<br>- Google Photos, Maps, and other connected apps.<br>- Google Drawings.<br>- Shared content external to your organization.<br>- Content not owned by the Google Drive account being migrated.<br>- Permissions and basic metadata of guests. \(**Note**: Use Google Drive Admin reports to identify content shared with guests. Instruct end users to reshare content with guests after migration.\)<br>- Shared Drive membership permissions. \(**Note**: Use Google Drive Admin reports to identify shared drive memberships. Instruct end users to configure these membership settings on the target before migration.\)<br>- Files marked as restricted or not copyable.<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724).<br>- Google Shortcuts. |
| **Box \(Starter, Business, Enterprise\)** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level folder permissions.<br>- Group-level folder permissions.<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared content owned by the Box account being migrated.<br>- Box Notes \(converted to Word document format\). | - Ownership history, previous versions, and comments.<br>- File and folder descriptions.<br>- Box Tags and advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Blocked or inactive users.<br>- Box Apps, Bookmarks, Favorites, and Workflows.<br>- Content not owned by the migrated Box account.<br>- Permissions and basic metadata of guests. \(**Note**: Use Box reports to identify content shared with guests. Instruct end users to reshare content with guests after migration.\)<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |
| **Dropbox for Teams \(Standard and Advanced\)** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level folder permissions.<br>- Group-level folder permissions.<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared team folders and content.<br>- Shared content owned by the Dropbox accounts being migrated. | - Ownership history, previous versions, and comments.<br>- File and folder descriptions.<br>- Advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Unmounted Dropbox folders.<br>- Deleted or disconnected users.<br>- Dropbox Paper, Showcases, and Spaces.<br>- Dropbox Apps and Favorites \(Pins/Stars\).<br>- Content not owned by the migrated Dropbox account.<br>- Permissions and basic metadata of guests. \(**Note**: Use Dropbox reports to identify content shared with guests. Instruct end users to reshare content with guests after migration\)<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |

## FastTrack responsibilities for SharePoint migrations

Our FastTrack Specialists perform standard activities during the migration project. Before migration, you must complete the set up and configuration of Exchange Online for your migration and meet the [FastTrack SharePoint migration](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/file%20share/getting-started/prerequisites) prerequisites.

Important

FastTrack requires authentication to access the FastTrack SharePoint migration prerequisites page. If you land on a registration page after clicking the migration link, come back and click the link again to access the page after you authenticate.

### Your responsibilities

You perform standard activities during the migration project. Refer to the data migration scope and responsibilities information in the [FastTrack Migration Learning Center](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/Exchange/migration/migration-scope-and-responsibility).

Important

FastTrack requires authentication to access the FastTrack Migration Learning Center Migration page. If you land on a registration page after clicking the Learning Center link, come back and click the link again, to access the page after you authenticate.

You also perform the following activities, specific to SharePoint migrations:

- Provision all SharePoint team sites to be targeted by your migration events.

## Migration to OneDrive

When you choose to use FastTrack to migrate your files to OneDrive, we provide migration guidance and data migration services. We provide guidance to help you plan your migration, configure your source environments and OneDrive, and use our data migration services to migrate your files. You create and schedule your migration events. We launch migration events in accordance with your schedule, monitor their progress, and provide status reports. When your migration events complete, you can expect files from appropriately scheduled and eligible sources of your migrated source environments to OneDrive.

### Considerations

- All migrations are subject to SharePoint quotas. Refer to [SharePoint limits](https://go.microsoft.com/fwlink/?LinkId=698855) for details.
- We recommend that you limit the overall migration amount to 75% of the overall SharePoint storage quota \(including any extra storage you purchased separately\).
- FastTrack migrates only to active OneDrive drives.

### Source environment details

Our data migration services migrate data from these source environments:

- File shares \(SMB file shares on devices supporting SMB 2.0 onward\).
- Single Google Workspace environment \(Google Drive only\).
- Box \(Starter, Business, Enterprise\).
- Dropbox for Teams \(Standard and Advanced\).

The following table presents migration details specific to each source environment:

| **Source environment** | **Type of migration** | **What migrates** | **What doesn't migrate** |
| --- | --- | --- | --- |
| **Any file share device supporting SMB 2.0 onward** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level file and folder permissions.\*<br>- Group-level file and folder permissions.\*<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>  <br>\*Directory synchronization configuration required. Only NTFS permissions exposed to the Windows File Explorer are migrated. Permissions managed directly on file share devices aren't migrated. If data is stored on an SMB 2.0 device, the NTFS-equivalent permissions exposed by the SMB protocol are migrated. | - Ownership history and previous versions.<br>- Conversion of embedded URLs in content.<br>- Previous versions.<br>- Windows file and folder attributes \(like read-only and hidden\).<br>- Non-Windows New Technology File System \(NTFS\) and NTFS advanced permissions and special settings:<br>- Explicit deny permissions \(removed after migration, content subject to parallel permissions or permissions on parent folder\).<br>- NTFS auditing configuration.<br>- More file metadata provided by File Classification Infrastructure \(FCI\).<br>- Inaccessible or corrupted documents.<br>- Hidden shares.<br>- Sharing \(like permissions granted on the share level\).<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |
| **Single Google Workspace environment \(Google Drive only\)** | Single or multi-pass | - Google Docs, Sheets, and Slides \(files are converted to the equivalent Office format including files over 10 MB\).<br>- File and folder structure.<br>- User-level folder permissions.<br>- Group-level folder permissions.<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared drives \(folders and files\).<br>- Shared content owned by the Google Drive account being migrated.<br>- Google Sheets are converted to Excel files, but custom scripts, formulas, and macros **aren't** migrated.<br>- Google Forms.<br>- File versions. | - Ownership history and comments.<br>- File and folder descriptions, folder colors.<br>- Advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Blocked or inactive users.<br>- Google Photos, Maps, and other connected apps.<br>- Google Drawings.<br>- Shared content external to your organization.<br>- Content not owned by the Google Drive account being migrated.<br>- Permissions and basic metadata of guests. \(**Note**: Use Google Drive Admin reports to identify content shared with guests. Instruct end users to reshare content with guests after migration.\)<br>- Shared drive membership permissions. \(**Note**: Use Google Drive Admin reports to identify shared drive memberships. Instruct end users to configure these membership settings on the target before migration.\)<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724).<br>- Google Shortcuts. |
| **Box \(Starter, Business, Enterprise\)** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level folder permissions.<br>- Group-level folder permissions.<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared content owned by the Box account being migrated. | - Ownership history, previous versions, and comments.<br>- File and folder descriptions.<br>- Box Tags and advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Blocked or inactive users.<br>- Box Apps, Bookmarks, Favorites, and Workflows.<br>- Content not owned by the migrated Box account.<br>- Permissions and basic metadata of guests. \(**Note**: Use Box reports to identify content shared with guests. Instruct end users to reshare content with guests after migration.\)<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |
| **Dropbox for Teams \(Standard and Advanced\)** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level folder permissions.<br>- Group-level folder permissions.<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared team folders and content.<br>- Shared content owned by the Dropbox accounts being migrated. | - Ownership history, previous versions, and comments.<br>- File and folder descriptions.<br>- Advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Unmounted Dropbox folders.<br>- Deleted or disconnected users.<br>- Dropbox Paper, Showcases, and Spaces.<br>- Dropbox Apps and Favorites \(Pins/Stars\).<br>- Content not owned by the migrated Dropbox account.<br>- Permissions and basic metadata of guests. \(**Note**: Use Dropbox reports to identify content shared with guests. Instruct end users to reshare content with guests after migration.\)<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |

## FastTrack responsibilities for OneDrive migrations

Our FastTrack Specialists perform standard activities during the migration project. Before migration, you must complete the set up and configuration of Exchange Online for your migration, and meet the [FastTrack OneDrive migration prerequisites](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/file%20share/getting-started/prerequisites).

Important

FastTrack requires authentication to access the FastTrack OneDrive migration prerequisites page. If you land on a registration page after clicking the migration link, come back and click the link again to access the page after you authenticate.

### Your responsibilities

You perform standard activities during the migration project. Refer to the data migration scope and responsibilities information in the [FastTrack Migration Learning Center](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/Exchange/migration/migration-scope-and-responsibility).

Important

FastTrack requires authentication to access the FastTrack Migration Learning Center Migration page. If you land on a registration page after clicking the Learning Center link, come back and click the link again, to access the page after you authenticate.

You also perform the following activities, specific to OneDrive migrations:

- Provision all OneDrive sites that are targeted by your migration events.

## Migration to Microsoft Teams and Microsoft 365 Groups

When you choose to use FastTrack to migrate your files to Microsoft Teams and Microsoft 365 Groups, we provide migration guidance and data migration services. We provide guidance to help you plan your migration, configure your source environments and Teams and Microsoft 365 Groups, and use our data migration services to migrate your files. You create and schedule your migration events. We launch migration events in accordance with your schedule, monitor their progress, and provide status reports. When your migration events are completed, you can expect files from appropriately scheduled and eligible sources of your migrated source environments to Teams and Microsoft 365 Groups. Teams channels and Microsoft 365 Groups must be pre-provisioned by the customer before they can migrate data into these destination types. Teams and Microsoft 365 Groups impacts your permissions on the file destination location. Teams and Microsoft 365 Groups are built to allow collaboration. The Teams channel or Microsoft 365 groups determine who has access to those files when migrating into those destinations. FastTrack doesn't add end users or groups to any Teams channel or Microsoft 365 Groups permission during migration.

### Considerations

- All migrations are subject to SharePoint quotas. Refer to [SharePoint limits](https://go.microsoft.com/fwlink/?LinkId=698855) for details.
- We recommend that you limit the overall migration amount to 75% of the overall SharePoint storage quota \(including any extra storage you purchased separately\).

### Source environment details

Our data migration services migrate data from these source environments:

- File shares \(Server Message Block \(SMB\) file shares on devices supporting SMB 2.0 onward\).
- A single Google Workspace environment \(Google Drive only\).
- Box \(Starter, Business, Enterprise\).
- Dropbox for Teams \(Standard and Advanced\).

The following table presents migration details specific to each source environment:

| **Source environment** | **Type of migration** | **What migrates** | **What doesn't migrate** |
| --- | --- | --- | --- |
| **Any file share device supporting SMB 2.0 onward** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level file and folder permissions.\*<br>- Group-level file and folder permissions.\*<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>  <br>\*Directory synchronization configuration required. Only NTFS permissions exposed to the Windows File Explorer are migrated. Permissions managed directly on file share devices aren't migrated. If data is stored on an SMB 2.0 device, the NTFS-equivalent permissions exposed by the SMB protocol are migrated. Permissions are impacted by the Microsoft 365 Group and/or Microsoft Teams channel. If the destination is a Microsoft 365 Group or Microsoft Teams channel, the group or channel determines the final permissions profile on migrated files. We recommend not migrating permissions on files migrating to a Microsoft 365 Group or Microsoft Teams channel. | - Ownership history and previous versions.<br>- Conversion of embedded URLs in content.<br>- Previous versions.<br>- Windows file and folder attributes \(like read-only and hidden\).<br>- Non-Windows New Technology File System \(NTFS\) and NTFS advanced permissions and special settings:<br>- Explicit deny permissions \(removed after migration, content subject to parallel permissions or permissions on parent folder\).<br>- NTFS auditing configuration.<br>- More file metadata provided by File Classification Infrastructure \(FCI\).<br>- Inaccessible or corrupted documents.<br>- Hidden shares.<br>- Sharing \(like permissions granted on the share level\).<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |
| **Single Google Workspace environment \(Google Drive only\)** | Single or multi-pass | - Google Docs, Sheets, and Slides \(files are converted to the equivalent Office format including files over 10 MB\).<br>- File and folder structure.<br>- User-level folder permissions.\*<br>- Group-level folder permissions.\*<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared drives \(folders and files\).<br>- Shared content owned by the Google Drive account being migrated.<br>- Google Sheets are converted to Excel files, but custom scripts, formulas, and macros **aren't** migrated.<br>- Google Forms.<br>- File versions.<br><br>  <br>\*Permissions are impacted by the Microsoft 365 Group and/or Microsoft Teams channel. If the destination is a Microsoft 365 Group or Microsoft Teams channel, the group or channel determines the final permissions profile on migrated files. We recommend not migrating permissions on files migrating to a Microsoft 365 Group or Microsoft Teams channel. | - Ownership history and comments.<br>- File and folder descriptions and folder colors.<br>- Advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Blocked or inactive users.<br>- Google Photos, Maps, and other connected apps.<br>- Google Drawings.<br>- Shared content external to your organization.<br>- Content not owned by the Google Drive account being migrated.<br>- Permissions and basic metadata of guests. \(**Note**: Use Google Drive Admin reports to identify content shared with guests. Instruct end users to reshare content with guests after migration.\)<br>- Shared drive membership permissions \(**Note**: Use Google Drive Admin reports to identify shared drive memberships. Instruct end users to configure these membership settings on the target before migration.\)<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724).<br>- Google Shortcuts. |
| **Box \(Starter, Business, Enterprise\)** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level folder permissions.\*<br>- Group-level folder permissions.\*<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared content owned by the Box account being migrated.<br>- Box Notes \(converted to Word document format\).<br><br>  <br>\*Permissions are impacted by the Microsoft 365 Group and/or Microsoft Teams channel. If the destination is a Microsoft 365 Group or Microsoft Teams channel, the group or channel determines the final permissions profile on migrated files. We recommend not migrating permissions on files migrating to a Microsoft 365 Group or Microsoft Teams channel. | - Ownership history, previous versions, and comments.<br>- File and folder descriptions.<br>- Box Tags and advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Blocked or inactive users.<br>- Box Apps, Bookmarks, Favorites, and Workflows.<br>- Content not owned by the migrated Box account.<br>- Permissions and basic metadata of guests. \(**Note**: Use Box reports to identify content shared with guests. Instruct end users to reshare content with guests after migration.\)<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |
| **Dropbox for Teams \(Standard and Advanced\)** | Single or multi-pass | - Documents.<br>- File and folder structure.<br>- User-level folder permissions.\*<br>- Group-level folder permissions.\*<br>- User-level file permissions.<br>- Group-level file permissions.<br>- Files under 250 GB.<br>- Basic document and folder metadata:<br><br>  - Created date.<br>  - Modified date.<br>  - Created by.<br>  - Last modified by.<br><br>- Shared team folders and content.<br>- Shared content owned by the Dropbox accounts being migrated.<br><br>  <br>\*Permissions are impacted by the Microsoft 365 Group and/or Microsoft Teams channel. If the destination is a Microsoft 365 Group or Microsoft Teams channel, the group or channel determines the final permissions profile on migrated files. We recommend not migrating permissions on files migrating to a Microsoft 365 Group or Microsoft Teams channel. | - Ownership history, previous versions, and comments.<br>- File and folder descriptions.<br>- Advanced metadata.<br>- File lock attributes.<br>- Conversion of embedded URLs in content.<br>- Trashed items.<br>- Inaccessible or corrupted documents.<br>- Unmounted Dropbox folders.<br>- Deleted or disconnected users.<br>- Dropbox Paper, Showcases, and Spaces.<br>- Dropbox Apps and Favorites \(Pins/Stars\).<br>- Content not owned by the migrated Dropbox account.<br>- Permissions and basic metadata of guests. \(**Note**: Use Dropbox reports to identify content shared with guests. Instruct end users to reshare content with guests after migration.\)<br>- Files or folders exceeding current [SharePoint restrictions and limitations](https://go.microsoft.com/fwlink/?linkid=846724). |

## FastTrack responsibilities for Microsoft Teams and Microsoft 365 Groups migrations

Our FastTrack Specialists perform standard activities during the migration project. Before migration, you must complete the set up and configuration of Exchange Online for your migration, and meet the [FastTrack Microsoft Teams and Microsoft 365 Groups migration prerequisites](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/file%20share/getting-started/prerequisites).

Important

FastTrack requires authentication to access the FastTrack Microsoft Teams and Microsoft 365 Groups prerequisites page. If you land on a registration page after clicking the migration link, come back and click the link again to access the page after you authenticate.

### Your responsibilities

You perform standard activities during the migration project. Refer to the data migration scope and responsibilities information in the [FastTrack Migration Learning Center](https://fasttrack.microsoft.com/v2/en-us/migration/learning-center/Exchange/migration/migration-scope-and-responsibility).

Important

FastTrack requires authentication to access the FastTrack Migration Learning Center Migration page. If you land on a registration page after clicking the Learning Center link, come back and click the link again, to access the page after you authenticate.

You also perform the following activities, specific to Microsoft Teams and Microsoft 365 Groups migrations:

- Provision all Microsoft Teams channels and Microsoft 365 Groups as targeted by your migration events.

Note

FastTrack doesn't pre-provision Microsoft Teams channels or Microsoft 365 Groups. FastTrack doesn't add end users or groups to Microsoft Teams channels or Microsoft 365 Groups. You must add your end users or groups to all Microsoft Teams channels and Microsoft 365 Groups before you migrate data into those destinations so those end users have access to those newly migrated documents

To learn more about FastTrack migrations, go to the [FastTrack Migrations Learning Center](https://go.microsoft.com/fwlink/?linkid=2299423).

Note

You first need to be registered with FastTrack in order to access the FastTrack Migrations Learning Center. To register, go to [Microsoft FastTrack Registration](https://go.microsoft.com/fwlink/?linkid=2186345).
