<!-- Source: https://learn.microsoft.com/en-us/graph/data-connect-datasets -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Datasets, regions, and sinks supported by Microsoft Graph Data Connect

Microsoft Graph Data Connect supports a variety of datasets, data regions, and storage locations in Microsoft Azure. This article describes the supported datasets and how to access the dataset schemas, the Microsoft 365 and Microsoft Azure regions that are supported, and the storage locations that Microsoft Graph Data Connect utilizes through Azure Synapse or Azure Data Factory.

## Datasets

Microsoft Graph Data Connect currently supports the following datasets. To view the schemas for each dataset, create a new dataset in Azure Synapse or Azure Data Factory and go to the Schema tab.

### Activities

| Dataset name | Description | Learn more |
| --- | --- | --- |
| OutlookContactActivity\_v0 | Provides employees' activity with their contacts in Microsoft Outlook. | [OutlookContactActivity\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-outlookcontactactivity.md) |
| OutlookMailActivity\_v0 | Provides employees' activity with their email in Outlook. | [OutlookMailActivity\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-outlookmailactivity.md) |
| OutlookMeetingActivity\_v0 | Provides employees' activity with their meetings in Outlook. | [OutlookMeetingActivity\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-outlookmeetingactivity.md) |
| TeamsChannelActivity\_v0 | Providesemployees' activity with their channels in Microsoft Teams. | [TeamsChannelActivity\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-teamschannelactivity.md) |
| TeamsConversationActivity\_v0 | Provides employees' activity with their teams and chats in Teams. | [TeamsConversationActivity\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-teamsconversationactivity.md) |

### Call records

| Dataset name | Description | Learn more |
| --- | --- | --- |
| TeamsCallRecords\_v1 | Provides activity records from Teams calls and meetings. | [TeamsCallRecords\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-teamscallrecords1.md) |

### Channel

| Dataset name | Description | Learn more |
| --- | --- | --- |
| TeamsChannelDetails\_v0 | Generates a list of Microsoft Teams channels. | [TeamsChannelDetails\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-teamschanneldetails.md) |

### Contact

| Dataset name | Description | Learn more |
| --- | --- | --- |
| Contact\_v0 | Provides contact details available from each user's address book. | [Contact\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-contact.md) |
| Contact\_v1 | Provides the contact details available from each user's address book. | [Contact\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-contact1.md) |

### Devices and Licenses

| Dataset name | Description | Learn more |
| --- | --- | --- |
| OwnedDevices\_v0 | Provides detailed information related to all the devices that are owned by each user in the organization. | [OwnedDevices\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-owneddevices.md) |
| RegisteredDevices\_v0 | Provides detailed information related to all the devices that a user is registered on in the organization. | [RegisteredDevices\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-registereddevices.md) |
| LicenseDetails\_v0 | Provides details for users' licenses that are directly assigned and those transitively assigned through memberships in licensed groups. | [LicenseDetails\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-licensedetails.md) |

### Event

| Dataset name | Description | Learn more |
| --- | --- | --- |
| CalendarView\_v0 | Provides occurrences, exceptions and single instances of events, based on the calendar view from users' calendars. | [CalendarView\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-calendarview.md) |
| ConferenceRoomCalendar\_v0 | Provides CalendarView data of the Conference Rooms created for a tenant. | [ConferenceRoomCalendar\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-conferenceroomcalendar.md) |
| Event\_v0 | Provides all the events from users' calendars. | [Event\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-event.md) |
| Event\_v1 | Provides all the events from users' calendars. | [Event\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-event1.md) |

### Group

| Dataset name | Description | Learn more |
| --- | --- | --- |
| GroupDetails\_v0 | Provides the Microsoft Entra ID \(Azure AD\) groups data for a tenant. | [GroupDetails\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-groupdetails.md) |
| GroupMembers\_v0 | Generates a list of direct members of all groups. | [GroupMembers\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-groupmembers.md) |
| GroupOwners\_v0 | Retrieves the list of all the group owners. | [GroupOwners\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-groupowners.md) |

### Mail

| Dataset name | Description | Learn more |
| --- | --- | --- |
| Message\_v0 | Provides a collection of all the messages received by a user in mail folders. | [Message\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-message.md) |
| Message\_v1 | Provides a collection of all the messages received by a user in mail folders. | [Message\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-message1.md) |
| SentItems\_v0 | Provides a collection of all the sent emails by all users of a tenant. | [SentItems\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-sentitems.md) |
| SentItems\_v1 | Provides a collection of all the sent emails with some additional fields. | [SentItems\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-sentitems1.md) |

### Mail folder

| Dataset name | Description | Learn more |
| --- | --- | --- |
| Inbox\_v1 | Provides the messages from users' mail folders. | [Inbox\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-inbox.md) |
| Mailfolder\_v0 | Provides information on all the folders created in a user's mailbox. | [Mailfolder\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-mailfolder.md) |
| Mailfolder\_v2 | Provides the information on all mail folders created in a user's mailbox. | [Mailfolder\_v2 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-mailfolder2.md) |

### Mailbox settings

| Dataset name | Description | Learn more |
| --- | --- | --- |
| MailboxSettings\_v0 | Provides details of all users' mailbox settings. | [MailboxSettings\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-mailboxsettings.md) |

### Message

| Dataset name | Description | Learn more |
| --- | --- | --- |
| OutlookGroupConversations\_v0 | Provides a collection of group conversations between users of tenant. | [OutlookGroupConversations\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-outlookgroupconversations.md) |
| TeamChat\_v1 | Provides Teams chat messages for one-on-one and group chat messages. | [TeamChat\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-teamchat.md) |
| TeamChat\_v2 | Provides Teams chat messages for one-on-one and group chat messages. | [TeamChat\_v2 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-teamchat2.md) |
| TeamsStandardChannelMessages\_v0 | Provides channel posts and messages from standard channels in Teams. | [TeamsStandardChannelMessages\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-teamsstandardchannelmessages.md) |

### Online meetings

| Dataset name | Description | Learn more |
| --- | --- | --- |
| TeamsTranscript\_v1 | Provides transcripts from calls and meetings in Teams when the transcript is enabled for a meeting or a call. | [TeamsTranscript\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-teamstranscript1.md) |

### Org hierarchy

| Dataset name | Description | Learn more |
| --- | --- | --- |
| DirectReport\_v0 | Provides details of all the direct reports for your users. | [DirectReport\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-directreport.md) |
| Manager\_v0 | Provides a list of users assigned as managers. | [Manager\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-manager.md) |

### Task

| Dataset name | Description | Learn more |
| --- | --- | --- |
| TodoTaskFolders\_v0 | Identifies task folders in Microsoft Outlook that track user-level work items. | [TodoTaskFolders\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-todotaskfolders.md) |
| TodoTasks\_v0 | Identifies tasks in Microsoft Outlook that track user-level work items. | [TodoTasks\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-todotasks.md) |
| PlannerTasks\_v0 | Identifies tasks in Planner that track user-level work items. | [PlannerTasks\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-plannertasks.md) |

### User

| Dataset name | Description | Learn more |
| --- | --- | --- |
| User\_v0 | Provides user details stored for all the Microsoft Entra ID \(Azure AD\) user accounts that are created for a particular tenant. | [User\_v0 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-user.md) |
| User\_v1 | Provides user details stored for all the Microsoft Entra ID \(Azure AD\) user accounts. | [User\_v1 dataset](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-user1.md) |

### OneDrive and SharePoint Online

| Dataset name | Description | Sample and Schema |
| --- | --- | --- |
| SharePointSites\_v1 | Contains information about SharePoint sites. | [SharePointSites\_v1](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-sharepointsites.md) |
| SharePointPermissions\_v1 | Contains information about sharing permissions. | [SharePointPermissions\_v1](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-sharepointpermissions.md) |
| SharePointGroups\_v1 | Contains SharePoint group information, including details about group members. | [SharePointGroups\_v1](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-sharepointgroups.md) |
| SharePointFiles\_v1 | Contains information about SharePoint files. | [SharePointFiles\_v1](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-sharepointfiles.md) |
| SharePointFileActions\_v1 | Contains information about SharePoint file actions. | [SharePointFileActions\_v1](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-sharepointfileactions.md) |
| OneDriveSyncHealth\_v1 | Contains information about devices running OneDrive for work or school. | [OneDriveSyncHealth\_v1](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-onedrivesynchealth.md) |
| OneDriveSyncErrors\_v1 | Contains details about errors on devices running OneDrive for work or school. | [OneDriveSyncErrors\_v1](https://github.com/microsoftgraph/dataconnect-solutions/blob/main/Datasets/data-connect-dataset-onedrivesyncerrors.md) |

### Viva Insights

| Dataset name | Description | Sample and Schema | License |
| --- | --- | --- | --- |
| VivaInsightsDataset\_Report\_v1\_{Viva\_Insights\_Query\_Name} | Contains metrics according to the query authored by the user in Viva Insights. | Varies per report. | Requires Viva Insights license. |

> **Note:** `{Viva_Insights_Query_Name}` represents a placeholder for the Viva Insights query name that, when combined with VivaInsightsDataset\_Report\_v1\_, forms the dataset name.

## Regions

Microsoft Graph Data Connect supports extracting data from a variety of Microsoft 365 regions. To successfully move data from the Microsoft 365 data center into your Microsoft Azure storage, the Azure Synapse or Azure Data Factory instance and the Azure storage location must both map to a supported region for the location of the Microsoft 365 data.

The following table indicates which Microsoft 365 regions are supported and the corresponding Azure regions required for data movement.

| Office region | Azure region |
| --- | --- |
| **Asia-Pacific** | - East Asia<br>- Southeast Asia |
| **Australia** | - Australia East<br>- Australia Southeast |
| **Europe** | - North Europe<br>- West Europe |
| **North America** | - Central US<br>- East US<br>- East US 2<br>- North Central US<br>- South Central US<br>- West Central US<br>- West US<br>- West US 2 |
| **Brazil** | - Brazil South |
| **United Kingdom** | - UK South<br>- UK West |
| **Canada \(CAN\)** | - Canada Central<br>- Canada East |
| **Japan \(JPN\)** | - Japan West<br>- Japan East |
| **India \(IND\)** | - South India<br>- Central India |
| **Korea \(KOR\)** | - Korea Central<br>- Korea South |
| **Switzerland \(CHE\)** | - Switzerland North |
| **Germany \(DEU\)** | - Germany West Central |
| **Norway \(NOR\)** | - Norway East |
| **France \(FRA\)** | - France Central |
| **UAE \(UAE\)** | - UAE North |

## Sinks

Sinks are the output location that Azure Synapse or Azure Data Factory uses to place data in Azure storage. Microsoft Graph Data Connect supports the following sink storage types:

- [Azure Data Lake Storage Gen2](https://learn.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction)
- [Azure Storage Blob](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blobs-overview)
- [Azure SQL DB](https://azure.microsoft.com/products/azure-sql/database/?ef_id=_k_790773b85b8d1e4ef64317867aeee8a0_k_&OCID=AIDcmm5edswduu_SEM__k_790773b85b8d1e4ef64317867aeee8a0_k_&msclkid=790773b85b8d1e4ef64317867aeee8a0) \(mapping data flows only\)
- [Microsoft Fabric OneLake](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview)

The following characteristics apply to sinks:

- Service Principal authentication is the only supported authentication mechanism for all sink types in a copy activity with Microsoft 365 as the source.
- When using Azure Storage Blob as the sink, you must ensure that your application has Storage Blob Data Contributor access to the Azure Storage Blob location.
- For copy activity, the output files are formatted as JSON. This format is fixed and modifying the format isn't supported. However, you can use Azure Synapse or Azure Data Factory to copy the result of a Microsoft Graph Data Connect pipeline into another storage mechanism \(such as Azure SQL Database\).
- Mapping data flows: [Copy and transform data from Microsoft 365 \(Office 365\) - Azure Data Factory & Azure Synapse \| Microsoft Learn \|](https://learn.microsoft.com/en-us/azure/data-factory/connector-office-365?tabs=data-factory#transform-data-with-the-microsoft-365-connector)

  - Output can be in parquet format. For details about the supported data transformations, see [Flatten transformation in mapping data flow](https://learn.microsoft.com/en-us/azure/data-factory/data-flow-flatten).
  - Microsoft Graph Data Connect on mapping data flows supports direct output of the data into Azure SQL DB.

The following table indicates the areas that are supported for the corresponding copy activity and mapping data flows.

| Area | Copy activity | Mapping data flows |
| --- | --- | --- |
| Output data formats supported | JSON | JSON, Parquet |
| Data transformation \(normalization/flattening/etc.\) | Requires additional transformation step in the ADF/Synapse pipeline | Supports inline transformations |
| Supported data sinks | ADLS gen2, Azure Blob | ADLS gen2, Azure Blob, Azure SQL DB |
| Azure VNET IR | Not supported | Supported |

## Related content

- [Azure Synapse and Azure Data Factory connector for Microsoft 365 data](https://learn.microsoft.com/en-us/azure/data-factory/connector-office-365)
