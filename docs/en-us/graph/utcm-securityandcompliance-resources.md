<!-- Source: https://learn.microsoft.com/en-us/graph/utcm-securityandcompliance-resources -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# Supported Microsoft Security and Compliance resources for Tenant Configuration Management

This article lists the supported resource types for Microsoft Security and Compliance in the Tenant Configuration Management \(TCM\) APIs in Microsoft Graph. Use these resource types to monitor and manage your Microsoft Security and Compliance configuration settings.

For the complete schema, required permissions, and examples for each resource type, see the [TCM schema store](https://json.schemastore.org/utcm-monitor.json).

## autoSensitivityLabelPolicy resource type

### Description

This resource configures a Auto Sensitivity label policy in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name for the sensitivity label. The maximum length is 64 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| Ensure | Write | String | Specify if this label policy should exist or not. | `Present`, `Absent` |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| ApplySensitivityLabel | Write | String | The ApplySensitivityLabel parameter specifies the label to use for the auto label policy. | - |
| ExchangeSender | Write | StringArray\[\] | The ExchangeSender parameter specifies which senders to include in the policy. | - |
| ExchangeSenderException | Write | StringArray\[\] | The ExchangeSenderException parameter specifies which senders to exclude in the policy. | - |
| ExchangeSenderMemberOf | Write | StringArray\[\] | The ExchangeSenderMemberOf parameter specifies the distribution groups, mail-enabled security groups, or dynamic distribution groups to include in the auto-labeling policy. | - |
| ExchangeSenderMemberOfException | Write | StringArray\[\] | he ExchangeSenderMemberOf parameter specifies the distribution groups, mail-enabled security groups, or dynamic distribution groups to exclude from the auto-labeling policy. | - |
| ExchangeLocation | Write | StringArray\[\] | The ExchangeSender parameter specifies which senders to include in the policy. | - |
| AddExchangeLocation | Write | StringArray\[\] | This AddExchangeLocation parameter specifies new Exchange locations to be added to the policy without affecting the existing ones. | - |
| RemoveExchangeLocation | Write | StringArray\[\] | The RemoveExchangeLocation parameter removes locations on Exchange from the policy. | - |
| Mode | Write | String | The Mode parameter specifies the action and notification level of the auto-labeling policy. | `Enable`, `Disable`, `TestWithNotifications`, `TestWithoutNotifications` |
| OneDriveLocation | Write | StringArray\[\] | The OneDriveLocation parameter specifies the OneDrive for Business sites to include. You identify the site by its URL value, or you can use the value. | - |
| AddOneDriveLocation | Write | StringArray\[\] | The AddOneDriveLocation parameter specifies the OneDrive for Business sites to add to the list of included sites when you aren't using the value All for the OneDriveLocation parameter. | - |
| RemoveOneDriveLocation | Write | StringArray\[\] | The RemoveOneDriveLocation parameter specifies the OneDrive for Business sites to remove from the list of included sites when you aren't using the value All for the OneDriveLocation parameter. | - |
| AddOneDriveLocationException | Write | StringArray\[\] | This parameter specifies the OneDrive for Business sites to exclude when you use the value All for the OneDriveLocation parameter. | - |
| RemoveOneDriveLocationException | Write | StringArray\[\] | This RemoveOneDriveLocationException parameter specifies the OneDrive for Business sites to remove from the list of excluded sites when you use the value All for the OneDriveLocation parameter. | - |
| OneDriveLocationException | Write | StringArray\[\] | The AddOneDriveLocationException parameter specifies the OneDrive for Business sites to add to the list of excluded sites when you use the value All for the OneDriveLocation parameter. | - |
| Priority | Write | UInt32 | The Priority parameter specifies the priority of the policy. The highest priority policy will take action over lower priority policies if two policies are applicable for a file. | - |
| SharePointLocation | Write | StringArray\[\] | The SharePointLocation parameter specifies the SharePoint Online sites to include. You identify the site by its URL value, or you can use the value All to include all sites. | - |
| SharePointLocationException | Write | StringArray\[\] | This parameter specifies the SharePoint Online sites to exclude when you use the value All for the SharePointLocation parameter. | - |
| AddSharePointLocationException | Write | StringArray\[\] | The AddSharePointLocation parameter specifies the SharePoint Online sites to add to the list of included sites when you aren't using the value All for the SharePointLocation parameter. | - |
| RemoveSharePointLocationException | Write | StringArray\[\] | The RemoveSharePointLocationException parameter specifies the SharePoint Online sites to remove from the list of excluded sites when you use the value All for the SharePointLocation parameter. | - |
| AddSharePointLocation | Write | StringArray\[\] | The AddSharePointLocation parameter specifies the SharePoint Online sites to add to the list of included sites when you aren't using the value All for the SharePointLocation parameter. | - |
| RemoveSharePointLocation | Write | StringArray\[\] | The RemoveSharePointLocation parameter specifies the SharePoint Online sites to remove from the list of included sites when you aren't using the value All for the SharePointLocation parameter. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## caseHoldPolicy resource type

### Description

This resource configures a eDiscovery Case Policy in Security and Compliance Center.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the case hold policy. | - |
| Case | Key | String | The Case parameter specifies the eDiscovery case that you want to associate with the case hold policy. | - |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| Enabled | Write | Boolean | The Enabled parameter specifies whether the policy is enabled or disabled. | - |
| ExchangeLocation | Write | StringArray\[\] | The ExchangeLocation parameter specifies the mailboxes to include in the policy. | - |
| PublicFolderLocation | Write | StringArray\[\] | The PublicFolderLocation parameter specifies that you want to include all public folders in the case hold policy. You use the value All for this parameter. | - |
| SharePointLocation | Write | StringArray\[\] | The SharePointLocation parameter specifies the SharePoint Online and OneDrive for Business sites to include. You identify a site by its URL value. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## caseHoldRule resource type

### Description

This resource configures an eDiscovery Case Hold Rule in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies a unique name for the case hold rule. | - |
| Policy | Key | String | The Policy parameter specifies the case hold policy that contains the rule. You can use any value that uniquely identifies the policy. | - |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| ContentMatchQuery | Write | String | The ContentMatchQuery parameter specifies a content search filter. Use this parameter to create a query-based hold so only the content that matches the specified search query is placed on hold. This parameter uses a text search string or a query that's formatted by using the Keyword Query Language \(KQL\). | - |
| Disabled | Write | Boolean | The Disabled parameter specifies whether the case hold rule is enabled or disabled. | - |
| Ensure | Write | String | Present ensures the rule exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## complianceCase resource type

### Description

This resource configures an eDiscovery Case in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the compliance case. | - |
| Description | Write | String | The description of the case. | - |
| Ensure | Write | String | Specify if this case should exist or not. | `Present`, `Absent` |
| Status | Write | String | Status for the case. Can either be 'Active' or 'Closed' | `Active`, `Closed` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## complianceSearch resource type

### Description

This resource configures an Compliance Search \(eDiscovery\) in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the complaiance tag. | - |
| Case | Write | String | Compliance Case \(eDiscovery\) that this Search is associated with | - |
| AllowNotFoundExchangeLocationsEnabled | Write | Boolean | The AllowNotFoundExchangeLocationsEnabled parameter specifies whether to include mailboxes other than regular user mailboxes in the compliance search. | - |
| ContentMatchQuery | Write | String | The ContentMatchQuery parameter specifies a content search filter. This parameter uses a text search string or a query that's formatted by using the Keyword Query Language \(KQL\). | - |
| Description | Write | String | The Description parameter specifies an optional description for the compliance search. If the value contains spaces, enclose the value in quotation marks. | - |
| ExchangeLocation | Write | StringArray\[\] | The ExchangeLocation parameter specifies the mailboxes to include. | - |
| ExchangeLocationExclusion | Write | StringArray\[\] | This parameter specifies the mailboxes to exclude when you use the value All for the ExchangeLocation parameter. | - |
| HoldNames | Write | StringArray\[\] | The HoldNames parameter specifies that the content locations that have been placed on hold in the specified eDiscovery case will be searched. You use the value All for this parameter. You also need to specify the name of an eDiscovery case by using the Case parameter. | - |
| IncludeUserAppContent | Write | Boolean | The IncludeUserAppContent parameter specifies that you want to search the cloud-based storage location for users who don't have a regular Office 365 user account in your organization. These types of users include users without an Exchange Online license who use Office applications, Office 365 guest users, and on-premises users whose identity is synchronized with your Office 365 organization. | - |
| Language | Write | String | The Language parameter specifies the language for the compliance search. Valid input for this parameter is a supported culture code value from the Microsoft .NET Framework CultureInfo class. For example, da-DK for Danish or ja-JP for Japanese. | - |
| PublicFolderLocation | Write | StringArray\[\] | The PublicFolderLocation parameter specifies that you want to include all public folders in the search. You use the value All for this parameter. | - |
| SharePointLocation | Write | StringArray\[\] | The SharePointLocation parameter specifies the SharePoint Online sites to include. You identify the site by its URL value, or you can use the value All to include all sites. | - |
| SharePointLocationExclusion | Write | StringArray\[\] | This parameter specifies the SharePoint Online sites to exclude when you use the value All for the SharePointLocation parameter. You identify the site by its URL value. | - |
| Ensure | Write | String | Specify if this search should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## complianceSearchAction resource type

### Description

This resource configures a Compliance Search Action in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Action | Key | String | The Action parameter specifies what type of action to define. Accepted values are Export, Retention and Purge. | `Export`, `Preview`, `Purge`, `Retention` |
| SearchName | Key | String | The SearchName parameter specifies the name of the existing content search to associate with the content search action. You can specify multiple content searches separated by commas. | - |
| FileTypeExclusionsForUnindexedItems | Write | StringArray\[\] | The FileTypeExclusionsForUnindexedItems specifies the file types to exclude because they can't be indexed. You can specify multiple values separated by commas. | - |
| EnableDedupe | Write | Boolean | The EnableDedupe parameter eliminates duplication of messages when you export content search results. | - |
| IncludeCredential | Write | Boolean | The IncludeCredential switch specifies whether to include the credential in the results. | - |
| IncludeSharePointDocumentVersions | Write | Boolean | The IncludeSharePointDocumentVersions parameter specifies whether to export previous versions of the document when you use the Export switch. | - |
| PurgeType | Write | String | The PurgeType parameter specifies how to remove items when the action is Purge. | `SoftDelete`, `HardDelete` |
| RetryOnError | Write | Boolean | The RetryOnError switch specifies whether to retry the action on any items that failed without re-running the entire action all over again. | - |
| ActionScope | Write | String | The ActionScope parameter specifies the items to include when the action is Export. | `IndexedItemsOnly`, `UnindexedItemsOnly`, `BothIndexedAndUnindexedItems` |
| Ensure | Write | String | Specify if this action should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## complianceTag resource type

### Description

This resource configures a Compliance Tag in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the complaiance tag. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| EventType | Write | String | The EventType parameter specifies the retention rule that's associated with the label. | - |
| IsRecordLabel | Write | Boolean | The IsRecordLabel parameter specifies whether the label is a record label. | - |
| Notes | Write | String | The Notes parameter specifies an optional note. If you specify a value that contains spaces, enclose the value in quotation marks, for example: 'This is a user note' | - |
| Regulatory | Write | Boolean | Regulatory description | - |
| FilePlanProperty | Write | FilePlanProperty | The FilePlanProperty parameter specifies the file plan properties to include in the label. | - |
| ReviewerEmail | Write | StringArray\[\] | The ReviewerEmail parameter specifies the email address of a reviewer for Delete and KeepAndDelete retention actions. You can specify multiple email addresses separated by commas. | - |
| RetentionDuration | Write | String | The RetentionDuration parameter specifies the hold duration for the retention rule. Valid values are: An integer - The hold duration in days, Unlimited - The content is held indefinitely. | - |
| RetentionAction | Write | String | The RetentionAction parameter specifies the action for the label. Valid values are: Delete, Keep or KeepAndDelete. | `Delete`, `Keep`, `KeepAndDelete` |
| RetentionType | Write | String | The RetentionType parameter specifies whether the retention duration is calculated from the content creation date, tagged date, or last modification date. Valid values are: CreationAgeInDays, EventAgeInDays,ModificationAgeInDays, or TaggedAgeInDays. | `CreationAgeInDays`, `EventAgeInDays`, `ModificationAgeInDays`, `TaggedAgeInDays` |

#### FilePlanProperty

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| FilePlanPropertyDepartment | Write | String | File plan department. Can get list by running Get-FilePlanPropertyDepartment. | - |
| FilePlanPropertyAuthority | Write | String | File plan Authority. Can get list by running Get-FilePlanPropertyAuthority. | - |
| FilePlanPropertyCategory | Write | String | File plan category. Can get a list by running Get-FilePlanPropertyCategory. | - |
| FilePlanPropertyCitation | Write | String | File plan citation. Can get a list by running Get-FilePlanPropertyCitation. | - |
| FilePlanPropertyReferenceId | Write | String | File plan reference id. Can get a list by running Get-FilePlanPropertyReferenceId. | - |
| FilePlanPropertySubCategory | Write | String | File plan subcategory. Can get a list by running Get-FilePlanPropertySubCategory. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## deviceConditionalAccessPolicy resource type

### Description

This resource configures a Device Conditional Access Policy in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The name of the Device Conditional Access Policy. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| Enabled | Write | Boolean | The Enabled parameter specifies whether the policy is enabled. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## deviceConfigurationPolicy resource type

### Description

This resource configures a Device Configuration Policy in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The name of the Device Configuration Policy. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| Enabled | Write | Boolean | The Enabled parameter specifies whether the policy is enabled. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## dlpCompliancePolicy resource type

### Description

This resource configures a Data Loss Prevention Compliance Policy in Security and Compliance Center.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the DLP policy. If the value contains spaces, enclose the value in quotation marks. | - |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| EndpointDlpLocation | Write | StringArray\[\] | The EndpointDLPLocation parameter specifies the user accounts to include in the DLP policy for Endpoint DLP when they are logged on to an onboarded device. You identify the account by name or email address. You can use the value All to include all user accounts. | - |
| EndpointDlpLocationException | Write | StringArray\[\] | The EndpointDlpLocationException parameter specifies the user accounts to exclude from Endpoint DLP when you use the value All for the EndpointDlpLocation parameter. You identify the account by name or email address. | - |
| OnPremisesScannerDlpLocation | Write | StringArray\[\] | The OnPremisesScannerDlpLocation parameter specifies the on-premises file shares and SharePoint document libraries and folders to include in the DLP policy. You can use the value All to include all on-premises file shares and SharePoint document libraries and folders. | - |
| OnPremisesScannerDlpLocationException | Write | StringArray\[\] | The OnPremisesScannerDlpLocationException parameter specifies the on-premises file shares and SharePoint document libraries and folders to exclude from the DLP policy if you use the value All for the OnPremisesScannerDlpLocation parameter. | - |
| PowerBIDlpLocation | Write | StringArray\[\] | The PowerBIDlpLocation parameter specifies the Power BI workspace IDs to include in the DLP policy. Only workspaces hosted in Premium Gen2 capacities are permitted. You can use the value All to include all supported workspaces. | - |
| PowerBIDlpLocationException | Write | StringArray\[\] | The PowerBIDlpLocationException parameter specifies the Power BI workspace IDs to exclude from the DLP policy when you use the value All for the PowerBIDlpLocation parameter. Only workspaces hosted in Premium Gen2 capacities are permitted. | - |
| ThirdPartyAppDlpLocation | Write | StringArray\[\] | The ThirdPartyAppDlpLocation parameter specifies the non-Microsoft cloud apps to include in the DLP policy. You can use the value All to include all connected apps. | - |
| ThirdPartyAppDlpLocationException | Write | StringArray\[\] | The ThirdPartyAppDlpLocationException parameter specifies the non-Microsoft cloud apps to exclude from the DLP policy when you use the value All for the ThirdPartyAppDlpLocation parameter. | - |
| ExchangeLocation | Write | StringArray\[\] | The ExchangeLocation parameter specifies Exchange Online mailboxes to include in the DLP policy. You can only use the value All for this parameter to include all mailboxes. | - |
| ExchangeSenderMemberOf | Write | StringArray\[\] | Exchange members to include. | - |
| ExchangeSenderMemberOfException | Write | StringArray\[\] | Exchange members to exclude. | - |
| Mode | Write | String | The Mode parameter specifies the action and notification level of the DLP policy. Valid values are: Enable, TestWithNotifications, TestWithoutNotifications, Disable and PendingDeletion. | `Enable`, `TestWithNotifications`, `TestWithoutNotifications`, `Disable`, `PendingDeletion` |
| OneDriveLocation | Write | StringArray\[\] | The OneDriveLocation parameter specifies the OneDrive for Business sites to include. You identify the site by its URL value, or you can use the value All to include all sites. | - |
| OneDriveLocationException | Write | StringArray\[\] | This parameter specifies the OneDrive for Business sites to exclude when you use the value All for the OneDriveLocation parameter. You identify the site by its URL value. | - |
| Priority | Write | UInt32 | Priority for the Policy. | - |
| SharePointLocation | Write | StringArray\[\] | The SharePointLocation parameter specifies the SharePoint Online sites to include. You identify the site by its URL value, or you can use the value All to include all sites. | - |
| SharePointLocationException | Write | StringArray\[\] | This parameter specifies the SharePoint Online sites to exclude when you use the value All for the SharePointLocation parameter. You identify the site by its URL value. | - |
| TeamsLocation | Write | StringArray\[\] | Teams locations to include | - |
| TeamsLocationException | Write | StringArray\[\] | Teams locations to exclude. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## filePlanPropertyAuthority resource type

### Description

This resource configures an authority entry for Security and Compliance File Plans.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the Authority. | - |
| Ensure | Write | String | Specify if this authority should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## filePlanPropertyCategory resource type

### Description

This resource configures a category entry for Security and Compliance File Plans.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the category. | - |
| Ensure | Write | String | Specify if this category should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## filePlanPropertyCitation resource type

### Description

This resource configures a citation entry for Security and Compliance File Plans.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the citation. | - |
| CitationUrl | Write | String | URL of the citation. | - |
| CitationJurisdiction | Write | String | Jurisdiction of the citation. | - |
| Ensure | Write | String | Specify if this citation should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## filePlanPropertyDepartment resource type

### Description

This resource configures a department entry for Security and Compliance File Plans.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the department. | - |
| Ensure | Write | String | Specify if this department should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## filePlanPropertyReferenceId resource type

### Description

This resource configures a reference ID entry for Security and Compliance File Plans.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the reference id. | - |
| Ensure | Write | String | Specify if this reference id should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## filePlanPropertySubCategory resource type

### Description

This resource configures a sub-category entry for Security and Compliance File Plans.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the sub-category. | - |
| Category | Required | String | The Category parameter specifies the name of the parent category associated with the sub-category. | - |
| Ensure | Write | String | Specify if this category should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## labelPolicy resource type

### Description

This resource configures a Sensitivity label policy in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name for the sensitivity label. The maximum length is 64 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| Ensure | Write | String | Specify if this label policy should exist or not. | `Present`, `Absent` |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| AdvancedSettings | Write | LabelSetting\[\] | The AdvancedSettings parameter enables client-specific features and capabilities on the sensitivity label. The settings that you configure with this parameter only affect apps that are designed for the setting. | - |
| ExchangeLocation | Write | StringArray\[\] | The ExchangeLocation parameter specifies the mailboxes to include in the policy. | - |
| ExchangeLocationException | Write | StringArray\[\] | The ExchangeLocationException parameter specifies the mailboxes to exclude when you use the value All for the ExchangeLocation parameter. | - |
| ModernGroupLocation | Write | StringArray\[\] | The ModernGroupLocation parameter specifies the Microsoft 365 Groups to include in the policy. | - |
| ModernGroupLocationException | Write | StringArray\[\] | The ModernGroupLocationException parameter specifies the Microsoft 365 Groups to exclude when you're using the value All for the ModernGroupLocation parameter. | - |
| Labels | Write | StringArray\[\] | The Labels parameter specifies the sensitivity labels that are associated with the policy. You can use any value that uniquely identifies the label. | - |
| AddExchangeLocation | Write | StringArray\[\] | The AddExchangeLocation parameter specifies the mailboxes to add in the existing policy. | - |
| AddExchangeLocationException | Write | StringArray\[\] | The AddExchangeLocationException parameter specifies the mailboxes to add to exclusions when you use the value All for the ExchangeLocation parameter. | - |
| AddModernGroupLocation | Write | StringArray\[\] | The AddModernGroupLocation parameter specifies the Microsoft 365 Groups to add to include the policy. | - |
| AddModernGroupLocationException | Write | StringArray\[\] | The AddModernGroupLocationException parameter specifies the Microsoft 365 Groups to add to exclusions when you're using the value All for the ModernGroupLocation parameter. | - |
| AddLabels | Write | StringArray\[\] | The AddLabels parameter specifies the sensitivity labels to add to the policy. You can use any value that uniquely identifies the label. | - |
| RemoveExchangeLocation | Write | StringArray\[\] | The RemoveExchangeLocation parameter specifies the mailboxes to remove from the policy. | - |
| RemoveExchangeLocationException | Write | StringArray\[\] | The RemoveExchangeLocationException parameter specifies the mailboxes to remove when you use the value All for the ExchangeLocation parameter. | - |
| RemoveModernGroupLocation | Write | StringArray\[\] | The RemoveModernGroupLocation parameter specifies the Microsoft 365 Groups to remove from the policy. | - |
| RemoveModernGroupLocationException | Write | StringArray\[\] | The RemoveModernGroupLocationException parameter specifies the Microsoft 365 Groups to remove from excluded values when you're using the value All for the ModernGroupLocation parameter. | - |
| RemoveLabels | Write | StringArray\[\] | The RemoveLabels parameter specifies the sensitivity labels that are removed from the policy. You can use any value that uniquely identifies the label. | - |

#### LabelSetting

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Key | Write | String | Advanced settings key. | - |
| Value | Write | StringArray\[\] | Advanced settings value. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## protectionAlert resource type

### Description

This resource configures a Protection Alert in Security and Compliance Center.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AlertBy | Write | StringArray\[\] | Specifies the scope for aggregated alert policies | - |
| AlertFor | Write | StringArray\[\] | This parameter is reserved for internal Microsoft use | - |
| AggregationType | Write | String | Specifies how the alert policy triggers alerts for multiple occurrences of monitored activity | `None`, `SimpleAggregation`, `AnomalousAggregation`, `CustomAggregation` |
| Category | Write | String | Specifies a category for the alert policy | - |
| Comment | Write | String | Specifies an optional comment | - |
| Disabled | Write | Boolean | Enables or disables the alert policy | - |
| Ensure | Write | String | Specify if this alert should exist or not. | `Present`, `Absent` |
| Filter | Write | String | The Filter parameter uses OPATH syntax to filter the results by the specified properties and values | - |
| Name | Key | String | Specifies the unique name for the alert policy | - |
| NotificationCulture | Write | String | Specifies the language or locale that's used for notifications. For example, da-DK for Danish | - |
| NotificationEnabled | Write | Boolean | NotificationEnabled true or false | - |
| NotifyUserOnFilterMatch | Write | Boolean | Specifies whether to trigger an alert for a single event when the alert policy is configured for aggregated activity | - |
| NotifyUserSuppressionExpiryDate | Write | DateTime | Specifies whether to temporarily suspend notifications for the alert policy. Until the specified date-time, no notifications are sent for detected activities. | - |
| NotifyUserThrottleThreshold | Write | UInt32 | Specifies the maximum number of notifications for the alert policy within the time period specified by the NotifyUserThrottleWindow parameter. Once the maximum number of notifications has been reached in the time period, no more notifications are sent for the alert. | - |
| NotifyUserThrottleWindow | Write | UInt32 | Specifies the time interval in minutes that's used by the NotifyUserThrottleThreshold parameter | - |
| NotifyUser | Write | StringArray\[\] | Specifies the SMTP address of the user who receives notification messages for the alert policy. You can specify multiple values separated by commas | - |
| Operation | Write | StringArray\[\] | Specifies the activities that are monitored by the alert policy | - |
| PrivacyManagementScopedSensitiveInformationTypes | Write | StringArray\[\] | PrivacyManagementScopedSensitiveInformationTypes | - |
| PrivacyManagementScopedSensitiveInformationTypesForCounting | Write | StringArray\[\] | PrivacyManagementScopedSensitiveInformationTypesForCounting | - |
| PrivacyManagementScopedSensitiveInformationTypesThreshold | Write | UInt64 | PrivacyManagementScopedSensitiveInformationTypesThreshold | - |
| Severity | Write | String | specifies the severity of the detection | `Low`, `Medium`, `High`, `Informational` |
| ThreatType | Write | String | Specifies the type of activities that are monitored by the alert policy | `Activity`, `Malware`, `Phish`, `Malicious`, `MaliciousUrlClick`, `MailFlow` |
| Threshold | Write | UInt32 | Specifies the number of detections that trigger the alert policy within the time period specified by the TimeWindow parameter. A valid value is an integer that's greater than or equal to 3. | - |
| TimeWindow | Write | UInt32 | Specifies the time interval in minutes for number of detections specified by the Threshold parameter. A valid value is an integer that's greater than 60 \(one hour\). | - |
| VolumeThreshold | Write | UInt32 | Volume Threshold | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## retentionCompliancePolicy resource type

### Description

This resource configures a Retention Compliance Policy in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the retention policy. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| DynamicScopeLocation | Write | StringArray\[\] | Location of the dynamic scope for this policy. | - |
| Enabled | Write | Boolean | Determines if the policy is enabled or not. | - |
| ExchangeLocation | Write | StringArray\[\] | The ExchangeLocation parameter specifies the mailboxes to include. | - |
| ExchangeLocationException | Write | StringArray\[\] | This parameter specifies the mailboxes to remove from the list of excluded mailboxes when you use the value All for the ExchangeLocation parameter | - |
| ModernGroupLocation | Write | StringArray\[\] | The ModernGroupLocation parameter specifies the Office 365 groups to include in the policy. | - |
| ModernGroupLocationException | Write | StringArray\[\] | The ModernGroupLocationException parameter specifies the Office 365 groups to exclude when you're using the value All for the ModernGroupLocation parameter. | - |
| OneDriveLocation | Write | StringArray\[\] | The OneDriveLocation parameter specifies the OneDrive for Business sites to include. You identify the site by its URL value, or you can use the value All to include all sites. | - |
| OneDriveLocationException | Write | StringArray\[\] | This parameter specifies the OneDrive for Business sites to exclude when you use the value All for the OneDriveLocation parameter. You identify the site by its URL value. | - |
| PublicFolderLocation | Write | StringArray\[\] | The PublicFolderLocation parameter specifies that you want to include all public folders in the retention policy. You use the value All for this parameter. | - |
| RestrictiveRetention | Write | Boolean | The RestrictiveRetention parameter specifies whether Preservation Lock is enabled for the policy. | - |
| SharePointLocation | Write | StringArray\[\] | The SharePointLocation parameter specifies the SharePoint Online sites to include. You identify the site by its URL value, or you can use the value All to include all sites. | - |
| SharePointLocationException | Write | StringArray\[\] | This parameter specifies the SharePoint Online sites to exclude when you use the value All for the SharePointLocation parameter. You identify the site by its URL value. | - |
| SkypeLocation | Write | StringArray\[\] | The SkypeLocation parameter specifies the Skype for Business Online users to include in the policy. | - |
| SkypeLocationException | Write | StringArray\[\] | This parameter is reserved for internal Microsoft use. | - |
| TeamsChannelLocation | Write | StringArray\[\] | The TeamsChannelLocation parameter specifies the Teams Channel to include in the policy. | - |
| TeamsChannelLocationException | Write | StringArray\[\] | This parameter specifies the SharePoint Online sites to exclude when you use the value All for the TeamsChannelLocation parameter. You identify the site by its URL value. | - |
| TeamsChatLocation | Write | StringArray\[\] | The TeamsChatLocation parameter specifies the Teams Chat to include in the policy. | - |
| TeamsChatLocationException | Write | StringArray\[\] | This parameter specifies the SharePoint Online sites to exclude when you use the value All for the TeamsChatLocation parameter. You identify the site by its URL value. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## retentionComplianceRule resource type

### Description

This resource configures a Retention Compliance Rule in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the retention rule. | - |
| Policy | Required | String | The Policy parameter specifies the policy to contain the rule. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| ExpirationDateOption | Write | String | The ExpirationDateOption parameter specifies whether the expiration date is calculated from the content creation date or last modification date. Valid values are: CreationAgeInDays and ModificationAgeInDays. | `CreationAgeInDays`, `ModificationAgeInDays` |
| ExcludedItemClasses | Write | StringArray\[\] | The ExcludedItemClasses parameter specifies the types of messages to exclude from the rule. You can use this parameter only to exclude items from a hold policy, which excludes the specified item class from being held. Using this parameter won't exclude items from deletion policies. Typically, you use this parameter to exclude voicemail messages, IM conversations, and other Skype for Business Online content from being held by a hold policy. | - |
| ContentMatchQuery | Write | String | The ContentMatchQuery parameter specifies a content search filter. | - |
| RetentionComplianceAction | Write | String | The RetentionComplianceAction parameter specifies the retention action for the rule. Valid values are: Delete, Keep and KeepAndDelete. | `Delete`, `Keep`, `KeepAndDelete` |
| RetentionDuration | Write | String | The RetentionDuration parameter specifies the hold duration for the retention rule. Valid values are: An integer - The hold duration in days, Unlimited - The content is held indefinitely. | - |
| RetentionDurationDisplayHint | Write | String | The RetentionDurationDisplayHint parameter specifies the units that are used to display the retention duration in the Security and Compliance Center. Valid values are: Days, Months or Years. | `Days`, `Months`, `Years` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## retentionEventType resource type

### Description

This resource configures a Retention Event Type in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the retention event type. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## securityFilter resource type

### Description

This resource configures a Security Filter in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| FilterName | Key | String | The FilterName parameter specifies the name of the compliance security filter that you want to view. If the value contains spaces, enclose the value in quotation marks \("\). | - |
| Action | Write | String | The Action parameter filters the results by the type of search action that a filter is applied to. | `Export`, `Preview`, `Purge`, `Search`, `All` |
| Users | Write | StringArray\[\] | The User parameter filters the results by the user who gets a filter applied to their searches. Acceptable values are : The alias or email address of a user, All or The name of a role group | - |
| Description | Write | String | The Description parameter specifies a description for the compliance security filter. The maximum length is 256 characters. If the value contains spaces, enclose the value in quotation marks \("\). | - |
| Filters | Write | StringArray\[\] | The Filters parameter specifies the search criteria for the compliance security filter. The filters are applied to the users specified by the Users parameter. You can create three different types of filters: Mailbox filter, Mailbox content filter or Site and site content filter | - |
| Region | Write | String | The Region parameter specifies the satellite location for multi-geo tenants to conduct eDiscovery searches in. | `APC`, `AUS`, `CAN`, `EUR`, `FRA`, `GBR`, `IND`, `JPN`, `LAM`, `NAM`, `` |
| Ensure | Write | String | Specify if this label policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## supervisoryReviewPolicy resource type

### Description

This resource configures a Supervision Policy in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name for the supervisory review policy. The name can't exceed 64 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| Comment | Write | String | The Comment parameter specifies an optional comment. If you specify a value that contains spaces, enclose the value in quotation marks. | - |
| Reviewers | Required | StringArray\[\] | The Reviewers parameter specifies the SMTP addresses of the reviewers for the supervisory review policy. You can specify multiple email addresses separated by commas. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## supervisoryReviewRule resource type

### Description

This resource configures a Supervision Review Rule in Security and Compliance.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name for the supervisory review policy. The name can't exceed 64 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| Policy | Key | String | The Policy parameter specifies the supervisory review policy that's assigned to the rule. You can use any value that uniquely identifies the policy. | - |
| Condition | Write | String | The Condition parameter specifies the conditions and exceptions for the rule. | - |
| SamplingRate | Write | UInt32 | The SamplingRate parameter specifies the percentage of communications for review. If you want reviewers to review all detected items, use the value 100. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Compliance Administrator |
| Update | Compliance Administrator |

#### Office 365 Exchange Online

To authenticate with the Security and Compliance APIs, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## Related content

- [Overview of the Tenant Configuration Management APIs](https://learn.microsoft.com/en-us/graph/unified-tenant-configuration-management-concept-overview)
- [Set up authentication for TCM](https://learn.microsoft.com/en-us/graph/utcm-authentication-setup)
