<!-- Source: https://learn.microsoft.com/en-us/graph/utcm-exchange-resources -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# Supported Microsoft Exchange resources for Tenant Configuration Management

This article lists the supported resource types for Microsoft Exchange in the Tenant Configuration Management \(TCM\) APIs in Microsoft Graph. Use these resource types to monitor and manage your Microsoft Exchange configuration settings.

For the complete schema, required permissions, and examples for each resource type, see the [TCM schema store](https://json.schemastore.org/utcm-monitor.json).

## acceptedDomain resource type

### Description

This resource configures the Accepted Email Domains in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specify the Fully Qualified Domain Name for the AcceptedDomain. | - |
| Ensure | Write | String | Specify if the AcceptedDomain should exist or not. | `Present`, `Absent` |
| DomainType | Write | String | The type of AcceptedDomain. Currently the EXOAcceptedDomain DSC Resource accepts a value of 'Authoritative' and 'InternalRelay'. | `Authoritative`, `InternalRelay` |
| MatchSubDomains | Write | Boolean | The MatchSubDomains parameter must be false on Authoritative domains. The default value is false. | - |
| OutboundOnly | Write | Boolean | OutboundOnly can only be enabled if the DomainType parameter is set to Authoritative or InternalRelay. The default value is false. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Retention Management, Remote and Accepted Domains, Distribution Groups, View-Only Configuration, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## activeSyncDeviceAccessRule resource type

### Description

This resource configures Active Sync Device Access Rules in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the identity of the device access rule. | - |
| AccessLevel | Write | String | The AccessLevel parameter specifies whether the devices are allowed, blocked or quarantined. | `Allow`, `Block`, `Quarantine` |
| Characteristic | Write | String | The Characteristic parameter specifies the device characteristic or category that's used by the rule. | `DeviceModel`, `DeviceType`, `DeviceOS`, `UserAgent`, `XMSWLHeader` |
| QueryString | Write | String | The QueryString parameter specifies the device identifier that's used by the rule. This parameter uses a text value that's used with Characteristic parameter value to define the device. | - |
| Ensure | Write | String | Specify if the Active Sync Device Access Rule should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Organization Client Access, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## antiPhishPolicy resource type

### Description

This resource configures an [Anti-Phish Policy in Exchange Online](https://learn.microsoft.com/en-us/powershell/module/exchange/advanced-threat-protection/new-antiphishpolicy?view=exchange-ps).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the antiphishing policy that you want to modify. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |
| AdminDisplayName | Write | String | The AdminDisplayName parameter specifies a description for the policy. | - |
| PhishThresholdLevel | Write | String | The PhishThresholdLevel parameter specifies the tolerance level that's used by machine learning in the handling of phishing messages. | `1`, `2`, `3`, `4` |
| AuthenticationFailAction | Write | String | The AuthenticationFailAction parameter specifies the action to take when the message fails composite authentication. | `MoveToJmf`, `Quarantine` |
| TargetedUserProtectionAction | Write | String | The TargetedUserProtectionActionâ¯parameter specifies the action to take on detected user impersonation messages for the users specified by the TargetedUsersToProtect parameter. | `BccMessage`, `Delete`, `MoveToJmf`, `NoAction`, `Quarantine`, `Redirect` |
| Enabled | Write | Boolean | Specify if this policy should be enabled. Default is $true. | - |
| EnableFirstContactSafetyTips | Write | Boolean | The EnableFirstContactSafetyTips parameter specifies whether to enable or disable the safety tip that's shown when recipients first receive an email from a sender or do not often receive email from a sender. | - |
| EnableMailboxIntelligence | Write | Boolean | The EnableMailboxIntelligence parameter specifies whether to enable or disable mailbox intelligence \(the first contact graph\) in domain and user impersonation protection. | - |
| EnableMailboxIntelligenceProtection | Write | Boolean | The EnableMailboxIntelligenceProtection specifies whether to enable or disable enhanced impersonation results based on each user's individual sender map. This intelligence allows Microsoft 365 to customize user impersonation detection and better handle false positives. | - |
| EnableOrganizationDomainsProtection | Write | Boolean | Theâ¯EnableOrganizationDomainsProtection parameter specifies whether to enable domain impersonation protection for all registered domains in the Office 365 organization. | - |
| EnableSimilarDomainsSafetyTips | Write | Boolean | Theâ¯EnableSimilarDomainsSafetyTipsâ¯parameter specifies whether to enable safety tips that are shown to recipients in messages for domain impersonation detections. | - |
| EnableSimilarUsersSafetyTips | Write | Boolean | Theâ¯EnableSimilarUsersSafetyTipsâ¯parameter specifies whether to enable safety tips that are shown to recipients in messages for user impersonation detections. | - |
| EnableSpoofIntelligence | Write | Boolean | The EnableSpoofIntelligence parameter specifies whether to enable or disable antispoofing protection for the policy. | - |
| EnableTargetedDomainsProtection | Write | Boolean | Theâ¯EnableTargetedDomainsProtection parameter specifies whether to enable domain impersonation protection for a list of specified domains. | - |
| EnableTargetedUserProtection | Write | Boolean | Theâ¯EnableTargetedUserProtection parameter specifies whether to enable user impersonation protection for the users specified by the TargetedUsersToProtect parameter | - |
| EnableUnauthenticatedSender | Write | Boolean | Theâ¯EnableUnauthenticatedSenderâ¯parameter enables or disables unauthenticated sender identification in Outlook. | - |
| EnableUnusualCharactersSafetyTips | Write | Boolean | Theâ¯EnableUnusualCharactersSafetyTipsâ¯parameter specifies whether to enable safety tips that are shown to recipients in messages for unusual characters in domain and user impersonation detections. | - |
| EnableViaTag | Write | Boolean | This setting is part of spoof protection. Theâ¯EnableViaTagâ¯parameter enables or disables adding the via tag to the From address in Outlook. | - |
| MakeDefault | Write | Boolean | Make this the default antiphishing policy | - |
| ExcludedDomains | Write | StringArray\[\] | Theâ¯ExcludedDomainsâ¯parameter specifies trusted domains that are excluded from scanning by antiphishing protection. You can specify multiple domains separated by commas. | - |
| ExcludedSenders | Write | StringArray\[\] | Theâ¯ExcludedSendersâ¯parameter specifies a list of trusted sender email addresses that are excluded from scanning by antiphishing protection. You can specify multiple email addresses separated by commas. | - |
| HonorDmarcPolicy | Write | Boolean | The HonorDmarcPolicy enables or disables using the sender's DMARC policy to determine what to do to messages that fail DMARC checks. | - |
| ImpersonationProtectionState | Write | String | The ImpersonationProtectionState parameter specifies the configuration of impersonation protection. | - |
| MailboxIntelligenceProtectionAction | Write | String | The MailboxIntelligenceProtectionAction parameter specifies what to do with messages that fail mailbox intelligence protection. | - |
| MailboxIntelligenceProtectionActionRecipients | Write | StringArray\[\] | Theâ¯MailboxIntelligenceProtectionActionRecipients parameter specifies the recipients to add to detected messages when the MailboxIntelligenceProtectionAction parameter is set to the valueâ¯Redirect or BccMessage. | - |
| MailboxIntelligenceQuarantineTag | Write | String | The MailboxIntelligenceQuarantineTag specifies the quarantine policy that's used on messages that are quarantined by mailbox intelligence. | - |
| SpoofQuarantineTag | Write | String | The SpoofQuarantineTag specifies the quarantine policy that's used on messages that are quarantined by spoof intelligence. | - |
| TargetedDomainActionRecipients | Write | StringArray\[\] | Theâ¯TargetedDomainActionRecipients parameter specifies the recipients to add to detected domain impersonation messages when the TargetedDomainProtectionAction parameter is set to the valueâ¯Redirect or BccMessage. A valid value for this parameter is an email address. You can specify multiple email addresses separated by commas. | - |
| TargetedDomainProtectionAction | Write | String | The TargetedDomainProtectionAction parameter specifies the action to take on detected domain impersonation messages. | `BccMessage`, `Delete`, `MoveToJmf`, `NoAction`, `Quarantine`, `Redirect` |
| TargetedDomainsToProtect | Write | StringArray\[\] | The TargetedDomainsToProtect parameter specifies the domains that are included in domain impersonation protection when the EnableTargetedDomainsProtection parameter is set to $true. | - |
| TargetedDomainQuarantineTag | Write | String | The TargetedDomainQuarantineTag specifies the quarantine policy that's used on messages that are quarantined by domain impersonation protection. | - |
| TargetedUserActionRecipients | Write | StringArray\[\] | Theâ¯TargetedUserActionRecipients parameter specifies the replacement or additional recipients for detected user impersonation messages when the TargetedUserProtectionAction parameter is set to the valueâ¯Redirect or BccMessage. A valid value for this parameter is an email address. You can specify multiple email addresses separated by commas. | - |
| TargetedUsersToProtect | Write | StringArray\[\] | The TargetedUsersToProtect parameter specifies the users that are included in user impersonation protection when the EnableTargetedUserProtection parameter is set to $true. | - |
| TargetedUserQuarantineTag | Write | String | The TargetedUserQuarantineTag specifies the quarantine policy that's used on messages that are quarantined by user impersonation protection. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## antiPhishRule resource type

### Description

This resource configures an [Anti-Phish Rule in Exchange Online](https://learn.microsoft.com/en-us/powershell/module/exchange/advanced-threat-protection/new-antiphishRule?view=exchange-ps).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the antiphishing rule that you want to modify. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |
| AntiPhishPolicy | Required | String | The AntiPhishPolicy parameter specifies the name of the antiphishing policy that's associated with the antiphishing rule. | - |
| Enabled | Write | Boolean | Specify if this rule should be enabled. Default is $true. | - |
| Priority | Write | UInt32 | The Priority parameter specifies a priority value for the rule that determines the order of rule processing. A lower integer value indicates a higher priority, the value 0 is the highest priority, and rules can't have the same priority value. | - |
| Comments | Write | String | The Comments parameter specifies informative comments for the rule, such as what the rule is used for or how it has changed over time. The length of the comment can't exceed 1,024 characters. | - |
| ExceptIfRecipientDomainIs | Write | StringArray\[\] | The ExceptIfRecipientDomainIs parameter specifies an exception that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| ExceptIfSentTo | Write | StringArray\[\] | The ExceptIfSentTo parameter specifies an exception that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| ExceptIfSentToMemberOf | Write | StringArray\[\] | The ExceptIfSentToMemberOf parameter specifies an exception that looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |
| RecipientDomainIs | Write | StringArray\[\] | The RecipientDomainIs parameter specifies a condition that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| SentTo | Write | StringArray\[\] | The SentTo parameter specifies a condition that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| SentToMemberOf | Write | StringArray\[\] | The SentToMemberOf parameter looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## applicationAccessPolicy resource type

### Description

This resource configures Applications Access Policies in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the application access policy that you want to modify. | - |
| AccessRight | Write | String | The AccessRight parameter specifies the permission that you want to assign in the application access policy. | `RestrictAccess`, `DenyAccess` |
| AppID | Write | StringArray\[\] | The AppID parameter specifies the GUID of the apps to include in the policy. | - |
| PolicyScopeGroupId | Write | String | The PolicyScopeGroupID parameter specifies the recipient to define in the policy. You can use any value that uniquely identifies the recipient. | - |
| Description | Write | String | The Description parameter specifies a description for the policy. | - |
| Ensure | Write | String | Specify if the Application Access Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- View-Only Configuration, Organization Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## atpPolicyForO365 resource type

### Description

This resource configures the Advanced Threat Protection \(ATP\) policy in Office 365. Tenant must be subscribed to ATP.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Specifies that the resource is a single instance, the value must be 'Yes' | `Yes` |
| Identity | Write | String | The Identity parameter specifies the Advanced Threat Protection \(ATP\) policy that you want to modify. There's only one policy named Default. | - |
| Ensure | Write | String | Since there's only one policy, the default policy, this value must be set to 'Present' | `Present` |
| AllowSafeDocsOpen | Write | Boolean | The AllowSafeDocsOpen parameter specifies whether users can click through and bypass the Protected View container even when Safe Documents identify a file as malicious. | - |
| EnableATPForSPOTeamsODB | Write | Boolean | The EnableATPForSPOTeamsODB parameter specifies whether ATP is enabled for SharePoint Online, OneDrive for Business and Microsoft Teams. The default value is $false. | - |
| EnableSafeDocs | Write | Boolean | The EnableSafeDocs parameter specifies whether to enable the Safe Documents feature in the organization. The default value is $false. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## authenticationPolicy resource type

### Description

This resource configures Authentication Policies in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the authentication policy you want to view or modify. | - |
| AllowBasicAuthActiveSync | Write | Boolean | The AllowBasicAuthActiveSync switch specifies whether to allow Basic authentication with Exchange Active Sync. | - |
| AllowBasicAuthAutodiscover | Write | Boolean | The AllowBasicAuthAutodiscover switch specifies whether to allow Basic authentication with Autodiscover. | - |
| AllowBasicAuthImap | Write | Boolean | The AllowBasicAuthImap switch specifies whether to allow Basic authentication with IMAP. | - |
| AllowBasicAuthMapi | Write | Boolean | The AllowBasicAuthMapi switch specifies whether to allow Basic authentication with MAPI. | - |
| AllowBasicAuthOfflineAddressBook | Write | Boolean | The AllowBasicAuthOfflineAddressBook switch specifies whether to allow Basic authentication with Offline Address Books. | - |
| AllowBasicAuthOutlookService | Write | Boolean | The AllowBasicAuthOutlookService switch specifies whether to allow Basic authentication with the Outlook service. | - |
| AllowBasicAuthPop | Write | Boolean | The AllowBasicAuthPop switch specifies whether to allow Basic authentication with POP. | - |
| AllowBasicAuthPowershell | Write | Boolean | The AllowBasicAuthPowerShell switch specifies whether to allow Basic authentication with PowerShell. | - |
| AllowBasicAuthReportingWebServices | Write | Boolean | The AllowBasicAuthReporting Web Services switch specifies whether to allow Basic authentication with reporting web services. | - |
| AllowBasicAuthRpc | Write | Boolean | The AllowBasicAuthRpc switch specifies whether to allow Basic authentication with RPC. | - |
| AllowBasicAuthSmtp | Write | Boolean | The AllowBasicAuthSmtp switch specifies whether to allow Basic authentication with SMTP. | - |
| AllowBasicAuthWebServices | Write | Boolean | The AllowBasicAuthWebServices switch specifies whether to allow Basic authentication with Exchange Web Services \(EWS\). | - |
| Ensure | Write | String | Specify if the authentication Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- View-Only Configuration, Organization Configuration, Recipient Policies

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## authenticationPolicyAssignment resource type

### Description

This resource assigns Exchange Online Authentication Policies to users.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| UserName | Key | String | Name of the user assigned to the authentication policy. | - |
| AuthenticationPolicyName | Write | String | Name of the authentication policy. | - |
| Ensure | Write | String | Specify if the authentication Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- View-Only Configuration, Organization Configuration, Recipient Policies

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## availabilityAddressSpace resource type

### Description

Create a new AvailabilityAddressSpace in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the AvailabilityAddressSpace you want to modify. | - |
| AccessMethod | Write | String | The AccessMethod parameter specifies how the free/busy data is accessed. Valid values are:PerUserFB, OrgWideFB, OrgWideFBToken, OrgWideFBBasic,InternalProxy | `PerUserFB`, `OrgWideFB`, `OrgWideFBToken`, `OrgWideFBBasic`, `InternalProxy` |
| Credentials | Write | String | The Credentials parameter specifies the username and password that's used to access the Availability services in the target forest. | - |
| ForestName | Write | String | The ForestName parameter specifies the SMTP domain name of the target forest for users whose free/busy data must be retrieved. If your users are distributed among multiple SMTP domains in the target forest, run the Add-AvailabilityAddressSpace command once for each SMTP domain. | - |
| TargetAutodiscoverEpr | Write | String | The TargetAutodiscoverEpr parameter specifies the Autodiscover URL of Exchange Web Services for the external organization. Exchange uses Autodiscover to automatically detect the correct server endpoint for external requests. | - |
| TargetServiceEpr | Write | String | The TargetServiceEpr parameter specifies the Exchange Online Calendar Service URL of the external Microsoft 365 organization that you're trying to read free/busy information from. | - |
| TargetTenantId | Write | String | The TargetTenantID parameter specifies the tenant ID of the external Microsoft 365 organization that you're trying to read free/busy information from. | - |
| Ensure | Write | String | Specifies if this AvailabilityAddressSpace should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Federated Sharing, Mail Tips, Message Tracking

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## availabilityConfig resource type

### Description

This resource configures the Availability Config in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| OrgWideAccount | Key | String | Specify the OrgWideAccount for the AvailabilityConfig. | - |
| Ensure | Write | String | Specify if the AvailabilityConfig should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Federated Sharing, Organization Configuration, Mail Tips, Message Tracking

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## calendarProcessing resource type

### Description

This resource configures the Calendar Processing settings Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the resource mailbox that you want to view. You can use any value that uniquely identifies the mailbox. | - |
| AddAdditionalResponse | Write | Boolean | The AddAdditionalResponse parameter specifies whether additional information \(the value of the AdditionalResponse parameter\) is added to meeting request responses | - |
| AdditionalResponse | Write | String | The AdditionalResponse parameter specifies the additional information to be included in responses to meeting requests when the value of the AddAdditionalResponse parameter is $true. If the value contains spaces, enclose the value in quotation marks. | - |
| AddNewRequestsTentatively | Write | Boolean | The AddNewRequestsTentatively parameter specifies whether new meeting requests are added to the calendar as tentative | - |
| AddOrganizerToSubject | Write | Boolean | The AddOrganizerToSubject parameter specifies whether the meeting organizer's name is used as the subject of the meeting request. | - |
| AllBookInPolicy | Write | Boolean | The AllBookInPolicy parameter specifies whether to automatically approve in-policy requests from all users to the resource mailbox. | - |
| AllowConflicts | Write | Boolean | The AllowConflicts parameter specifies whether to allow conflicting meeting requests. | - |
| AllowRecurringMeetings | Write | Boolean | The AllowRecurringMeetings parameter specifies whether to allow recurring meetings in meeting requests. | - |
| AllRequestInPolicy | Write | Boolean | The AllRequestInPolicy parameter specifies whether to allow all users to submit in-policy requests to the resource mailbox. | - |
| AllRequestOutOfPolicy | Write | Boolean | The AllRequestOutOfPolicy parameter specifies whether to allow all users to submit out-of-policy requests to the resource mailbox. | - |
| AutomateProcessing | Write | String | The AutomateProcessing parameter enables or disables calendar processing on the mailbox. | `None`, `AutoUpdate`, `AutoAccept` |
| BookingType | Write | String | The BookingType parameter specifies how reservations work on the resource mailbox. | `Standard`, `Reserved` |
| BookingWindowInDays | Write | UInt32 | The BookingWindowInDays parameter specifies the maximum number of days in advance that the resource can be reserved. A valid value is an integer from 0 through 1080. The default value is 180 days. The value 0 means today. | - |
| BookInPolicy | Write | StringArray\[\] | The BookInPolicy parameter specifies users or groups who are allowed to submit in-policy meeting requests to the resource mailbox that are automatically approved. You can use any value that uniquely identifies the user or group. | - |
| ConflictPercentageAllowed | Write | UInt32 | The ConflictPercentageAllowed parameter specifies the maximum percentage of meeting conflicts for new recurring meeting requests. A valid value is an integer from 0 through 100. The default value is 0. | - |
| DeleteAttachments | Write | Boolean | The DeleteAttachments parameter specifies whether to remove attachments from all incoming messages. | - |
| DeleteComments | Write | Boolean | The DeleteComments parameter specifies whether to remove or keep any text in the message body of incoming meeting requests. | - |
| DeleteNonCalendarItems | Write | Boolean | The DeleteNonCalendarItems parameter specifies whether to remove or keep all non-calendar-related messages that are received by the resource mailbox. | - |
| DeleteSubject | Write | Boolean | The DeleteSubject parameter specifies whether to remove or keep the subject of incoming meeting requests. | - |
| EnableAutoRelease | Write | Boolean | N/A | - |
| EnableResponseDetails | Write | Boolean | The EnableResponseDetails parameter specifies whether to include the reasons for accepting or declining a meeting in the response email message. | - |
| EnforceCapacity | Write | Boolean | The EnforceCapacity parameter specifies whether to restrict the number of attendees to the capacity of the workspace. For example, if capacity is set to 10, then only 10 people can book the workspace. | - |
| EnforceSchedulingHorizon | Write | Boolean | The EnforceSchedulingHorizon parameter controls the behavior of recurring meetings that extend beyond the date specified by the BookingWindowInDays parameter. | - |
| ForwardRequestsToDelegates | Write | Boolean | The ForwardRequestsToDelegates parameter specifies whether to forward incoming meeting requests to the delegates that are configured for the resource mailbox. | - |
| MaximumConflictInstances | Write | UInt32 | The MaximumConflictInstances parameter specifies the maximum number of conflicts for new recurring meeting requests when the AllowRecurringMeetings parameter is set to $true. A valid value is an integer from 0 through INT32 \(2147483647\). The default value is 0. | - |
| MaximumDurationInMinutes | Write | UInt32 | The MaximumDurationInMinutes parameter specifies the maximum duration in minutes for meeting requests. A valid value is an integer from 0 through INT32 \(2147483647\). The default value is 1440 \(24 hours\). | - |
| MinimumDurationInMinutes | Write | UInt32 | The MinimumDurationInMinutes parameter specifies the minimum duration in minutes for meeting requests in workspace mailboxes. A valid value is an integer from 0 through INT32 \(2147483647\). The default value is 0, which means there's no minimum duration. | - |
| OrganizerInfo | Write | Boolean | The OrganizerInfo parameter specifies whether the resource mailbox sends organizer information when a meeting request is declined because of conflicts. | - |
| PostReservationMaxClaimTimeInMinutes | Write | UInt32 | N/A | - |
| ProcessExternalMeetingMessages | Write | Boolean | The ProcessExternalMeetingMessages parameter specifies whether to process meeting requests that originate outside the Exchange organization. | - |
| RemoveCanceledMeetings | Write | Boolean | The RemoveCanceledMeetings parameter specifies whether to automatically delete meetings that were cancelled by the organizer from the resource mailbox's calendar. | - |
| RemoveForwardedMeetingNotifications | Write | Boolean | The RemoveForwardedMeetingNotifications parameter specifies whether forwarded meeting notifications are moved to the Deleted Items folder after they're processed by the Calendar Attendant. | - |
| RemoveOldMeetingMessages | Write | Boolean | The RemoveOldMeetingMessages parameter specifies whether the Calendar Attendant removes old and redundant updates and responses. | - |
| RemovePrivateProperty | Write | Boolean | The RemovePrivateProperty parameter specifies whether to clear the private flag for incoming meetings that were sent by the organizer in the original requests. | - |
| RequestInPolicy | Write | StringArray\[\] | The RemovePrivateProperty parameter specifies whether to clear the private flag for incoming meetings that were sent by the organizer in the original requests. | - |
| RequestOutOfPolicy | Write | StringArray\[\] | The RequestOutOfPolicy parameter specifies users who are allowed to submit out-of-policy requests that require approval by a resource mailbox delegate. You can use any value that uniquely identifies the user. | - |
| ResourceDelegates | Write | StringArray\[\] | The ResourceDelegates parameter specifies users can approve or reject requests that are sent to the resource mailbox. You can use any value that uniquely identifies the user. | - |
| ScheduleOnlyDuringWorkHours | Write | Boolean | The ScheduleOnlyDuringWorkHours parameter specifies whether to allow meetings to be scheduled outside of the working hours that are defined for the resource mailbox. | - |
| TentativePendingApproval | Write | Boolean | The TentativePendingApproval parameter specifies whether to mark pending requests as tentative on the calendar. | - |
| Ensure | Write | String | Determines wether or not the instance exist. | `Present` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Organization Management, Recipient Management

##### Role Groups

- Organization Management, Help Desk

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## casMailboxPlan resource type

### Description

This resource configures Client Access services \(CAS\) mailbox plans in cloud-based organizations.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the CAS Mailbox Plan that you want to modify. | - |
| DisplayName | Write | String | The display name of the CAS Mailbox Plan. | - |
| Ensure | Write | String | CASMailboxPlans can't be created or removed in O365 and must be set to 'Present'. | `Present` |
| ActiveSyncEnabled | Write | Boolean | The ActiveSyncEnabled parameter enables or disables access to the mailbox by using Exchange Active Sync. Default is $true. | - |
| ImapEnabled | Write | Boolean | The ImapEnabled parameter enables or disables access to the mailbox by using IMAP4 clients. The default value is $true for all CAS mailbox plans except ExchangeOnlineDeskless which is $false by default. | - |
| OwaMailboxPolicy | Write | String | The OwaMailboxPolicy parameter specifies the Outlook on the web \(formerly known as Outlook Web App\) mailbox policy for the mailbox plan. The default value is OwaMailboxPolicy-Default. You can use the Get-OwaMailboxPolicy cmdlet to view the available Outlook on the web mailbox policies. | - |
| PopEnabled | Write | Boolean | The PopEnabled parameter enables or disables access to the mailbox by using POP3 clients. Default is $true. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Organization Client Access, View-Only Recipients, View-Only Configuration, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## casMailboxSettings resource type

### Description

This resource configures CAS mailbox settings.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the mailbox that you want to configure. | - |
| ActiveSyncAllowedDeviceIDs | Write | StringArray\[\] | TheActiveSyncAllowedDeviceIDs parameter specifies one or more Exchange ActiveSync device IDs that are allowed to synchronize with the mailbox. | - |
| ActiveSyncBlockedDeviceIDs | Write | StringArray\[\] | The ActiveSyncBlockedDeviceIDs parameter specifies one or more Exchange ActiveSync device IDs that aren't allowed to synchronize with the mailbox. | - |
| ActiveSyncDebugLogging | Write | Boolean | The ActiveSyncDebugLogging parameter enables or disables Exchange ActiveSync debug logging for the mailbox. | - |
| ActiveSyncEnabled | Write | Boolean | The ActiveSyncEnabled parameter enables or disables access to the mailbox using Exchange ActiveSync. | - |
| ActiveSyncMailboxPolicy | Write | String | The ActiveSyncMailboxPolicy parameter specifies the Exchange ActiveSync mailbox policy for the mailbox. | - |
| ActiveSyncSuppressReadReceipt | Write | Boolean | The ActiveSyncSuppressReadReceipt parameter controls the behavior of read receipts for Exchange ActiveSync clients that access the mailbox. | - |
| EwsAllowEntourage | Write | Boolean | The EwsAllowEntourage parameter enables or disables access to the mailbox by Microsoft Entourage clients that use Exchange Web Services. | - |
| EwsAllowList | Write | StringArray\[\] | The EwsAllowList parameter specifies the Exchange Web Services applications \(user agent strings\) that are allowed to access the mailbox. | - |
| EwsAllowMacOutlook | Write | Boolean | The EwsAllowMacOutlook parameter enables or disables access to the mailbox by Outlook for Mac clients that use Exchange Web Services. | - |
| EwsAllowOutlook | Write | Boolean | The EwsAllowOutlook parameter enables or disables access to the mailbox by Outlook clients that use Exchange Web Services. | - |
| EwsApplicationAccessPolicy | Write | String | The EwsApplicationAccessPolicy parameter controls access to the mailbox using Exchange Web Services applications. | - |
| EwsBlockList | Write | StringArray\[\] | The EwsBlockList parameter specifies the Exchange Web Services applications \(user agent strings\) that aren't allowed to access the mailbox using Exchange Web Services. | - |
| EwsEnabled | Write | Boolean | The EwsEnabled parameter enables or disables access to the mailbox using Exchange Web Services clients. | - |
| ImapEnabled | Write | Boolean | The ImapEnabled parameter enables or disables access to the mailbox using IMAP4 clients. | - |
| ImapMessagesRetrievalMimeFormat | Write | String | The ImapMessagesRetrievalMimeFormat parameter specifies the message format for IMAP4 clients that access the mailbox. | - |
| ImapForceICalForCalendarRetrievalOption | Write | Boolean | The ImapForceICalForCalendarRetrievalOption parameter specifies how meeting requests are presented to IMAP4 clients that access the mailbox. | - |
| ImapSuppressReadReceipt | Write | Boolean | The ImapSuppressReadReceipt parameter controls the behavior of read receipts for IMAP4 clients that access the mailbox. | - |
| ImapUseProtocolDefaults | Write | Boolean | The ImapUseProtocolDefaults parameter specifies whether to use the IMAP4 protocol defaults for the mailbox. | - |
| MacOutlookEnabled | Write | Boolean | The MacOutlookEnabled parameter enables or disables access to the mailbox using Outlook for Mac clients that use Microsoft Sync technology. | - |
| MAPIEnabled | Write | Boolean | The MAPIEnabled parameter enables or disables access to the mailbox using MAPI clients \(for example, Outlook\). | - |
| OneWinNativeOutlookEnabled | Write | Boolean | The OneWinNativeOutlookEnabled parameter enables or disables access to the mailbox using the new Outlook for Windows. | - |
| OutlookMobileEnabled | Write | Boolean | The OutlookMobileEnabled parameter enables or disables access to the mailbox using Outlook for iOS and Android. | - |
| OWAEnabled | Write | Boolean | The OWAEnabled parameter enables or disables access to the mailbox using Outlook on the web \(formerly known as Outlook Web App or OWA\). | - |
| OWAforDevicesEnabled | Write | Boolean | The OWAforDevicesEnabled parameter enables or disables access to the mailbox using the older Outlook Web App \(OWA\) app on iOS and Android devices. | - |
| OwaMailboxPolicy | Write | String | The OwaMailboxPolicy parameter specifies the Outlook on the web mailbox policy for the mailbox. | - |
| PopEnabled | Write | Boolean | The PopEnabled parameter enables or disables access to the mailbox using POP3 clients. | - |
| PopForceICalForCalendarRetrievalOption | Write | Boolean | The PopForceICalForCalendarRetrievalOption parameter specifies how meeting requests are presented to POP3 clients that access the mailbox. | - |
| PopMessagesRetrievalMimeFormat | Write | String | The PopMessagesRetrievalMimeFormat parameter specifies the message format for POP3 clients that access the mailbox. | - |
| PopSuppressReadReceipt | Write | Boolean | The PopSuppressReadReceipt parameter controls the behavior of read receipts for POP3 clients that access the mailbox. | - |
| PopUseProtocolDefaults | Write | Boolean | The PopUseProtocolDefaults parameter specifies whether to use the POP3 protocol defaults for the mailbox. | - |
| PublicFolderClientAccess | Write | Boolean | The PublicFolderClientAccess parameter enables or disables access to public folders in Microsoft Outlook. | - |
| ShowGalAsDefaultView | Write | Boolean | The ShowGalAsDefaultView parameter specifies whether the global address list \(GAL\) is the default recipient picker for messages. | - |
| SmtpClientAuthenticationDisabled | Write | Boolean | The SmtpClientAuthenticationDisabled parameter specifies whether to disable authenticated SMTP \(SMTP AUTH\) for the mailbox. | - |
| UniversalOutlookEnabled | Write | Boolean | The UniversalOutlookEnabled parameter enables or disables access to the mailbox using Windows 10 Mail and Calendar. | - |
| Ensure | Write | String | Present ensures the Mailbox CAS settings are applied. | `Present` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- User Options, View-Only Recipients, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## dataClassification resource type

### Description

Create a new data classification policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the data classification rule that you want to modify. | - |
| Description | Write | String | The Description parameter specifies a description for the data classification rule. You use the Description parameter with the Locale and Name parameters to specify descriptions for the data classification rule in different languages. | - |
| Fingerprints | Write | StringArray\[\] | The Fingerprints parameter specifies the byte-encoded document files that are used as fingerprints by the data classification rule. | - |
| IsDefault | Write | Boolean | IsDefault is used with the Locale parameter to specify the default language for the data classification rule. | - |
| Locale | Write | String | The Locale parameter adds or removes languages that are associated with the data classification rule. | - |
| Name | Write | String | The Name parameter specifies a name for the data classification rule. The value must be less than 256 characters. | - |
| Ensure | Write | String | Specifies if this policy should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Data Loss Prevention, View-Only Configuration

##### Role Groups

- Organization Management, Compliance Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## dataEncryptionPolicy resource type

### Description

Create a new Data Encryption policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the data encryption policy that you want to modify. | - |
| AzureKeyIDs | Write | StringArray\[\] | The AzureKeyIDs parameter specifies the URI values of the Azure Key Vault keys to associate with the data encryption policy. | - |
| Description | Write | String | The Description parameter specifies an optional description for the data encryption policy | - |
| Enabled | Write | Boolean | The Enabled parameter enables or disable the data encryption policy. | - |
| Name | Write | String | The Name parameter specifies the unique name for the data encryption policy. | - |
| PermanentDataPurgeContact | Write | String | The PermanentDataPurgeContact parameter specifies a contact for the purge of all data that's encrypted by the data encryption policy. | - |
| PermanentDataPurgeReason | Write | String | The PermanentDataPurgeReason parameter specifies a descriptive reason for the purge of all data that's encrypted by the data encryption policy | - |
| Ensure | Write | String | Specifies if this policy should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Recipient Policies, Mail Recipient Creation, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## distributionGroup resource type

### Description

This resource configures Exchange Online distribution groups.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the distribution group or mail-enabled security group that you want to modify. You can use any value that uniquely identifies the group. | - |
| Name | Required | String | The Name parameter specifies a unique name for the address list. | - |
| Alias | Write | String | Exchange alias \(also known as the mail nickname\) for the recipient | - |
| BccBlocked | Write | Boolean | Is Bcc blocked for the distribution group. | - |
| BypassNestedModerationEnabled | Write | Boolean | The ByPassNestedModerationEnabled parameter specifies how to handle message approval when a moderated group contains other moderated groups as members. | - |
| Description | Write | String | Description of the distribution group. | - |
| DisplayName | Write | String | The DisplayName parameter specifies the display name of the group. The display name is visible in the Exchange admin center and in address lists. The maximum length is 256 characters. | - |
| HiddenGroupMembershipEnabled | Write | Boolean | The HiddenGroupMembershipEnabled switch specifies whether to hide the members of the distribution group from members of the group and users who aren't members of the group. | - |
| ManagedBy | Write | StringArray\[\] | The ManagedBy parameter specifies an owner for the group. A group must have at least one owner. | - |
| MemberDepartRestriction | Write | String | The MemberDepartRestriction parameter specifies the restrictions that you put on requests to leave the group. Valid values are: Open & Closed | `Open`, `Closed` |
| MemberJoinRestriction | Write | String | The MemberJoinRestriction parameter specifies the restrictions that you put on requests to join the group. Valid values are: Open, Closed & ApprovalRequired | `Open`, `Closed`, `ApprovalRequired` |
| Members | Write | StringArray\[\] | The Members parameter specifies the recipients \(mail-enabled objects\) that are members of the group. You can use any value that uniquely identifies the recipient. | - |
| ModeratedBy | Write | StringArray\[\] | The ModeratedBy parameter specifies one or more moderators for this group. A moderator approves messages sent to the group before the messages are delivered. A moderator must be a mailbox, mail user, or mail contact in your organization. You can use any value that uniquely identifies the moderator. | - |
| ModerationEnabled | Write | Boolean | The ModerationEnabled parameter specifies whether moderation is enabled for this recipient. | - |
| Notes | Write | String | The Notes parameters specifies additional information about the object. | - |
| OrganizationalUnit | Write | String | The OrganizationalUnit parameter specifies the location in Active Directory where the group is created. | - |
| PrimarySmtpAddress | Write | String | The PrimarySmtpAddress parameter specifies the primary return email address that's used for the recipient. | - |
| RequireSenderAuthenticationEnabled | Write | Boolean | The RequireSenderAuthenticationEnabled parameter specifies whether to accept messages only from authenticated \(internal\) senders. | - |
| RoomList | Write | Boolean | The RoomList switch specifies that all members of this distribution group are room mailboxes. You don't need to specify a value with this switch. | - |
| AcceptMessagesOnlyFrom | Write | StringArray\[\] | The AcceptMessagesOnlyFrom parameter specifies who is allowed to send messages to this recipient. Messages from other senders are rejected. | - |
| AcceptMessagesOnlyFromDLMembers | Write | StringArray\[\] | The AcceptMessagesOnlyFromDLMembers parameter specifies who is allowed to send messages to this recipient. Messages from other senders are rejected. | - |
| AcceptMessagesOnlyFromSendersOrMembers | Write | StringArray\[\] | The AcceptMessagesOnlyFromSendersOrMembers parameter specifies who is allowed to send messages to this recipient. Messages from other senders are rejected. | - |
| CustomAttribute1 | Write | String | This parameter specifies a value for the CustomAttribute1 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute2 | Write | String | This parameter specifies a value for the CustomAttribute2 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute3 | Write | String | This parameter specifies a value for the CustomAttribute3 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute4 | Write | String | This parameter specifies a value for the CustomAttribute4 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute5 | Write | String | This parameter specifies a value for the CustomAttribute5 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute6 | Write | String | This parameter specifies a value for the CustomAttribute6 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute7 | Write | String | This parameter specifies a value for the CustomAttribute7 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute8 | Write | String | This parameter specifies a value for the CustomAttribute8 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute9 | Write | String | This parameter specifies a value for the CustomAttribute9 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute10 | Write | String | This parameter specifies a value for the CustomAttribute10 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute11 | Write | String | This parameter specifies a value for the CustomAttribute11 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute12 | Write | String | This parameter specifies a value for the CustomAttribute12 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute13 | Write | String | This parameter specifies a value for the CustomAttribute13 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute14 | Write | String | This parameter specifies a value for the CustomAttribute14 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomAttribute15 | Write | String | This parameter specifies a value for the CustomAttribute15 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| EmailAddresses | Write | StringArray\[\] | The EmailAddresses parameter specifies all email addresses \(proxy addresses\) for the recipient, including the primary SMTP address. In on-premises Exchange organizations, the primary SMTP address and other proxy addresses are typically set by email address policies. However, you can use this parameter to configure other proxy addresses for the recipient. | - |
| GrantSendOnBehalfTo | Write | StringArray\[\] | The GrantSendOnBehalfTo parameter specifies who can send on behalf of this group. Although messages send on behalf of the group clearly show the sender in the From field \(<Sender> on behalf of <Group>\), replies to these messages are delivered to the group, not the sender. | - |
| HiddenFromAddressListsEnabled | Write | Boolean | The HiddenFromAddressListsEnabled parameter specifies whether this recipient is visible in address lists. | - |
| SendOofMessageToOriginatorEnabled | Write | Boolean | The SendOofMessageToOriginatorEnabled parameter specifies how to handle out of office \(OOF\) messages for members of the group. | - |
| SendModerationNotifications | Write | String | The SendModerationNotifications parameter specifies when moderation notification messages are sent. Valid values are: Always, Internal, Never. | `Always`, `Internal`, `Never` |
| Type | Write | String | The Type parameter specifies the type of group that you want to create. Valid values are: Distribution, Security | `Distribution`, `Security` |
| Ensure | Write | String | Specifies if this AddressList should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Organization Management, Recipient Management

##### Role Groups

- None

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## dkimSigningConfig resource type

### Description

This resource configures the DomainKeys Identified Mail \(DKIM\) signing policy settings for domains in a cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the DKIM signing policy that you want to modify. This should be the FQDN. | - |
| AdminDisplayName | Write | String | The AdminDisplayName parameter specifies a description for the policy. | - |
| BodyCanonicalization | Write | String | The BodyCanonicalization parameter specifies the canonicalization algorithm that's used to create and verify the message body part of the DKIM signature. This value effectively controls the sensitivity of DKIM to changes to the message body in transit. Valid values are 'Simple' or 'Relaxed'. 'Relaxed' is the default. | `Simple`, `Relaxed` |
| HeaderCanonicalization | Write | String | The HeaderCanonicalization parameter specifies the canonicalization algorithm that's used to create and verify the message header part of the DKIM signature. This value effectively controls the sensitivity of DKIM to changes to the message headers in transit. Valid values are 'Simple' or 'Relaxed'. 'Relaxed' is the default. | `Simple`, `Relaxed` |
| KeySize | Write | UInt16 | The KeySize parameter specifies the size in bits of the public key that's used in the DKIM signing policy. Valid values are 1024 and 2048 | `1024`, `2048` |
| Enabled | Write | Boolean | The Enabled parameter specifies whether the DKIM Signing Configuration is enabled or disabled. Default is $true. | - |
| Ensure | Write | String | Specifies if this Client Access Rule should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## emailAddressPolicy resource type

### Description

This resource configures Email address policies in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the email address policy. The maximum length is 64 characters. | - |
| Priority | Write | String | The Priority parameter specifies the order that the email address policies are evaluated. By default, every time that you add a new email address policy, the policy is assigned a priority of N+1, where N is the number of email address policies that you've created. | - |
| EnabledEmailAddressTemplates | Write | StringArray\[\] | The EnabledEmailAddressTemplates parameter specifies the rules in the email address policy that are used to generate email addresses for recipients. | - |
| EnabledPrimarySMTPAddressTemplate | Write | StringArray\[\] | The EnabledPrimarySMTPAddressTemplate parameter specifies the specifies the rule in the email address policy that's used to generate the primary SMTP email addresses for recipients. You can use this parameter instead of the EnabledEmailAddressTemplates if the policy only applies the primary email address and no additional proxy addresses. | - |
| ManagedByFilter | Write | String | The ManagedByFilter parameter specifies the email address policies to apply to Office 365 groups based on the properties of the users who create the Office 365 groups. | - |
| Ensure | Write | String | Specify if the Email Address Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- E-Mail Address Policies

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## groupSettings resource type

### Description

This resource configures settings on groups such as the custom attributes and language.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The DisplayName parameter specifies the name of the Microsoft 365 Group. The display name is visible in the Exchange admin center, address lists, and Outlook. The maximum length is 64 characters. | - |
| Id | Write | String | The unique Id of the group | - |
| AcceptMessagesOnlyFromSendersOrMembers | Write | StringArray\[\] | The AcceptMessagesOnlyFromSendersOrMembers parameter specifies who is allowed to send messages to this recipient. Messages from other senders are rejected. | - |
| AccessType | Write | String | Private | `Public`, `Private` |
| AlwaysSubscribeMembersToCalendarEvents | Write | Boolean | The AlwaysSubscribeMembersToCalendarEvents switch controls the default subscription settings of new members that are added to the Microsoft 365 Group. Changing this setting doesn't affect existing group members. | - |
| AuditLogAgeLimit | Write | String | The AlwaysSubscribeMembersToCalendarEvents switch controls the default subscription settings of new members that are added to the Microsoft 365 Group. Changing this setting doesn't affect existing group members. | - |
| AutoSubscribeNewMembers | Write | Boolean | The AutoSubscribeNewMembers switch specifies whether to automatically subscribe new members that are added to the Microsoft 365 Group to conversations and calendar events. Only users that are added to the group after you enable this setting are automatically subscribed to the group. | - |
| CalendarMemberReadOnly | Write | Boolean | The CalendarMemberReadOnly parameter specifies whether to set read-only Calendar permissions to the Microsoft 365 Group for members of the group. | - |
| Classification | Write | String | The CalendarMemberReadOnly switch specifies whether to set read-only Calendar permissions to the Microsoft 365 Group for members of the group. | - |
| ConnectorsEnabled | Write | Boolean | The CalendarMemberReadOnly switch specifies whether to set read-only Calendar permissions to the Microsoft 365 Group for members of the group. | - |
| CustomAttribute1 | Write | String | This parameter specifies a value for the CustomAttribute1 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute2 | Write | String | This parameter specifies a value for the CustomAttribute2 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute3 | Write | String | This parameter specifies a value for the CustomAttribute3 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute4 | Write | String | This parameter specifies a value for the CustomAttribute4 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute5 | Write | String | This parameter specifies a value for the CustomAttribute5 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute6 | Write | String | This parameter specifies a value for the CustomAttribute6 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute7 | Write | String | This parameter specifies a value for the CustomAttribute7 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute8 | Write | String | This parameter specifies a value for the CustomAttribute8 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute9 | Write | String | This parameter specifies a value for the CustomAttribute9 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute10 | Write | String | This parameter specifies a value for the CustomAttribute10 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute11 | Write | String | This parameter specifies a value for the CustomAttribute11 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute12 | Write | String | This parameter specifies a value for the CustomAttribute12 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute13 | Write | String | This parameter specifies a value for the CustomAttribute13 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute14 | Write | String | This parameter specifies a value for the CustomAttribute14 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| CustomAttribute15 | Write | String | This parameter specifies a value for the CustomAttribute15 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. The maximum length is 1,024 characters. | - |
| DataEncryptionPolicy | Write | String | The DataEncryptionPolicy parameter specifies the data encryption policy that's applied to the Microsoft 365 Group. | - |
| EmailAddresses | Write | StringArray\[\] | The EmailAddresses parameter specifies all the email addresses \(proxy addresses\) for the recipient, including the primary SMTP address. | - |
| ExtensionCustomAttribute1 | Write | String | This parameter specifies a value for the ExtensionCustomAttribute1 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. You can specify up to 1300 values separated by commas. | - |
| ExtensionCustomAttribute2 | Write | String | This parameter specifies a value for the ExtensionCustomAttribute2 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. You can specify up to 1300 values separated by commas. | - |
| ExtensionCustomAttribute3 | Write | String | This parameter specifies a value for the ExtensionCustomAttribute3 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. You can specify up to 1300 values separated by commas. | - |
| ExtensionCustomAttribute4 | Write | String | This parameter specifies a value for the ExtensionCustomAttribute4 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. You can specify up to 1300 values separated by commas. | - |
| ExtensionCustomAttribute5 | Write | String | This parameter specifies a value for the ExtensionCustomAttribute5 property on the recipient. You can use this property to store custom information about the recipient, and to identify the recipient in filters. You can specify up to 1300 values separated by commas. | - |
| GrantSendOnBehalfTo | Write | StringArray\[\] | The GrantSendOnBehalfTo parameter specifies who can send on behalf of this Microsoft 365 Group. | - |
| HiddenFromAddressListsEnabled | Write | Boolean | The GrantSendOnBehalfTo parameter specifies who can send on behalf of this Microsoft 365 Group. | - |
| HiddenFromExchangeClientsEnabled | Write | Boolean | The HiddenFromExchangeClientsEnabled switch specifies whether the Microsoft 365 Group is hidden from Outlook clients connected to Microsoft 365. | - |
| InformationBarrierMode | Write | String | The InformationBarrierMode parameter specifies the information barrier mode for the Microsoft 365 Group. | `Explicit`, `Implicit`, `Open`, `OwnerModerated` |
| IsMemberAllowedToEditContent | Write | Boolean | This parameter specifies whether or not members are allow to edit content. | - |
| Language | Write | String | The Language parameter specifies language preference for the Microsoft 365 Group. | - |
| MailboxRegion | Write | String | The MailboxRegion parameter specifies the preferred data location \(PDL\) for the Microsoft 365 Group in multi-geo environments. | - |
| MailTip | Write | String | The MailTip parameter specifies the custom MailTip text for this recipient. The MailTip is shown to senders when they start drafting an email message to this recipient. | - |
| MailTipTranslations | Write | String | The MailTipTranslations parameter specifies additional languages for the custom MailTip text that's defined by the MailTip parameter. | - |
| MaxReceiveSize | Write | String | The MaxReceiveSize parameter specifies the maximum size of an email message that can be sent to this group. Messages that exceed the maximum size are rejected by the group. | - |
| MaxSendSize | Write | String | The MaxSendSize parameter specifies the maximum size of an email message that can be sent by this group. | - |
| ModeratedBy | Write | StringArray\[\] | The ModeratedBy parameter specifies one or more moderators for this recipient. A moderator approves messages sent to the recipient before the messages are delivered. A moderator must be a mailbox, mail user, or mail contact in your organization. You can use any value that uniquely identifies the moderator. | - |
| ModerationEnabled | Write | Boolean | The ModerationEnabled parameter specifies whether moderation is enabled for this recipient. | - |
| Notes | Write | String | The Notes parameter specifies the description of the Microsoft 365 Group. If the value contains spaces, enclose the value in quotation marks. | - |
| PrimarySmtpAddress | Write | String | The PrimarySmtpAddress parameter specifies the primary return email address that's used for the recipient. You can't use the EmailAddresses and PrimarySmtpAddress parameters in the same command. | - |
| RejectMessagesFromSendersOrMembers | Write | StringArray\[\] | The RejectMessagesFromSendersOrMembers parameter specifies who isn't allowed to send messages to this recipient. Messages from these senders are rejected. | - |
| RequireSenderAuthenticationEnabled | Write | Boolean | The RequireSenderAuthenticationEnabled parameter specifies whether to accept messages only from authenticated \(internal\) senders. | - |
| SensitivityLabelId | Write | String | The SensitivityLabelId parameter specifies the GUID value of the sensitivity label that's assigned to the Microsoft 365 Group. | - |
| SubscriptionEnabled | Write | Boolean | The SubscriptionEnabled switch specifies whether the group owners can enable subscription to conversations and calendar events on the groups they own. | - |
| UnifiedGroupWelcomeMessageEnabled | Write | Boolean | The UnifiedGroupWelcomeMessageEnabled switch specifies whether to enable or disable sending system-generated welcome messages to users who are added as members to the Microsoft 365 Group. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- User Options, View-Only Recipients, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## hostedConnectionFilterPolicy resource type

### Description

This resource configures the settings of connection filter policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the Hosted Connection Filter Policy that you want to modify. | - |
| AdminDisplayName | Write | String | The AdminDisplayName parameter specifies a description for the policy. | - |
| EnableSafeList | Write | Boolean | The EnableSafeList parameter enables or disables use of the safe list. The safe list is a dynamic allow list in the Microsoft datacenter that requires no customer configuration. Valid input for this parameter is $true or $false. The default value is $false. | - |
| IPAllowList | Write | StringArray\[\] | The IPAllowList parameter specifies IP addresses from which messages are always allowed. Messages from the IP addresses you specify won't be identified as spam, despite any other spam characteristics of the messages. Valid values for this parameter are: A single IP address, an IP address range, a CIDR IP. | - |
| IPBlockList | Write | StringArray\[\] | The IPBlockList parameter specifies IP addresses from which messages are never allowed. Messages from the IP addresses you specify are blocked without any further spam scanning. Valid values for this parameter are: A single IP address, an IP address range, a CIDR IP. | - |
| MakeDefault | Write | Boolean | The MakeDefault parameter makes the specified policy the default connection filter policy. Default is $false. | - |
| Ensure | Write | String | Specifies if this Hosted Connection Filter Policy should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## hostedContentFilterPolicy resource type

### Description

This resource configures the settings of connection filter policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the Hosted Content Filter Policy that you want to modify. | - |
| AddXHeaderValue | Write | String | The AddXHeaderValue parameter specifies the X-header value to add to spam messages when an action parameter is set to the value AddXHeader. | - |
| AdminDisplayName | Write | String | The AdminDisplayName parameter specifies a description for the policy. | - |
| AllowedSenderDomains | Write | StringArray\[\] | The AllowedSenderDomains parameter specifies trusted domains that aren't processed by the spam filter. | - |
| AllowedSenders | Write | StringArray\[\] | The AllowedSenders parameter specifies a list of trusted senders that aren't processed by the spam filter. | - |
| BlockedSenderDomains | Write | StringArray\[\] | The BlockedSenderDomains parameter specifies domains that are always marked as spam sources. | - |
| BlockedSenders | Write | StringArray\[\] | The BlockedSenders parameter specifies senders that are always marked as spam sources. | - |
| BulkQuarantineTag | Write | String | The BulkQuarantineTag parameter specifies the quarantine policy that's used on messages that are quarantined as bulk email. | - |
| BulkSpamAction | Write | String | The BulkSpamAction parameter specifies the action to take on messages that are classified as bulk email. | `MoveToJmf`, `AddXHeader`, `ModifySubject`, `Redirect`, `Delete`, `Quarantine`, `NoAction` |
| BulkThreshold | Write | UInt32 | The BulkThreshold parameter specifies the Bulk Complaint Level \(BCL\) threshold setting. Valid values are from 1 - 9, where 1 marks most bulk email as spam, and 9 allows the most bulk email to be delivered. The default value is 7. | - |
| DownloadLink | Write | Boolean | The DownloadLink parameter shows or hides a link in end-user spam notification messages to download the Junk Email Reporting Tool plugin for Outlook. Valid input for this parameter is $true or $false. The default value is $false. | - |
| EnableEndUserSpamNotifications | Write | Boolean | The EnableEndUserSpamNotification parameter enables for disables sending end-user spam quarantine notification messages. Valid input for this parameter is $true or $false. The default value is $false. | - |
| EnableLanguageBlockList | Write | Boolean | The EnableLanguageBlockList parameter enables or disables blocking email messages that are written in specific languages, regardless of the message contents. Valid input for this parameter is $true or $false. The default value is $false. | - |
| EnableRegionBlockList | Write | Boolean | The EnableRegionBlockList parameter enables or disables blocking email messages that are sent from specific countries or regions, regardless of the message contents. Valid input for this parameter is $true or $false. The default value is $false. | - |
| EndUserSpamNotificationCustomSubject | Write | String | The EndUserSpamNotificationCustomSubject parameter specifies a custom subject for end-user spam notification messages. | - |
| EndUserSpamNotificationFrequency | Write | UInt32 | The EndUserSpamNotificationFrequency parameter specifies the repeat interval in days that end-user spam notification messages are sent. Valid input for this parameter is an integer between 1 and 15. The default value is 3. | - |
| EndUserSpamNotificationLanguage | Write | String | The EndUserSpamNotificationLanguage parameter specifies the language of end-user spam notification messages. The default value is Default. This means the default language of end-user spam notification messages is the default language of the cloud-based organization. | `Default`, `English`, `French`, `German`, `Italian`, `Japanese`, `Spanish`, `Korean`, `Portuguese`, `Russian`, `ChineseSimplified`, `ChineseTraditional`, `Amharic`, `Arabic`, `Bulgarian`, `BengaliIndia`, `Catalan`, `Czech`, `Cyrillic`, `Danish`, `Greek`, `Estonian`, `Basque`, `Persian`, `Finnish`, `Filipino`, `Galician`, `Gujarati`, `Hebrew`, `Hindi`, `Croatian`, `Hungarian`, `Indonesian`, `Icelandic`, `Kazakh`, `Kannada`, `Lithuanian`, `Latvian`, `Malayalam`, `Marathi`, `Malay`, `Dutch`, `NorwegianNynorsk`, `Norwegian`, `Odia`, `Polish`, `PortuguesePortugal`, `Romanian`, `Slovak`, `Slovenian`, `SerbianCyrillic`, `Serbian`, `Swedish`, `Swahili`, `Tamil`, `Telugu`, `Thai`, `Turkish`, `Ukrainian`, `Urdu`, `Vietnamese` |
| HighConfidencePhishAction | Write | String | The HighConfidencePhishAction parameter specifies the action to take on messages that are marked as high confidence phishing | `MoveToJmf`, `Redirect`, `Quarantine` |
| HighConfidencePhishQuarantineTag | Write | String | The HighConfidencePhishQuarantineTag parameter specifies the quarantine policy that's used on messages that are quarantined as high confidence phishing. | - |
| HighConfidenceSpamAction | Write | String | The HighConfidenceSpamAction parameter specifies the action to take on messages that are classified as high confidence spam. | `MoveToJmf`, `AddXHeader`, `ModifySubject`, `Redirect`, `Delete`, `Quarantine`, `NoAction` |
| HighConfidenceSpamQuarantineTag | Write | String | The HighConfidenceSpamQuarantineTag parameter specifies the quarantine policy that's used on messages that are quarantined as high confidence spam. | - |
| IncreaseScoreWithBizOrInfoUrls | Write | String | The IncreaseScoreWithBizOrInfoUrls parameter increases the spam score of messages that contain links to .biz or .info domains. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| IncreaseScoreWithImageLinks | Write | String | The IncreaseScoreWithImageLinks parameter increases the spam score of messages that contain image links to remote websites. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| IncreaseScoreWithNumericIps | Write | String | The IncreaseScoreWithNumericIps parameter increases the spam score of messages that contain links to IP addresses. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| IncreaseScoreWithRedirectToOtherPort | Write | String | The IncreaseScoreWithRedirectToOtherPort parameter increases the spam score of messages that contain links that redirect to other TCP ports. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| InlineSafetyTipsEnabled | Write | Boolean | The InlineSafetyTipsEnabled parameter specifies whether to enable or disable safety tips that are shown to recipients in messages. The default is $true | - |
| IntraOrgFilterState | Write | String | The IntraOrgFilterState parameter specifies whether to enable anti-spam filtering for messages sent between internal users \(users in the same organization\). | `Default`, `HighConfidencePhish`, `Phish`, `HighConfidenceSpam`, `Spam`, `Disabled` |
| LanguageBlockList | Write | StringArray\[\] | The LanguageBlockList parameter specifies the languages to block when messages are blocked based on their language. Valid input for this parameter is a supported ISO 639-1 lowercase two-letter language code. You can specify multiple values separated by commas. This parameter is only use when the EnableRegionBlockList parameter is set to $true. | - |
| MakeDefault | Write | Boolean | The MakeDefault parameter makes the specified content filter policy the default content filter policy. The default value is $false | - |
| MarkAsSpamBulkMail | Write | String | The MarkAsSpamBulkMail parameter classifies the message as spam when the message is identified as a bulk email message. Valid values for this parameter are Off, On or Test. The default value is On. | `Off`, `On`, `Test` |
| MarkAsSpamEmbedTagsInHtml | Write | String | The MarkAsSpamEmbedTagsInHtml parameter classifies the message as spam when the message contains HTML <embed> tags. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamEmptyMessages | Write | String | The MarkAsSpamEmptyMessages parameter classifies the message as spam when the message is empty. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamFormTagsInHtml | Write | String | The MarkAsSpamFormTagsInHtml parameter classifies the message as spam when the message contains HTML <form> tags. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamFramesInHtml | Write | String | The MarkAsSpamFramesInHtml parameter classifies the message as spam when the message contains HTML <frame> or <iframe> tags. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamFromAddressAuthFail | Write | String | The MarkAsSpamFromAddressAuthFail parameter classifies the message as spam when Sender ID filtering encounters a hard fail. Valid values for this parameter are Off or On. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamJavaScriptInHtml | Write | String | The MarkAsSpamJavaScriptInHtml parameter classifies the message as spam when the message contains JavaScript or VBScript. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamNdrBackscatter | Write | String | The MarkAsSpamNdrBackscatter parameter classifies the message as spam when the message is a non-delivery report \(NDR\) to a forged sender. Valid values for this parameter are Off or On. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamObjectTagsInHtml | Write | String | The MarkAsSpamObjectTagsInHtml parameter classifies the message as spam when the message contains HTML <object> tags. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamSensitiveWordList | Write | String | The MarkAsSpamSensitiveWordList parameter classifies the message as spam when the message contains words from the sensitive words list. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamSpfRecordHardFail | Write | String | The MarkAsSpamSpfRecordHardFail parameter classifies the message as spam when Sender Policy Framework \(SPF\) record checking encounters a hard fail. Valid values for this parameter are Off or On. The default value is Off. | `Off`, `On`, `Test` |
| MarkAsSpamWebBugsInHtml | Write | String | The MarkAsSpamWebBugsInHtml parameter classifies the message as spam when the message contains web bugs. Valid values for this parameter are Off, On or Test. The default value is Off. | `Off`, `On`, `Test` |
| ModifySubjectValue | Write | String | The ModifySubjectValue parameter specifies the text to prepend to the existing subject of spam messages when an action parameter is set to the value ModifySubject. | - |
| PhishSpamAction | Write | String | The PhishSpamAction parameter specifies the action to take on messages that are classified as phishing | `MoveToJmf`, `AddXHeader`, `ModifySubject`, `Redirect`, `Delete`, `Quarantine`, `NoAction` |
| PhishQuarantineTag | Write | String | The PhishQuarantineTag parameter specifies the quarantine policy that's used on messages that are quarantined as phishing. | - |
| SpamQuarantineTag | Write | String | The SpamQuarantineTag parameter specifies the quarantine policy that's used on messages that are quarantined as spam. | - |
| QuarantineRetentionPeriod | Write | UInt32 | The QuarantineRetentionPeriod parameter specifies the length of time in days that spam messages remain in the quarantine. Valid input for this parameter is an integer between 1 and 30. The default value is 15. | - |
| RedirectToRecipients | Write | StringArray\[\] | The RedirectToRecipients parameter specifies the replacement recipients in spam messages when an action parameter is set to the value Redirect. The action parameters that use the value of RedirectToRecipients are BulkSpamAction, HighConfidencePhishAction, HighConfidenceSpamAction, PhishSpamAction and SpamAction. | - |
| RegionBlockList | Write | StringArray\[\] | The RegionBlockList parameter specifies the region to block when messages are blocked based on their source region. Valid input for this parameter is a supported ISO 3166-1 uppercase two-letter country code. You can specify multiple values separated by commas. This parameter is only used when the EnableRegionBlockList parameter is set to $true. | - |
| SpamAction | Write | String | The SpamAction parameter specifies the action to take on messages that are classified as spam \(not high confidence spam, bulk email, or phishing\). | `MoveToJmf`, `AddXHeader`, `ModifySubject`, `Redirect`, `Delete`, `Quarantine`, `NoAction` |
| TestModeAction | Write | String | The TestModeAction parameter specifies the additional action to take on messages that match any of the IncreaseScoreWith or MarkAsSpam parameters that are set to the value Test. | `None`, `AddXHeader`, `BccMessage` |
| TestModeBccToRecipients | Write | StringArray\[\] | The TestModeBccToRecipients parameter specifies the blind carbon copy recipients to add to spam messages when the TestModeAction action parameter is set to the value BccMessage. | - |
| PhishZapEnabled | Write | Boolean | The PhishZapEnabled parameter enables or disables zero-hour auto purge \(ZAP\) to detect phishing messages in delivered messages in Exchange Online mailboxes. | - |
| SpamZapEnabled | Write | Boolean | The SpamZapEnabled parameter enables or disables zero-hour auto purge \(ZAP\) to detect spam in delivered messages in Exchange Online mailboxes. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## hostedContentFilterRule resource type

### Description

This resource configures a [Hosted Content Filter Rule in Exchange Online](https://learn.microsoft.com/en-us/powershell/module/exchange/advanced-threat-protection/new-HostedContentFilterRule?view=exchange-ps).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the HostedContentFilter rule that you want to modify. | - |
| HostedContentFilterPolicy | Required | String | The HostedContentFilterPolicy parameter specifies the name of the HostedContentFilter policy that's associated with the HostedContentFilter rule. | - |
| Enabled | Write | Boolean | Specify if this rule should be enabled. Default is $true. | - |
| Priority | Write | UInt32 | The Priority parameter specifies a priority value for the rule that determines the order of rule processing. A lower integer value indicates a higher priority, the value 0 is the highest priority, and rules can't have the same priority value. | - |
| Comments | Write | String | The Comments parameter specifies informative comments for the rule, such as what the rule is used for or how it has changed over time. The length of the comment can't exceed 1,024 characters. | - |
| ExceptIfRecipientDomainIs | Write | StringArray\[\] | The ExceptIfRecipientDomainIs parameter specifies an exception that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| ExceptIfSentTo | Write | StringArray\[\] | The ExceptIfSentTo parameter specifies an exception that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| ExceptIfSentToMemberOf | Write | StringArray\[\] | The ExceptIfSentToMemberOf parameter specifies an exception that looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |
| RecipientDomainIs | Write | StringArray\[\] | The RecipientDomainIs parameter specifies a condition that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| SentTo | Write | StringArray\[\] | The SentTo parameter specifies a condition that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| SentToMemberOf | Write | StringArray\[\] | The SentToMemberOf parameter looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## hostedOutboundSpamFilterPolicy resource type

### Description

This resource configures the settings of the outbound spam filter policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the policy that you want to modify. there's only one policy named 'Default' | - |
| AdminDisplayName | Write | String | The AdminDisplayName parameter specifies a description for the policy. | - |
| BccSuspiciousOutboundAdditionalRecipients | Write | StringArray\[\] | The BccSuspiciousOutboundAdditionalRecipients parameter specifies the recipients to add to the Bcc field of outgoing spam messages. Valid input for this parameter is an email address. Separate multiple email addresses with commas. | - |
| BccSuspiciousOutboundMail | Write | Boolean | The BccSuspiciousOutboundMail parameter enables or disables adding recipients to the Bcc field of outgoing spam messages. Valid input for this parameter is $true or $false. The default value is $false. You specify the additional recipients using the BccSuspiciousOutboundAdditionalRecipients parameter. | - |
| NotifyOutboundSpam | Write | Boolean | The NotifyOutboundSpam parameter enables or disables sending notification messages to administrators when an outgoing message is determined to be spam. Valid input for this parameter is $true or $false. The default value is $false. You specify the administrators to notify by using the NotifyOutboundSpamRecipients parameter. | - |
| NotifyOutboundSpamRecipients | Write | StringArray\[\] | The NotifyOutboundSpamRecipients parameter specifies the administrators to notify when an outgoing message is determined to be spam. Valid input for this parameter is an email address. Separate multiple email addresses with commas. | - |
| RecipientLimitInternalPerHour | Write | UInt32 | The RecipientLimitInternalPerHour parameter specifies the maximum number of internal recipients that a user can send to within an hour. A valid value is 0 to 10000. The default value is 0, which means the service defaults are used. | - |
| RecipientLimitPerDay | Write | UInt32 | The RecipientLimitPerDay parameter specifies the maximum number of recipients that a user can send to within a day. A valid value is 0 to 10000. The default value is 0, which means the service defaults are used. | - |
| RecipientLimitExternalPerHour | Write | UInt32 | The RecipientLimitExternalPerHour parameter specifies the maximum number of external recipients that a user can send to within an hour. A valid value is 0 to 10000. The default value is 0, which means the service defaults are used. | - |
| ActionWhenThresholdReached | Write | String | The ActionWhenThresholdReached parameter specifies the action to take when any of the limits specified in the policy are reached. Valid values are: Alert, BlockUser, BlockUserForToday. BlockUserForToday is the default value. | - |
| AutoForwardingMode | Write | String | The AutoForwardingMode specifies how the policy controls automatic email forwarding to outbound recipients. Valid values are: Automatic, On, Off. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## hostedOutboundSpamFilterRule resource type

### Description

This resource configures a [Hosted Content Filter Rule in Exchange Online](https://learn.microsoft.com/en-us/powershell/module/exchange/new-hostedoutboundspamfilterrule?view=exchange-ps).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the HostedOutboundSpamFilter rule that you want to modify. | - |
| HostedOutboundSpamFilterPolicy | Required | String | The HostedOutboundSpamFilterPolicy parameter specifies the name of the HostedOutboundSpamFilter policy that's associated with the HostedOutboundSpamFilter rule. | - |
| Enabled | Write | Boolean | Specify if this rule should be enabled. Default is $true. | - |
| Priority | Write | UInt32 | The Priority parameter specifies a priority value for the rule that determines the order of rule processing. A lower integer value indicates a higher priority, the value 0 is the highest priority, and rules can't have the same priority value. | - |
| Comments | Write | String | The Comments parameter specifies informative comments for the rule, such as what the rule is used for or how it has changed over time. The length of the comment can't exceed 1,024 characters. | - |
| ExceptIfSenderDomainIs | Write | StringArray\[\] | The ExceptIfSenderDomainIs parameter specifies an exception that looks for senders with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| ExceptIfFrom | Write | StringArray\[\] | The ExceptIfFrom parameter specifies an exception that looks for messages from specific senders. You can use any value that uniquely identifies the sender. | - |
| ExceptIfFromMemberOf | Write | StringArray\[\] | The ExceptIfFromMemberOf parameter specifies an exception that looks for messages sent by group members. You can use any value that uniquely identifies the group. | - |
| SenderDomainIs | Write | StringArray\[\] | The SenderDomainIs parameter specifies a condition that looks for senders with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| From | Write | StringArray\[\] | The From parameter specifies a condition that looks for messages from specific senders. You can use any value that uniquely identifies the sender. | - |
| FromMemberOf | Write | StringArray\[\] | The FromMemberOf parameter specifies a condition that looks for messages sent by group members. You can use any value that uniquely identifies the group. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## inboundConnector resource type

### Description

This resource configures an Inbound connector in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the outbound connector that you want to modify. | - |
| AssociatedAcceptedDomains | Write | StringArray\[\] | The AssociatedAcceptedDomains parameter specifies the accepted domains that the connector applies to, thereby limiting its scope. For example, you can apply the connector to a specific accepted domain in your organization, such as contoso.com. | - |
| CloudServicesMailEnabled | Write | Boolean | The CloudServicesMailEnabled parameter specifies whether the connector is used for hybrid mail flow between an on-premises Exchange environment and Microsoft Office 365. Specifically, this parameter controls how certain internal X-MS-Exchange-Organization-\* message headers are handled in messages that are sent between accepted domains in the on-premises and cloud organizations. These headers are collectively known as cross-premises headers. DO NOT USE MANUALLY! | - |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| ConnectorSource | Write | String | The ConnectorSource parameter specifies how the connector is created. DO NOT CHANGE THIS! | `Default`, `Migrated`, `HybridWizard` |
| ConnectorType | Write | String | The ConnectorType parameter specifies a category for the domains that are serviced by the connector. Valid values are Partner and OnPremises | `Partner`, `OnPremises` |
| EFSkipIPs | Write | StringArray\[\] | The EFSkipIPs parameter specifies the source IP addresses to skip in Enhanced Filtering for Connectors when the EFSkipLastIP parameter value is $false. | - |
| EFSkipLastIP | Write | Boolean | The EFSkipLastIP parameter specifies the behavior of Enhanced Filtering for Connectors. | - |
| EFUsers | Write | StringArray\[\] | The EFUsers parameter specifies the recipients that Enhanced Filtering for Connectors applies to. | - |
| Enabled | Write | Boolean | Specifies whether connector is enabled. | - |
| RequireTls | Write | Boolean | The RequireTLS parameter specifies that all messages received by this connector require TLS transmission. Valid values for this parameter are $true or $false. The default value is $false. When the RequireTLS parameter is set to $true, all messages received by this connector require TLS transmission. | - |
| RestrictDomainsToCertificate | Write | Boolean | The RestrictDomainsToCertificate parameter specifies that Office 365 should identify incoming messages that are eligible for this connector by verifying that the remote server authenticates using a TLS certificate that has the TlsSenderCertificateName in the Subject. | - |
| RestrictDomainsToIPAddresses | Write | Boolean | The RestrictDomainsToIPAddresses parameter, when set to $true, automatically rejects mail from the domains specified by the SenderDomains parameter if the mail originates from an IP address that isn't specified by the SenderIPAddresses parameter. | - |
| SenderDomains | Write | StringArray\[\] | The SenderDomains parameter specifies the remote domains from which this connector accepts messages, thereby limiting its scope. You can use a wildcard character to specify all subdomains of a specified domain, as shown in the following example: *.contoso.com. However, you can't embed a wildcard character, as shown in the following example: domain.*.contoso.com. | - |
| SenderIPAddresses | Write | StringArray\[\] | The SenderIPAddresses parameter specifies the remote IP addresses from which this connector accepts messages. | - |
| TlsSenderCertificateName | Write | String | The TlsSenderCertificateName parameter specifies the certificate used by the sender's domain when the RequireTls parameter is set to $true. Valid input for the TlsSenderCertificateName parameter is an SMTP domain. | - |
| TreatMessagesAsInternal | Write | Boolean | The TreatMessagesAsInternal parameter specifies an alternative method to identify messages sent from an on-premises organization as internal messages. You should only consider using this parameter when your on-premises organization doesn't use Exchange. | - |
| Ensure | Write | String | Specifies if this Outbound connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Remote and Accepted Domains, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## intraOrganizationConnector resource type

### Description

Create a new EXOIntraOrganizationConnector in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the intraorg connector that you want to modify. | - |
| DiscoveryEndpoint | Write | String | The DiscoveryEndpoint parameter specifies the externally-accessible URL that's used for the Autodiscover service for the domain that's configured in the Intra-Organization connector. | - |
| Enabled | Write | Boolean | Specifies whether connector is enabled. | - |
| TargetAddressDomains | Write | StringArray\[\] | The TargetAddressDomains parameter specifies the domain namespaces that will be used in the Intra-organization connector. These domains must have valid Autodiscover endpoints defined in their organizations. The domains and their associated Autodiscover endpoints are used by the Intra-Organization connector for feature and service connectivity. You can specify multiple domains separated by commas. | - |
| TargetSharingEpr | Write | String | The TargetSharingEpr parameter specifies the URL of the target Exchange Web Services that will be used in the Intra-Organization connector. | - |
| Ensure | Write | String | Specifies if this Intra-Organization connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Federated Sharing, Organization Transport Settings, View-Only Configuration, Mail Tips, Message Tracking

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## irmConfiguration resource type

### Description

Modify the resource Configuration policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| AutomaticServiceUpdateEnabled | Write | Boolean | The AutomaticServiceUpdateEnabled parameter specifies whether to allow the automatic addition of new features within Azure Information Protection for your cloud-based organization. | - |
| AzureRMSLicensingEnabled | Write | Boolean | The AzureRMSLicensingEnabled parameter specifies whether the Exchange Online organization can to connect directly to Azure Rights Management. | - |
| DecryptAttachmentForEncryptOnly | Write | Boolean | The DecryptAttachmentForEncryptOnly parameter specifies whether mail recipients have unrestricted rights on the attachment or not for Encrypt-only mails sent using Microsoft Purview Message Encryption. | - |
| EDiscoverySuperUserEnabled | Write | Boolean | The EDiscoverySuperUserEnabled parameter specifies whether members of the Discovery Management role group can access IRM-protected messages in a discovery mailbox that were returned by a discovery search. | - |
| EnablePdfEncryption | Write | Boolean | The EnablePdfEncryption parameter specifies whether to enable the encryption of PDF attachments using Microsoft Purview Message Encryption. | - |
| InternalLicensingEnabled | Write | Boolean | The InternalLicensingEnabled parameter specifies whether to enable IRM features for messages that are sent to internal and external recipients. | - |
| JournalReportDecryptionEnabled | Write | Boolean | The JournalReportDecryptionEnabled parameter specifies whether to enable journal report decryption. | - |
| LicensingLocation | Write | StringArray\[\] | The LicensingLocation parameter specifies the RMS licensing URLs. You can specify multiple URL values separated by commas. | - |
| RejectIfRecipientHasNoRights | Write | Boolean | This parameter is available only in the cloud-based service. | - |
| RMSOnlineKeySharingLocation | Write | String | The RMSOnlineKeySharingLocation parameter specifies the Azure Rights Management URL that's used to get the trusted publishing domain \(TPD\) for the Exchange Online organization. | - |
| SearchEnabled | Write | Boolean | The SearchEnabled parameter specifies whether to enable searching of IRM-encrypted messages in Outlook on the web \(formerly known as Outlook Web App\). | - |
| SimplifiedClientAccessDoNotForwardDisabled | Write | Boolean | The SimplifiedClientAccessDoNotForwardDisabled parameter specifies whether to disable Do not forward in Outlook on the web. | - |
| SimplifiedClientAccessEnabled | Write | Boolean | The SimplifiedClientAccessEnabled parameter specifies whether to enable the Protect button in Outlook on the web. | - |
| SimplifiedClientAccessEncryptOnlyDisabled | Write | Boolean | The SimplifiedClientAccessEncryptOnlyDisabled parameter specifies whether to disable Encrypt only in Outlook on the web. | - |
| TransportDecryptionSetting | Write | String | The TransportDecryptionSetting parameter specifies the transport decryption configuration. | `Disabled`, `Mandatory`, `Optional` |
| Ensure | Write | String | Specifies if this Outbound connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Information Rights Management, View-Only Configuration

##### Role Groups

- Organization Management, Compliance Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## journalRule resource type

### Description

This resource allows to configure Journal Rules in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | Name of the Journal Rule | - |
| JournalEmailAddress | Key | String | The JournalEmailAddress parameter specifies a recipient object to which journal reports are sent. You can use any value that uniquely identifies the recipient. | - |
| Recipient | Write | String | The Recipient parameter specifies the SMTP address of a mailbox, contact, or distribution group to journal. If you specify a distribution group, all recipients in that distribution group are journaled. All messages sent to or from a recipient are journaled. | - |
| Enabled | Write | Boolean | Specifies whether the Journal Rule is enabled or not. | - |
| RuleScope | Write | String | The Scope parameter specifies the scope of email messages to which the journal rule is applied | `Global`, `Internal`, `External` |
| Ensure | Write | String | Present ensures the rule exists, Absent that it does not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Compliance Admin, View-Only Configuration, Journaling

##### Role Groups

- Organization Management, Compliance Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## mailboxAutoReplyConfiguration resource type

### Description

This resource configures the Auto Reply settings of mailboxes.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the mailbox that you want to modify. You can use any value that uniquely identifies the mailbox. | - |
| Owner | Write | String | User Principal Name of the mailbox owner | - |
| AutoDeclineFutureRequestsWhenOOF | Write | Boolean | The AutoDeclineFutureRequestsWhenOOF parameter specifies whether to automatically decline new meeting requests that are sent to the mailbox during the scheduled time period when Automatic Replies are being sent. | - |
| AutoReplyState | Write | String | The AutoReplyState parameter specifies whether the mailbox is enabled for Automatic Replies. Valid values are: Enabled, Disabled, Scheduled | `Enabled`, `Disabled`, `Scheduled` |
| CreateOOFEvent | Write | Boolean | The CreateOOFEvent parameter specifies whether to create a calendar event that corresponds to the scheduled time period when Automatic Replies are being sent for the mailbox. | - |
| DeclineAllEventsForScheduledOOF | Write | Boolean | The DeclineAllEventsForScheduledOOF parameter specifies whether to decline all existing calendar events in the mailbox during the scheduled time period when Automatic Replies are being sent. | - |
| DeclineEventsForScheduledOOF | Write | Boolean | The DeclineEventsForScheduledOOF parameter specifies whether it's possible to decline existing calendar events in the mailbox during the scheduled time period when Automatic Replies are being sent. | - |
| DeclineMeetingMessage | Write | String | The DeclineMeetingMessage parameter specifies the text in the message when meetings requests that are sent to the mailbox are automatically declined. | - |
| EndTime | Write | String | The EndTime parameter specifies the end date and time that Automatic Replies are sent for the mailbox. You use this parameter only when the AutoReplyState parameter is set to Scheduled, and the value of this parameter is meaningful only when AutoReplyState is Scheduled. | - |
| EventsToDeleteIDs | Write | StringArray\[\] | The EventsToDeleteIDs parameter specifies the calendar events to delete from the mailbox when the DeclineEventsForScheduledOOF parameter is set to $true. | - |
| ExternalAudience | Write | String | The ExternalAudience parameter specifies whether Automatic Replies are sent to external senders. Valid values are: None, Known, All | `None`, `Known`, `All` |
| ExternalMessage | Write | String | The ExternalMessage parameter specifies the Automatic Replies message that's sent to external senders or senders outside the organization. If the value contains spaces, enclose the value in quotation marks. | - |
| InternalMessage | Write | String | The InternalMessage parameter specifies the Automatic Replies message that's sent to internal senders or senders within the organization. If the value contains spaces, enclose the value in quotation marks. | - |
| OOFEventSubject | Write | String | The OOFEventSubject parameter specifies the subject for the calendar event that's automatically created when the CreateOOFEvent parameter is set to $true. | - |
| StartTime | Write | String | The StartTime parameter specifies the start date and time that Automatic Replies are sent for the specified mailbox. You use this parameter only when the AutoReplyState parameter is set to Scheduled, and the value of this parameter is meaningful only when AutoReplyState is Scheduled. | - |
| Ensure | Write | String | Represents the existance of the instance. This must be set to 'Present' | `Present` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## mailboxCalendarFolder resource type

### Description

This resource configures calendar publishing or sharing settings on a mailbox for the visibility of calendar information to external users.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the calendar folder that you want to modify. | - |
| DetailLevel | Write | String | The DetailLevel parameter specifies the level of calendar detail that's published and available to anonymous users. | `AvailabilityOnly`, `LimitedDetails`, `FullDetails` |
| PublishDateRangeFrom | Write | String | The PublishDateRangeFrom parameter specifies the start date of calendar information to publish \(past information\). | `OneDay`, `ThreeDays`, `OneWeek`, `OneMonth`, `ThreeMonths`, `SixMonths`, `OneYear` |
| PublishDateRangeTo | Write | String | The PublishDateRangeTo parameter specifies the end date of calendar information to publish \(future information\). | `OneDay`, `ThreeDays`, `OneWeek`, `OneMonth`, `ThreeMonths`, `SixMonths`, `OneYear` |
| PublishEnabled | Write | Boolean | The PublishEnabled parameter specifies whether to publish the specified calendar information. | - |
| SearchableUrlEnabled | Write | Boolean | The SearchableUrlEnabled parameter specifies whether the published calendar URL is discoverable on the web. | - |
| SharedCalendarSyncStartDate | Write | String | The SharedCalendarSyncStartDate parameter specifies the limit for past events in the shared calendar that are visible to delegates. A copy of the shared calendar within the specified date range is stored in the delegate's mailbox. | - |
| Ensure | Write | String | Determines wether or not the instance exist. | `Present` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Organization Management, Recipient Management

##### Role Groups

- Organization Management, Help Desk

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## mailboxPermission resource type

### Description

Use this resource to modify the permissions of mailbox.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the mailbox where you want to assign permissions to the user. You can use any value that uniquely identifies the mailbox. | - |
| AccessRights | Required | StringArray\[\] | The AccessRights parameter specifies the permission that you want to add for the user on the mailbox. Valid values are: ChangeOwner, ChangePermission, DeleteItem, ExternalAccount, FullAccess and ReadPermission. | - |
| User | Key | String | The User parameter specifies who gets the permissions on the mailbox. | - |
| InheritanceType | Key | String | The InheritanceType parameter specifies how permissions are inherited by folders in the mailbox. Valid values are: None, All, Children, Descendents, SelfAndChildren. | `None`, `All`, `Children`, `Descendents`, `SelfAndChildren` |
| Owner | Write | String | The Owner parameter specifies the owner of the mailbox object. | - |
| Deny | Write | Boolean | The Deny switch specifies that the permissions you're adding are Deny permissions. | - |
| Ensure | Write | String | Determines wheter or not the permission should exist on the mailbox. | `Present` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Unified Messaging, View-Only Recipients, Mail Recipient Creation, Mail Recipients, UM Mailboxes

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## mailboxPlan resource type

### Description

Use this resource to modify the settings of mailbox plans in the cloud-based service.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the Mailbox Plan that you want to modify. | - |
| DisplayName | Write | String | The display name of the mailbox plan. | - |
| Ensure | Write | String | MailboxPlans can't be created/removed in O365. This must be set to 'Present' | `Present` |
| IssueWarningQuota | Write | String | The IssueWarningQuota parameter specifies the warning threshold for the size of the mailboxes that are created or enabled using the mailbox plan. | - |
| MaxReceiveSize | Write | String | The MaxReceiveSize parameter specifies the maximum size of a message that can be sent to the mailbox. | - |
| MaxSendSize | Write | String | The MaxSendSize parameter specifies the maximum size of a message that can be sent by the mailbox. | - |
| ProhibitSendQuota | Write | String | The ProhibitSendQuota parameter specifies a size limit for the mailbox. | - |
| ProhibitSendReceiveQuota | Write | String | The ProhibitSendReceiveQuota parameter specifies a size limit for the mailbox. | - |
| RetainDeletedItemsFor | Write | String | The RetainDeletedItemsFor parameter specifies the length of time to keep soft-deleted items for the mailbox. | - |
| RetentionPolicy | Write | String | The RetentionPolicy parameter specifies the retention policy that's applied to the mailbox. | - |
| RoleAssignmentPolicy | Write | String | The RoleAssignmentPolicy parameter specifies the role assignment policy that's applied to the mailbox. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Unified Messaging, View-Only Recipients, Mail Recipient Creation, Mail Recipients, UM Mailboxes

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## mailboxSettings resource type

### Description

This resource configures settings on Mailboxes such as the Regional settings and its timezone.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The display name of the Shared Mailbox | - |
| TimeZone | Write | String | The name of the Time Zone to assign to the mailbox | - |
| Locale | Write | String | The code of the Locale to assign to the mailbox | - |
| Ensure | Write | String | Present ensures the Mailbox Settings are applied | `Present` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- User Options, View-Only Recipients, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## mailContact resource type

### Description

This resource configures Exchange Online address lists.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies a unique name for the mail contact. | - |
| ExternalEmailAddress | Required | String | The ExternalEmailAddress parameter specifies the target email address of the mail contact or mail user. By default, this value is used as the primary email address of the mail contact or mail user. | - |
| Alias | Write | String | The Alias parameter specifies the Exchange alias \(also known as the mail nickname\) for the recipient. This value identifies the recipient as a mail-enabled object, and shouldn't be confused with multiple email addresses for the same recipient \(also known as proxy addresses\). A recipient can have only one Alias value. The maximum length is 64 characters. | - |
| DisplayName | Write | String | The DisplayName parameter specifies the display name of the mail contact. The display name is visible in the Exchange admin center and in address lists. | - |
| FirstName | Write | String | The FirstName parameter specifies the user's first name. | - |
| Initials | Write | String | The Initials parameter specifies the user's middle initials. | - |
| LastName | Write | String | The LastName parameter specifies the user's last name. | - |
| MacAttachmentFormat | Write | String | The MacAttachmentFormat parameter specifies the Apple Macintosh operating system attachment format to use for messages sent to the mail contact or mail user. Valid values are: BinHex, UuEncode, AppleSingle, AppleDouble | `BinHex`, `UuEncode`, `AppleSingle`, `AppleDouble` |
| MessageBodyFormat | Write | String | The MessageBodyFormat parameter specifies the message body format for messages sent to the mail contact or mail user. Valid values are: Text, Html, TextAndHtml | `Text`, `Html`, `TextAndHtml` |
| MessageFormat | Write | String | The MessageFormat parameter specifies the message format for messages sent to the mail contact or mail user. Valid values are: Mime, Text | `Mime`, `Text` |
| ModeratedBy | Write | StringArray\[\] | The ModeratedBy parameter specifies one or more moderators for this mail contact. A moderator approves messages sent to the mail contact before the messages are delivered. A moderator must be a mailbox, mail user, or mail contact in your organization. | - |
| ModerationEnabled | Write | Boolean | The ModerationEnabled parameter specifies whether moderation is enabled for this recipient. | - |
| OrganizationalUnit | Write | String | The OrganizationalUnit parameter specifies the location in Active Directory where the new contact is created. | - |
| SendModerationNotifications | Write | String | The SendModerationNotifications parameter specifies when moderation notification messages are sent. Valid values are: ALways, Internal, Never | `Always`, `Internal`, `Never` |
| UsePreferMessageFormat | Write | Boolean | The UsePreferMessageFormat specifies whether the message format settings configured for the mail user or mail contact override the global settings configured for the remote domain or configured by the message sender | - |
| CustomAttribute1 | Write | String | The CustomAttribute1 parameter specifies the value of the CustomAttribute1 | - |
| CustomAttribute2 | Write | String | The CustomAttribute2 parameter specifies the value of the CustomAttribute2 | - |
| CustomAttribute3 | Write | String | The CustomAttribute3 parameter specifies the value of the CustomAttribute3 | - |
| CustomAttribute4 | Write | String | The CustomAttribute4 parameter specifies the value of the CustomAttribute4 | - |
| CustomAttribute5 | Write | String | The CustomAttribute5 parameter specifies the value of the CustomAttribute5 | - |
| CustomAttribute6 | Write | String | The CustomAttribute6 parameter specifies the value of the CustomAttribute6 | - |
| CustomAttribute7 | Write | String | The CustomAttribute7 parameter specifies the value of the CustomAttribute7 | - |
| CustomAttribute8 | Write | String | The CustomAttribute8 parameter specifies the value of the CustomAttribute8 | - |
| CustomAttribute9 | Write | String | The CustomAttribute9 parameter specifies the value of the CustomAttribute9 | - |
| CustomAttribute10 | Write | String | The CustomAttribute10 parameter specifies the value of the CustomAttribute10 | - |
| CustomAttribute11 | Write | String | The CustomAttribute11 parameter specifies the value of the CustomAttribute11 | - |
| CustomAttribute12 | Write | String | The CustomAttribute12 parameter specifies the value of the CustomAttribute12 | - |
| CustomAttribute13 | Write | String | The CustomAttribute13 parameter specifies the value of the CustomAttribute13 | - |
| CustomAttribute14 | Write | String | The CustomAttribute14 parameter specifies the value of the CustomAttribute14 | - |
| CustomAttribute15 | Write | String | The CustomAttribute15 parameter specifies the value of the CustomAttribute15 | - |
| ExtensionCustomAttribute1 | Write | StringArray\[\] | The ExtensionCustomAttribute1 parameter specifies the value of the ExtensionCustomAttribute1 | - |
| ExtensionCustomAttribute2 | Write | StringArray\[\] | The ExtensionCustomAttribute2 parameter specifies the value of the ExtensionCustomAttribute2 | - |
| ExtensionCustomAttribute3 | Write | StringArray\[\] | The ExtensionCustomAttribute3 parameter specifies the value of the ExtensionCustomAttribute3 | - |
| ExtensionCustomAttribute4 | Write | StringArray\[\] | The ExtensionCustomAttribute4 parameter specifies the value of the ExtensionCustomAttribute4 | - |
| ExtensionCustomAttribute5 | Write | StringArray\[\] | The ExtensionCustomAttribute5 parameter specifies the value of the ExtensionCustomAttribute5 | - |
| Ensure | Write | String | Specifies if this Contact should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Address Lists

##### Role Groups

- None

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## mailTips resource type

### Description

This resource allows to configure Mailtips behaviors in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| MailTipsAllTipsEnabled | Write | Boolean | Specifies whether MailTips are enabled. | - |
| MailTipsGroupMetricsEnabled | Write | Boolean | Specifies whether MailTips that rely on group metrics data are enabled. | - |
| MailTipsLargeAudienceThreshold | Write | UInt32 | Specifies what a large audience is. | - |
| MailTipsMailboxSourcedTipsEnabled | Write | Boolean | Specifies whether MailTips that rely on mailbox data \(out-of-office or full mailbox\) are enabled. | - |
| MailTipsExternalRecipientsTipsEnabled | Write | Boolean | Specifies whether MailTips for external recipients are enabled. | - |
| Ensure | Write | String | Specifies if this MailTip should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Mail Tips, View-Only Configuration, Organization Configuration, Federated Sharing, Public Folders, Team Mailboxes, Compliance Admin, Recipient Policies, Remote and Accepted Domains, Distribution Groups, Mail Recipients

##### Role Groups

- Organization Management

## malwareFilterPolicy resource type

### Description

Create or modify a EXOMalwareFilterPolicy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the MalwareFilterPolicy you want to modify. | - |
| AdminDisplayName | Write | String | The AdminDisplayName parameter specifies a description for the policy. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomExternalBody | Write | String | The CustomExternalBody parameter specifies the body of the custom notification message for malware detections in messages from external senders. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomExternalSubject | Write | String | The CustomExternalSubject parameter specifies the subject of the custom notification message for malware detections in messages from external senders. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomFromAddress | Write | String | The CustomFromAddress parameter specifies the From address of the custom notification message for malware detections in messages from internal or external senders. | - |
| CustomFromName | Write | String | The CustomFromName parameter specifies the From name of the custom notification message for malware detections in messages from internal or external senders. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomInternalBody | Write | String | The CustomInternalBody parameter specifies the body of the custom notification message for malware detections in messages from internal senders. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomInternalSubject | Write | String | The CustomInternalSubject parameter specifies the subject of the custom notification message for malware detections in messages from internal senders. If the value contains spaces, enclose the value in quotation marks. | - |
| CustomNotifications | Write | Boolean | The CustomNotifications parameter enables or disables custom notification messages for malware detections in messages from internal or external senders. Valid values are: $true, $false. | - |
| EnableExternalSenderAdminNotifications | Write | Boolean | The EnableExternalSenderAdminNotifications parameter enables or disables sending malware detection notification messages to an administrator for messages from external senders. Valid values are: $true, $false. | - |
| EnableFileFilter | Write | Boolean | The EnableFileFilter parameter enables or disables common attachment blocking - also known as the Common Attachment Types Filter.Valid values are: $true, $false. | - |
| EnableInternalSenderAdminNotifications | Write | Boolean | The EnableInternalSenderAdminNotifications parameter enables or disables sending malware detection notification messages to an administrator for messages from internal senders. Valid values are: $true, $false. | - |
| ExternalSenderAdminAddress | Write | String | The ExternalSenderAdminAddress parameter specifies the email address of the administrator who will receive notification messages for malware detections in messages from external senders. | - |
| FileTypeAction | Write | String | The FileTypeAction parameter specifies what's done to messages that contain one or more attachments where the file extension is included in the FileTypes parameter \(common attachment blocking\). Valid values are Quarantine and Reject. The default value is Reject. | `Quarantine`, `Reject` |
| FileTypes | Write | StringArray\[\] | The FileTypes parameter specifies the file types that are automatically blocked by common attachment blocking \(also known as the Common Attachment Types Filter\), regardless of content. | - |
| InternalSenderAdminAddress | Write | String | The InternalSenderAdminAddress parameter specifies the email address of the administrator who will receive notification messages for malware detections in messages from internal senders. | - |
| MakeDefault | Write | Boolean | MakeDefault makes this malware filter policy the default policy. Valid values are: $true, $false. | - |
| QuarantineTag | Write | String | The QuarantineTag specifies the quarantine policy that's used on messages that are quarantined as malware. | - |
| ZapEnabled | Write | Boolean | The ZapEnabled parameter enables or disables zero-hour auto purge \(ZAP\) for malware. ZAP detects malware in unread messages that have already been delivered to the user's Inbox. Valid values are: $true, $false. | - |
| Ensure | Write | String | Specifies if this MalwareFilterPolicy should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## malwareFilterRule resource type

### Description

Create or modify a new EXOMalwareFilterRule in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the EXO resource you want to modify. | - |
| Comments | Write | String | The Comments parameter specifies informative comments for the rule, such as what the rule is used for or how it has changed over time. The length of the comment can't exceed 1,024 characters. | - |
| Enabled | Write | Boolean | The Enabled parameter enables or disables the malware filter rule. Valid input for this parameter is $true or $false. The default value is $true. | - |
| ExceptIfRecipientDomainIs | Write | StringArray\[\] | The ExceptIfRecipientDomainIs parameter specifies an exception that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| ExceptIfSentTo | Write | StringArray\[\] | The ExceptIfSentTo parameter specifies an exception that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| ExceptIfSentToMemberOf | Write | StringArray\[\] | The ExceptIfSentToMemberOf parameter specifies an exception that looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |
| MalwareFilterPolicy | Write | String | The MalwareFilterPolicy parameter specifies the malware filter policy to apply to messages that match the conditions defined by this malware filter rule. | - |
| Priority | Write | String | The Priority parameter specifies a priority value for the rule that determines the order of rule processing. A lower integer value indicates a higher priority, the value 0 is the highest priority, and rules can't have the same priority value. | - |
| RecipientDomainIs | Write | StringArray\[\] | The RecipientDomainIs parameter specifies a condition that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| SentTo | Write | StringArray\[\] | The SentTo parameter specifies a condition that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| SentToMemberOf | Write | StringArray\[\] | The SentToMemberOf parameter specifies a condition that looks for messages sent to members of distribution groups, dynamic distribution groups, or mail-enabled security groups. You can use any value that uniquely identifies the group. | - |
| Ensure | Write | String | Specifies if the Malware Filter Rule should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## managementRole resource type

### Description

This resource configures RBAC Management Roles in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the name of the role. The maximum length of the name is 64 characters. | - |
| Parent | Key | String | The Parent parameter specifies the identity of the role to copy. Mandatory for management role creation/update or when Ensure=Present. Non-mandatory for Ensure=Absent | - |
| Description | Write | String | The Description parameter specifies the description that's displayed when the management role is viewed using the Get-ManagementRole cmdlet. | - |
| Ensure | Write | String | Specify if the Management Role should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Role Management, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## managementRoleAssignment resource type

### Description

This resource configures RBAC Management Roles Assignments in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies a name for the new management role assignment. The maximum length of the name is 64 characters. | - |
| Role | Key | String | The Role parameter specifies the existing role to assign. You can use any value that uniquely identifies the role. | - |
| App | Write | String | The App parameter specifies the service principal to assign the management role to. Specifically, the ServiceId GUID value from the output of the Get-ServicePrincipal cmdlet \(for example, 6233fba6-0198-4277-892f-9275bf728bcc\). | - |
| Policy | Write | String | The Policy parameter specifies the name of the management role assignment policy to assign the management role to. | - |
| SecurityGroup | Write | String | The SecurityGroup parameter specifies the name of the management role group or mail-enabled universal security group to assign the management role to. | - |
| User | Write | String | The User parameter specifies the name or alias of the user to assign the management role to. | - |
| CustomRecipientWriteScope | Write | String | The CustomRecipientWriteScope parameter specifies the existing recipient-based management scope to associate with this management role assignment. | - |
| CustomResourceScope | Write | String | The CustomResourceScope parameter specifies the custom management scope to associate with this management role assignment. You can use any value that uniquely identifies the management scope. | - |
| ExclusiveRecipientWriteScope | Write | String | The ExclusiveConfigWriteScope parameter specifies the exclusive configuration-based management scope to associate with the new role assignment. | - |
| RecipientAdministrativeUnitScope | Write | String | The RecipientAdministrativeUnitScope parameter specifies the administrative unit to scope the new role assignment to. | - |
| RecipientOrganizationalUnitScope | Write | String | The RecipientOrganizationalUnitScope parameter specifies the OU to scope the new role assignment to. If you use the RecipientOrganizationalUnitScope parameter, you can't use the CustomRecipientWriteScope or ExclusiveRecipientWriteScope parameters. | - |
| RecipientRelativeWriteScope | Write | String | The RecipientRelativeWriteScope parameter specifies the type of restriction to apply to a recipient scope. The available types are None, Organization, MyGAL, Self, and MyDistributionGroups. The RecipientRelativeWriteScope parameter is automatically set when the CustomRecipientWriteScope or RecipientOrganizationalUnitScope parameters are used. | - |
| Ensure | Write | String | Specify if the Management Role Assignment should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Role Management, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## messageClassification resource type

### Description

Create a new Message Classification policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the OME Configuration policy that you want to modify. | - |
| ClassificationID | Write | String | The ClassificationID parameter specifies the classification ID \(GUID\) of an existing message classification that you want to import and use in your Exchange organization. | - |
| DisplayName | Write | String | The DisplayName parameter specifies the title of the message classification that's displayed in Outlook and selected by users. | - |
| DisplayPrecedence | Write | String | The DisplayPrecedence parameter specifies the relative precedence of the message classification to other message classifications that may be applied to a specified message. | `Highest`, `Higher`, `High`, `MediumHigh`, `Medium`, `MediumLow`, `Low`, `Lower`, `Lowest` |
| Name | Write | String | The Name parameter specifies the unique name for the message classification. | - |
| PermissionMenuVisible | Write | Boolean | The PermissionMenuVisible parameter specifies whether the values that you entered for the DisplayName and RecipientDescription parameters are displayed in Outlook as the user composes a message. | - |
| RecipientDescription | Write | String | The RecipientDescription parameter specifies the detailed text that's shown to Outlook recipient when they receive a message that has the message classification applied. | - |
| RetainClassificationEnabled | Write | Boolean | The RetainClassificationEnabled parameter specifies whether the message classification should persist with the message if the message is forwarded or replied to. | - |
| SenderDescription | Write | String | The SenderDescription parameter specifies the detailed text that's shown to Outlook senders when they select a message classification to apply to a message before they send the message. | - |
| Ensure | Write | String | Specifies if this Outbound connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- User Options, Data Loss Prevention, Transport Rules, View-Only Configuration, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## mobileDeviceMailboxPolicy resource type

### Description

This resource configures Mobile Device Mailbox Policies in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the friendly name of the mobile device mailbox policy. | - |
| AllowApplePushNotifications | Write | Boolean | The AllowApplePushNotifications parameter specifies whether push notifications are allowed to Apple mobile devices. | - |
| AllowBluetooth | Write | String | The AllowBluetooth parameter specifies whether the Bluetooth capabilities are allowed on the mobile phone. The available options are Disable, HandsfreeOnly, and Allow. The default value is Allow. | `Disable`, `HandsfreeOnly`, `Allow` |
| AllowBrowser | Write | Boolean | The AllowBrowser parameter indicates whether Microsoft Pocket Internet Explorer is allowed on the mobile phone. This parameter doesn't affect third-party browsers. | - |
| AllowCamera | Write | Boolean | The AllowCamera parameter specifies whether the mobile phone's camera is allowed. | - |
| AllowConsumerEmail | Write | Boolean | The AllowConsumerEmail parameter specifies whether the mobile phone user can configure a personal email account on the mobile phone. | - |
| AllowDesktopSync | Write | Boolean | The AllowDesktopSync parameter specifies whether the mobile phone can synchronize with a desktop computer through a cable. | - |
| AllowExternalDeviceManagement | Write | Boolean | The AllowExternalDeviceManagement parameter specifies whether an external device management program is allowed to manage the mobile phone. | - |
| AllowGooglePushNotifications | Write | Boolean | The AllowGooglePushNotifications parameter controls whether the user can receive push notifications from Google for Outlook on the web for devices. | - |
| AllowHTMLEmail | Write | Boolean | The AllowHTMLEmail parameter specifies whether HTML email is enabled on the mobile phone. | - |
| AllowInternetSharing | Write | Boolean | The AllowInternetSharing parameter specifies whether the mobile phone can be used as a modem to connect a computer to the Internet. | - |
| AllowIrDA | Write | Boolean | The AllowIrDA parameter specifies whether infrared connections are allowed to the mobile phone. | - |
| AllowMobileOTAUpdate | Write | Boolean | The AllowMobileOTAUpdate parameter specifies whether the Exchange ActiveSync mailbox policy can be sent to the mobile phone over a cellular data connection. | - |
| AllowMicrosoftPushNotifications | Write | Boolean | The AllowMicrosoftPushNotifications parameter specifies whether push notifications are enabled on the mobile device. | - |
| AllowNonProvisionableDevices | Write | Boolean | The AllowNonProvisionableDevices parameter specifies whether all mobile phones can synchronize with the server running Exchange. | - |
| AllowPOPIMAPEmail | Write | Boolean | The AllowPOPIMAPEmail parameter specifies whether the user can configure a POP3 or IMAP4 email account on the mobile phone. | - |
| AllowRemoteDesktop | Write | Boolean | The AllowRemoteDesktop parameter specifies whether the mobile phone can initiate a remote desktop connection. | - |
| AllowSimplePassword | Write | Boolean | The AllowSimplePassword parameter specifies whether a simple device password is allowed. A simple device password is a password that has a specific pattern, such as 1111 or 1234. | - |
| AllowSMIMEEncryptionAlgorithmNegotiation | Write | String | The AllowSMIMEEncryptionAlgorithmNegotiation parameter specifies whether the messaging application on the mobile device can negotiate the encryption algorithm if a recipient's certificate doesn't support the specified encryption algorithm. | `AllowAnyAlgorithmNegotiation`, `BlockNegotiation`, `OnlyStrongAlgorithmNegotiation` |
| AllowSMIMESoftCerts | Write | Boolean | The AllowSMIMESoftCerts parameter specifies whether S/MIME software certificates are allowed. | - |
| AllowStorageCard | Write | Boolean | The AllowStorageCard parameter specifies whether the mobile phone can access information stored on a storage card. | - |
| AllowTextMessaging | Write | Boolean | The AllowTextMessaging parameter specifies whether text messaging is allowed from the mobile phone. | - |
| AllowUnsignedApplications | Write | Boolean | The AllowUnsignedApplications parameter specifies whether unsigned applications can be installed on the mobile phone. | - |
| AllowUnsignedInstallationPackages | Write | Boolean | The AllowUnsignedInstallationPackages parameter specifies whether unsigned installation packages can be executed on the mobile phone. | - |
| AllowWiFi | Write | Boolean | The AllowWiFi parameter specifies whether wireless Internet access is allowed on the mobile phone. | - |
| AlphanumericPasswordRequired | Write | Boolean | The AlphanumericPasswordRequired parameter specifies whether the password for the mobile phone must be alphanumeric. | - |
| ApprovedApplicationList | Write | StringArray\[\] | The ApprovedApplicationList parameter specifies a list of approved applications for the mobile phone. | - |
| AttachmentsEnabled | Write | Boolean | The AttachmentsEnabled parameter specifies whether attachments can be downloaded. | - |
| DeviceEncryptionEnabled | Write | Boolean | The DeviceEncryptionEnabled parameter specifies whether encryption is enabled. | - |
| DevicePolicyRefreshInterval | Write | String | The DevicePolicyRefreshInterval parameter specifies how often the policy is sent from the server to the mobile phone. | - |
| IrmEnabled | Write | Boolean | The IrmEnabled parameter specifies whether Information Rights Management \(IRM\) is enabled for the mailbox policy. | - |
| IsDefault | Write | Boolean | The IsDefault parameter specifies whether this policy is the default Mobile Device mailbox policy. | - |
| MaxAttachmentSize | Write | String | The MaxAttachmentSize parameter specifies the maximum size of attachments that can be downloaded to the mobile phone. | - |
| MaxCalendarAgeFilter | Write | String | The MaxCalendarAgeFilter parameter specifies the maximum range of calendar days that can be synchronized to the device. | `All`, `TwoWeeks`, `OneMonth`, `ThreeMonths`, `SixMonths` |
| MaxEmailAgeFilter | Write | String | The MaxEmailAgeFilter parameter specifies the maximum number of days of email items to synchronize to the mobile phone. | `All`, `OneDay`, `ThreeDays`, `OneWeek`, `TwoWeeks`, `OneMonth` |
| MaxEmailBodyTruncationSize | Write | String | The MaxEmailBodyTruncationSize parameter specifies the maximum size at which email messages are truncated when synchronized to the mobile phone. The value is specified in kilobytes \(KB\). | - |
| MaxEmailHTMLBodyTruncationSize | Write | String | The MaxEmailHTMLBodyTruncationSize parameter specifies the maximum size at which HTML-formatted email messages are synchronized to the mobile phone. The value is specified in KB. | - |
| MaxInactivityTimeLock | Write | String | The MaxInactivityTimeDeviceLock parameter specifies the length of time that the mobile phone can be inactive before the password is required to reactivate it. | - |
| MaxPasswordFailedAttempts | Write | String | The MaxPasswordFailedAttempts parameter specifies the number of attempts a user can make to enter the correct password for the mobile phone. You can enter any number from 4 through 16 or the value Unlimited. | - |
| MinPasswordComplexCharacters | Write | String | The MinPasswordComplexCharacters parameter specifies the character sets that are required in the password of the mobile device. | - |
| MinPasswordLength | Write | String | The MinPasswordLength parameter specifies the minimum number of characters in the mobile device password. | - |
| PasswordEnabled | Write | Boolean | The PasswordEnabled parameter specifies whether a password is required on the mobile device. | - |
| PasswordExpiration | Write | String | The PasswordExpiration parameter specifies how long a password can be used on a mobile device before the user is forced to change the password. | - |
| PasswordHistory | Write | String | The PasswordHistory parameter specifies the number of unique new passwords that need to be created on the mobile device before an old password can be reused. | - |
| PasswordRecoveryEnabled | Write | Boolean | The PasswordRecoveryEnabled parameter specifies whether the recovery password for the mobile device is stored in Exchange. | - |
| RequireDeviceEncryption | Write | Boolean | The RequireDeviceEncryption parameter specifies whether encryption is required on the mobile device. | - |
| RequireEncryptedSMIMEMessages | Write | Boolean | The RequireEncryptedSMIMEMessages parameter specifies whether the mobile device must send encrypted S/MIME messages. | - |
| RequireEncryptionSMIMEAlgorithm | Write | String | The RequireEncryptionSMIMEAlgorithm parameter specifies the algorithm that's required to encrypt S/MIME messages on a mobile device. | `DES`, `TripleDES`, `RC240bit`, `RC264bit`, `RC2128bit` |
| RequireManualSyncWhenRoaming | Write | Boolean | The RequireSignedSMIMEAlgorithm parameter specifies the algorithm that's used to sign S/MIME messages on the mobile device. | - |
| RequireSignedSMIMEAlgorithm | Write | String | The RequireSignedSMIMEAlgorithm parameter specifies the algorithm that's used to sign S/MIME messages on the mobile device. | `SHA1`, `MD5` |
| RequireSignedSMIMEMessages | Write | Boolean | The RequireSignedSMIMEMessages parameter specifies whether the mobile device must send signed S/MIME messages. | - |
| RequireStorageCardEncryption | Write | Boolean | The RequireStorageCardEncryption parameter specifies whether storage card encryption is required on the mobile device. | - |
| UnapprovedInROMApplicationList | Write | StringArray\[\] | The UnapprovedInROMApplicationList parameter specifies a list of applications that can't be run in ROM on the mobile device. | - |
| UNCAccessEnabled | Write | Boolean | The UNCAccessEnabled parameter specifies whether access to Microsoft Windows file shares is enabled from the mobile device. | - |
| WSSAccessEnabled | Write | Boolean | The WSSAccessEnabled parameter specifies whether access to Microsoft Windows SharePoint Services is enabled from the mobile device. | - |
| Ensure | Write | String | Specify if the Mobile Device Mailbox Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Recipient Policies, View-Only Recipients, Mail Recipient Creation, View-Only Configuration, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## omeConfiguration resource type

### Description

Create a new OME Configuration policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the OME Configuration policy that you want to modify. | - |
| BackgroundColor | Write | String | The BackgroundColor parameter specifies the background color | - |
| DisclaimerText | Write | String | The DisclaimerText parameter specifies the disclaimer text in the email that contains the encrypted message | - |
| EmailText | Write | String | The EmailText parameter specifies the default text that accompanies encrypted email messages. | - |
| ExternalMailExpiryInDays | Write | UInt32 | The ExternalMailExpiryInDays parameter specifies the number of days that the encrypted message is available to external recipients in the Microsoft 365 portal. A valid value is an integer from 0 to 730. | - |
| IntroductionText | Write | String | The IntroductionText parameter specifies the default text that accompanies encrypted email messages. | - |
| OTPEnabled | Write | Boolean | The OTPEnabled parameter specifies whether to allow recipients to use a one-time passcode to view encrypted messages. | - |
| PortalText | Write | String | The PortalText parameter specifies the text that appears at the top of the encrypted email viewing portal. | - |
| PrivacyStatementUrl | Write | String | The PrivacyStatementUrl parameter specifies the Privacy Statement link in the encrypted email notification message. | - |
| ReadButtonText | Write | String | The ReadButtonText parameter specifies the text that appears on the 'Read the message' button. | - |
| SocialIdSignIn | Write | Boolean | The SocialIdSignIn parameter specifies whether a user is allowed to view an encrypted message in the Microsoft 365 admin center using their own social network id \(Google, Yahoo, and Microsoft account\). | - |
| Ensure | Write | String | Specifies if this Outbound connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Compliance Admin, Security Admin, Data Loss Prevention, Transport Rules, Information Rights Management, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## onPremisesOrganization resource type

### Description

This resource configures On-Premises Organization in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the identity of the on-premises organization object. | - |
| HybridDomains | Write | StringArray\[\] | The HybridDomains parameter specifies the domains that are configured in the hybrid deployment between an Office 365 tenant and an on-premises Exchange organization. The domains specified in this parameter must match the domains listed in the HybridConfiguration Active Directory object for the on-premises Exchange organization configured by the Hybrid Configuration wizard. | - |
| InboundConnector | Write | String | The InboundConnector parameter specifies the name of the inbound connector configured on the Microsoft Exchange Online Protection \(EOP\) service for a hybrid deployment configured with an on-premises Exchange organization. | - |
| OutboundConnector | Write | String | The OutboundConnector parameter specifies the name of the outbound connector configured on the EOP service for a hybrid deployment configured with an on-premises Exchange organization. | - |
| OrganizationName | Write | String | The OrganizationName parameter specifies the Active Directory object name of the on-premises Exchange organization. | - |
| OrganizationGuid | Write | String | The OrganizationGuid parameter specifies the globally unique identifier \(GUID\) of the on-premises Exchange organization object in the Office 365 tenant. | - |
| OrganizationRelationship | Write | String | The OrganizationRelationship parameter specifies the organization relationship configured by the Hybrid Configuration wizard on the Office 365 tenant as part of a hybrid deployment with an on-premises Exchange organization. This organization relationship defines the federated sharing features enabled on the Office 365 tenant. | - |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| Ensure | Write | String | Specify if the On-Premises Organization should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Remote and Accepted Domains, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## organizationConfig resource type

### Description

This resource configures the Exchange Online organization-wide settings.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| ActivityBasedAuthenticationTimeoutEnabled | Write | Boolean | The ActivityBasedAuthenticationTimeoutEnabled parameter specifies whether the timed logoff feature is enabled. The default value is $true | - |
| ActivityBasedAuthenticationTimeoutInterval | Write | String | The ActivityBasedAuthenticationTimeoutInterval parameter specifies the time span for logoff. You enter this value as a time span: hh:mm:ss where hh = hours, mm = minutes and ss = seconds. Valid values for this parameter are from 00:05:00 to 08:00:00 \(5 minutes to 8 hours\). The default value is 06:00:00 \(6 hours\). | - |
| ActivityBasedAuthenticationTimeoutWithSingleSignOnEnabled | Write | Boolean | The ActivityBasedAuthenticationTimeoutWithSingleSignOnEnabled parameter specifies whether to keep single sign-on enabled. The default value is $true. | - |
| AppsForOfficeEnabled | Write | Boolean | The AppsForOfficeEnabled parameter specifies whether to enable apps for Outlook features. By default, the parameter is set to $true. If the flag is set to $false, no new apps can be activated for any user in the organization. | - |
| AsyncSendEnabled | Write | Boolean | The AsyncSendEnabled parameter specifies whether to enable or disable async send in Outlook on the web. | - |
| AuditDisabled | Write | Boolean | The AuditDisabled parameter specifies whether to disable or enable mailbox auditing for the organization. | - |
| AutodiscoverPartialDirSync | Write | Boolean | Setting this parameter to $true will cause unknown users to be redirected to the on-premises endpoint and will allow on-premises users to discover their mailbox automatically. | - |
| AutoExpandingArchive | Write | Boolean | The AutoExpandingArchive switch enables the unlimited archiving feature \(called auto-expanding archiving\) in an Exchange Online organization. You don't need to specify a value with this switch. | - |
| BlockMoveMessagesForGroupFolders | Write | Boolean | No description available for BlockMoveMessagesForGroupFolders | - |
| BookingsAddressEntryRestricted | Write | Boolean | The BookingsAddressEntryRestricted parameter specifies whether addresses can be collected from Bookings customers. | - |
| BookingsAuthEnabled | Write | Boolean | The BookingsAuthEnabled parameter specifies whether to enforce authentication to access all published Bookings pages. | - |
| BookingsBlockedWordsEnabled | Write | Boolean | No description available for BookingsBlockedWordsEnabled | - |
| BookingsCreationOfCustomQuestionsRestricted | Write | Boolean | The BookingsCreationOfCustomQuestionsRestricted parameter specifies whether Bookings admins can add custom questions. | - |
| BookingsEnabled | Write | Boolean | The BookingsEnabled parameter specifies whether to enable Microsoft Bookings in an organization. | - |
| BookingsExposureOfStaffDetailsRestricted | Write | Boolean | The BookingsExposureOfStaffDetailsRestricted parameter specifies whether the attributes of internal Bookings staff members are visible to external Bookings customers. | - |
| BookingsMembershipApprovalRequired | Write | Boolean | The BookingsMembershipApprovalRequired parameter enables a membership approval requirement when new staff members are added to Bookings calendars. | - |
| BookingsNamingPolicyEnabled | Write | Boolean | No description available for BookingsNamingPolicyEnabled | - |
| BookingsNamingPolicyPrefix | Write | String | No description available for BookingsNamingPolicyPrefix | - |
| BookingsNamingPolicyPrefixEnabled | Write | Boolean | No description available for BookingsNamingPolicyPrefixEnabled | - |
| BookingsNamingPolicySuffix | Write | String | No description available for BookingsNamingPolicySuffix | - |
| BookingsNamingPolicySuffixEnabled | Write | Boolean | No description available for BookingsNamingPolicySuffixEnabled | - |
| BookingsNotesEntryRestricted | Write | Boolean | The BookingsNotesEntryRestricted parameter specifies whether appointment notes can be collected from Bookings customers. | - |
| BookingsPaymentsEnabled | Write | Boolean | The BookingsPaymentsEnabled parameter specifies whether to enable online payment node inside Bookings. | - |
| BookingsPhoneNumberEntryRestricted | Write | Boolean | The BookingsPhoneNumberEntryRestricted parameter specifies whether phone numbers can be collected from Bookings customers. | - |
| BookingsSearchEngineIndexDisabled | Write | Boolean | No description available for BookingsSearchEngineIndexDisabled | - |
| BookingsSmsMicrosoftEnabled | Write | Boolean | No description available for BookingsSmsMicrosoftEnabled | - |
| BookingsSocialSharingRestricted | Write | Boolean | The BookingsSocialSharingRestricted parameter allows you to control whether, or not, your users can see social sharing options inside Bookings. | - |
| ByteEncoderTypeFor7BitCharsets | Write | UInt32 | The ByteEncoderTypeFor7BitCharsets parameter specifies the 7-bit transfer encoding method for MIME format for messages sent to this remote domain. | - |
| ComplianceMLBgdCrawlEnabled | Write | Boolean | No description available for ComplianceMLBgdCrawlEnabled | - |
| ConnectorsActionableMessagesEnabled | Write | Boolean | The ConnectorsActionableMessagesEnabled parameter specifies whether to enable or disable actionable buttons in messages \(connector cards\) from connected apps on Outlook on the web. | - |
| ConnectorsEnabled | Write | Boolean | The ConnectorsEnabled parameter specifies whether to enable or disable all connected apps in organization. | - |
| ConnectorsEnabledForOutlook | Write | Boolean | The ConnectorsEnabledForOutlook parameter specifies whether to enable or disable connected apps in Outlook on the web. | - |
| ConnectorsEnabledForSharepoint | Write | Boolean | The ConnectorsEnabledForSharepoint parameter specifies whether to enable or disable connected apps on Sharepoint. | - |
| ConnectorsEnabledForTeams | Write | Boolean | The ConnectorsEnabledForTeams parameter specifies whether to enable or disable connected apps on Teams. | - |
| ConnectorsEnabledForYammer | Write | Boolean | The ConnectorsEnabledForYammer parameter specifies whether to enable or disable connected apps on Yammer. | - |
| CustomerLockboxEnabled | Write | Boolean | Enable Customer Lockbox. | - |
| DefaultAuthenticationPolicy | Write | String | The DefaultAuthenticationPolicy parameter specifies the authentication policy that's used for the whole organization. You can use any value that uniquely identifies the policy. | - |
| DefaultGroupAccessType | Write | String | The DefaultGroupAccessType parameter specifies the default access type for Office 365 groups. | `Private`, `Public` |
| DefaultMinutesToReduceLongEventsBy | Write | UInt32 | The DefaultMinutesToReduceLongEventsBy parameter specifies the number of minutes to reduce calendar events by if the events are 60 minutes or longer. | - |
| DefaultMinutesToReduceShortEventsBy | Write | UInt32 | The DefaultMinutesToReduceShortEventsBy parameter specifies the number of minutes to reduce calendar events by if the events are less than 60 minutes long. | - |
| DefaultPublicFolderAgeLimit | Write | String | The DefaultPublicFolderAgeLimit parameter specifies the default age limit for the contents of public folders across the entire organization. Content in a public folder is automatically deleted when this age limit is exceeded. This attribute applies to all public folders in the organization that don't have their own AgeLimit setting. To specify a value, enter it as a time span: dd.hh:mm:ss where d = days, h = hours, m = minutes, and s = seconds. Or, enter the value $null. The default value is blank \($null\). | - |
| DefaultPublicFolderDeletedItemRetention | Write | String | The DefaultPublicFolderDeletedItemRetention parameter specifies the default value of the length of time to retain deleted items for public folders across the entire organization. This attribute applies to all public folders in the organization that don't have their own RetainDeletedItemsFor attribute set. | - |
| DefaultPublicFolderIssueWarningQuota | Write | String | The DefaultPublicFolderIssueWarningQuota parameter specifies the default value across the entire organization for the public folder size at which a warning message is sent to this folder's owners, warning that the public folder is almost full. This attribute applies to all public folders within the organization that don't have their own warning quota attribute set. The default value of this attribute is unlimited. The valid input range for this parameter is from 0 through 2199023254529 bytes\(2 TB\). If you enter a value of unlimited, no size limit is imposed on the public folder. | - |
| DefaultPublicFolderMaxItemSize | Write | String | The DefaultPublicFolderMaxItemSize parameter specifies the default maximum size for posted items within public folders across the entire organization. Items larger than the value of the DefaultPublicFolderMaxItemSize parameter are rejected. This attribute applies to all public folders within the organization that don't have their own MaxItemSize attribute set. The default value of this attribute is unlimited. | - |
| DefaultPublicFolderMovedItemRetention | Write | String | The DefaultPublicFolderMovedItemRetention parameter specifies how long items that have been moved between mailboxes are kept in the source mailbox for recovery purposes before being removed by the Public Folder Assistant. | - |
| DefaultPublicFolderProhibitPostQuota | Write | String | The DefaultPublicFolderProhibitPostQuota parameter specifies the size of a public folder at which users are notified that the public folder is full. Users can't post to a folder whose size is larger than the DefaultPublicFolderProhibitPostQuota parameter value. The default value of this attribute is unlimited. | - |
| DirectReportsGroupAutoCreationEnabled | Write | Boolean | The DirectReportsGroupAutoCreationEnabled parameter specifies whether to enable or disable the automatic creation of direct report Office 365 groups. | - |
| DisablePlusAddressInRecipients | Write | Boolean | The DisablePlusAddressInRecipients parameter specifies whether to enable or disable plus addressing \(also known as subaddressing\) for Exchange Online mailboxes. | - |
| DistributionGroupDefaultOU | Write | String | The DistributionGroupDefaultOU parameter specifies the container where distribution groups are created by default. | - |
| DistributionGroupNameBlockedWordsList | Write | StringArray\[\] | The DistributionGroupNameBlockedWordsList parameter specifies words that can't be included in the names of distribution groups. Separate multiple values with commas. | - |
| DistributionGroupNamingPolicy | Write | String | The DistributionGroupNamingPolicy parameter specifies the template applied to the name of distribution groups that are created in the organization. You can enforce that a prefix or suffix be applied to all distribution groups. Prefixes and suffixes can be either a string or an attribute, and you can combine strings and attributes. | - |
| ElcProcessingDisabled | Write | Boolean | The ElcProcessingDisabled parameter specifies whether to enable or disable the processing of mailboxes by the Managed Folder Assistant. | - |
| EnableOutlookEvents | Write | Boolean | The EnableOutlookEvents parameter specifies whether Outlook or Outlook on the web automatically discovers events from email messages and adds them to user calendars. | - |
| EndUserDLUpgradeFlowsDisabled | Write | Boolean | The EndUserDLUpgradeFlowsDisabled parameter specifies whether to prevent users from upgrading their own distribution groups to Office 365 groups in an Exchange Online organization. | - |
| EwsAllowEntourage | Write | Boolean | The EwsAllowEntourage parameter specifies whether to enable or disable Entourage 2008 to access Exchange Web Services \(EWS\) for the entire organization. | - |
| EwsAllowList | Write | StringArray\[\] | The EwsAllowList parameter specifies the applications that are allowed to access EWS or REST when the EwsApplicationAccessPolicy parameter is set to EwsAllowList. Other applications that aren't specified by this parameter aren't allowed to access EWS or REST. You identify the application by its user agent string value. Wildcard characters \(\*\) are supported. | - |
| EwsAllowMacOutlook | Write | Boolean | The EwsAllowMacOutlook parameter enables or disables access to mailboxes by Outlook for Mac clients that use Exchange Web Services \(for example, Outlook for Mac 2011 or later\). | - |
| EwsAllowOutlook | Write | Boolean | The EwsAllowOutlook parameter enables or disables access to mailboxes by Outlook clients that use Exchange Web Services. Outlook uses Exchange Web Services for free/busy, out-of-office settings, and calendar sharing. | - |
| EwsApplicationAccessPolicy | Write | String | The EwsApplicationAccessPolicy parameter specifies the client applications that have access to EWS and REST. | `EnforceAllowList`, `EnforceBlockList` |
| EwsBlockList | Write | StringArray\[\] | The EwsBlockList parameter specifies the applications that aren't allowed to access EWS or REST when the EwsApplicationAccessPolicy parameter is set to EnforceBlockList. All other applications that aren't specified by this parameter are allowed to access EWS or REST. You identify the application by its user agent string value. Wildcard characters \(\*\) are supported. | - |
| EwsEnabled | Write | Boolean | The EwsEnabled parameter specifies whether to globally enable or disable EWS access for the entire organization, regardless of what application is making the request. | - |
| ExchangeNotificationEnabled | Write | Boolean | The ExchangeNotificationEnabled parameter enables or disables Exchange notifications sent to administrators regarding their organizations. Valid input for this parameter is $true or $false. | - |
| ExchangeNotificationRecipients | Write | StringArray\[\] | The ExchangeNotificationRecipients parameter specifies the recipients for Exchange notifications sent to administrators regarding their organizations. If the ExchangeNotificationEnabled parameter is set to $false, no notification messages are sent. Be sure to enclose values that contain spaces in quotation marks and separate multiple values with commas. If this parameter isn't set, Exchange notifications are sent to all administrators. | - |
| FindTimeAttendeeAuthenticationEnabled | Write | Boolean | The FindTimeAttendeeAuthenticationEnabled parameter controls whether attendees are required to verify their identity in meeting polls using the FindTime Outlook add-in. | - |
| FindTimeAutoScheduleDisabled | Write | Boolean | The FindTimeAutoScheduleDisabled parameter controls automatically scheduling the meeting once a consensus is reached in meeting polls using the FindTime Outlook add-in. | - |
| FindTimeLockPollForAttendeesEnabled | Write | Boolean | The FindTimeLockPollForAttendeesEnabled controls whether the Lock poll for attendees setting is managed by the organization. | - |
| FindTimeOnlineMeetingOptionDisabled | Write | Boolean | The FindTimeOnlineMeetingOptionDisabled parameter controls the availability of the Online meeting checkbox for Teams in meeting polls using the FindTime Outlook add-in. | - |
| FocusedInboxOn | Write | Boolean | The FocusedInboxOn parameter enables or disables Focused Inbox for the organization. | - |
| HierarchicalAddressBookRoot | Write | String | The HierarchicalAddressBookRoot parameter specifies the user, contact, or group to be used as the root organization for a hierarchical address book in the Exchange organization. You can use any value that uniquely identifies the recipient. | - |
| IPListBlocked | Write | StringArray\[\] | The IPListBlocked parameter specifies the blocked IP addresses that aren't allowed to connect to Exchange Online organization. These settings affect client connections that use Basic authentication where on-premises Active Directory Federation Services \(ADFS\) servers federate authentication with Microsoft Entra. The new settings might take up to 4 hours to fully propagate across the service. | - |
| IsGroupFoldersAndRulesEnabled | Write | Boolean | No description available for IsGroupFoldersAndRulesEnabled | - |
| IsGroupMemberAllowedToEditContent | Write | Boolean | No description available for IsGroupMemberAllowedToEditContent | - |
| LeanPopoutEnabled | Write | Boolean | The LeanPopoutEnabled parameter specifies whether to enable faster loading of pop-out messages in Outlook on the web for Internet Explorer and Microsoft Edge. | - |
| LinkPreviewEnabled | Write | Boolean | The LinkPreviewEnabled parameter specifies whether link preview of URLs in email messages is allowed for the organization. | - |
| MailTipsAllTipsEnabled | Write | Boolean | The MailTipsAllTipsEnabled parameter specifies whether MailTips are enabled. The default value is $true. | - |
| MailTipsExternalRecipientsTipsEnabled | Write | Boolean | The MailTipsExternalRecipientsTipsEnabled parameter specifies whether MailTips for external recipients are enabled. The default value is $false. | - |
| MailTipsGroupMetricsEnabled | Write | Boolean | The MailTipsGroupMetricsEnabled parameter specifies whether MailTips that rely on group metrics data are enabled. The default value is $true. | - |
| MailTipsLargeAudienceThreshold | Write | UInt32 | The MailTipsLargeAudienceThreshold parameter specifies what a large audience is. The default value is 25. | - |
| MailTipsMailboxSourcedTipsEnabled | Write | Boolean | The MailTipsMailboxSourcedTipsEnabled parameter specifies whether MailTips that rely on mailbox data \(out-of-office or full mailbox\) are enabled. | - |
| MaskClientIpInReceivedHeadersEnabled | Write | Boolean | No description available for MaskClientIpInReceivedHeadersEnabled. | - |
| MatchSenderOrganizerProperties | Write | Boolean | No description available for MatchSenderOrganizerProperties. | - |
| MessageHighlightsEnabled | Write | Boolean | No description available for MessageHighlightsEnabled. | - |
| MessageRecallEnabled | Write | Boolean | The MessageRecallEnabled parameter enables or disables the message recall feature in the organization. | - |
| MessageRemindersEnabled | Write | Boolean | The MessageRemindersEnabled parameter enables or disables the message reminders feature in the organization. | - |
| MobileAppEducationEnabled | Write | Boolean | The MobileAppEducationEnabled specifies whether to show or hide the Outlook for iOS and Android education reminder in Outlook on the web. | - |
| OAuth2ClientProfileEnabled | Write | Boolean | The OAuth2ClientProfileEnabled parameter enables or disables modern authentication in the Exchange organization. | - |
| OnlineMeetingsByDefaultEnabled | Write | Boolean | The OnlineMeetingsByDefaultEnabled parameter specifies whether to set all meetings as Teams by default during meeting creation. | - |
| OutlookGifPickerDisabled | Write | Boolean | The OutlookGifPickerDisabled parameter disables the GIF Search \(powered by Bing\) feature that's built into the Compose page in Outlook on the web. | - |
| OutlookMobileGCCRestrictionsEnabled | Write | Boolean | The OutlookMobileGCCRestrictionsEnabled parameter specifies whether to enable or disable features within Outlook for iOS and Android that are not FedRAMP compliant for Office 365 US Government Community Cloud \(GCC\) customers. | - |
| OutlookPayEnabled | Write | Boolean | The OutlookPayEnabled parameter enables or disables Payments in Outlook in the Office 365 organization. | - |
| OutlookTextPredictionDisabled | Write | Boolean | No description available for OutlookTextPredictionDisabled. | - |
| PublicComputersDetectionEnabled | Write | Boolean | The PublicComputersDetectionEnabled parameter specifies whether Outlook on the web will detect when a user signs from a public or private computer or network, and then enforces the attachment handling settings from public networks. The default is $false. However, if you set this parameter to $true, Outlook on the web will determine if the user is signing in from a public computer, and all public attachment handling rules will be applied and enforced. | - |
| PublicFoldersEnabled | Write | String | The PublicFoldersEnabled parameter specifies how public folders are deployed in your organization. | `None`, `Local`, `Remote` |
| PublicFolderShowClientControl | Write | Boolean | The PublicFolderShowClientControl parameter enables or disables access to public folders in Microsoft Outlook. | - |
| ReadTrackingEnabled | Write | Boolean | The ReadTrackingEnabled parameter specifies whether the tracking for read status for messages in an organization is enabled. The default value is $false. | - |
| RecallReadMessagesEnabled | Write | Boolean | No description available for RecallReadMessagesEnabled. | - |
| RemotePublicFolderMailboxes | Write | StringArray\[\] | The RemotePublicFolderMailboxes parameter specifies the identities of the public folder objects \(represented as mail user objects locally\) corresponding to the public folder mailboxes created in the remote forest. The public folder values set here are used only if the public folder deployment is a remote deployment. | - |
| SendFromAliasEnabled | Write | Boolean | The SendFromAliasEnabled parameter allows mailbox users to send messages using aliases \(proxy addresses\). It does this by disabling the rewriting of aliases to their primary SMTP address. This change is implemented in the Exchange Online service | - |
| SharedDomainEmailAddressFlowEnabled | Write | Boolean | No description available for SharedDomainEmailAddressFlowEnabled. | - |
| ShortenEventScopeDefault | Write | String | The ShortenEventScopeDefault parameter specifies whether calendar events start late or end early in the organization. | - |
| SiteMailboxCreationURL | Write | String | The SiteMailboxCreationURL parameter specifies the URL that's used to create site mailboxes. Site mailboxes improve collaboration and user productivity by allowing access to both SharePoint documents and Exchange email in Outlook 2013 or later. | - |
| SmtpActionableMessagesEnabled | Write | Boolean | The SmtpActionableMessagesEnabled parameter specifies whether to enable or disable action buttons in email messages in Outlook on the web. | - |
| VisibleMeetingUpdateProperties | Write | String | The VisibleMeetingUpdateProperties parameter specifies whether meeting message updates will be auto-processed on behalf of attendees. Auto-processed updates are applied to the attendee's calendar item, and then the meeting message is moved to the deleted items. The attendee never sees the update in their inbox, but their calendar is updated. | - |
| WebPushNotificationsDisabled | Write | Boolean | The WebPushNotificationsDisabled parameter specifies whether to enable or disable Web Push Notifications in Outlook on the Web. This feature provides web push notifications which appear on a user's desktop while the user is not using Outlook on the Web. This brings awareness of incoming messages while they are working elsewhere on their computer. | - |
| WebSuggestedRepliesDisabled | Write | Boolean | The WebSuggestedRepliesDisabled parameter specifies whether to enable or disable Suggested Replies in Outlook on the web. This feature provides suggested replies to emails so users can easily and quickly respond to messages. | - |
| WorkspaceTenantEnabled | Write | Boolean | The WorkspaceTenantEnabled parameter enables or disables workspace booking in the organization. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Mail Tips, View-Only Configuration, Organization Configuration, Federated Sharing, Public Folders, Team Mailboxes, Compliance Admin, Recipient Policies, Remote and Accepted Domains, Distribution Groups, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## organizationRelationship resource type

### Description

This resource configures the Organization Relationship in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the organization relationship. The maximum length is 64 characters. | - |
| ArchiveAccessEnabled | Write | Boolean | The ArchiveAccessEnabled parameter specifies whether the organization relationship has been configured to provide remote archive access. | - |
| DeliveryReportEnabled | Write | Boolean | The DeliveryReportEnabled parameter specifies whether Delivery Reports should be shared over the organization relationship. | - |
| DomainNames | Write | StringArray\[\] | The DomainNames parameter specifies the SMTP domains of the external organization. You can specify multiple domains separated by commas. | - |
| Enabled | Write | Boolean | The Enabled parameter specifies whether to enable the organization relationship. | - |
| FreeBusyAccessEnabled | Write | Boolean | The FreeBusyAccessEnabled parameter specifies whether the organization relationship should be used to retrieve free/busy information from the external organization. | - |
| FreeBusyAccessLevel | Write | String | The FreeBusyAccessLevel parameter specifies the maximum amount of detail returned to the requesting organization. Valid values are: None, AvailabilityOnly or LimitedDetails | `None`, `AvailabilityOnly`, `LimitedDetails` |
| FreeBusyAccessScope | Write | String | The FreeBusyAccessScope parameter specifies a mail-enabled security group in the internal organization that contains users whose free/busy information is accessible by an external organization. You can use any value that uniquely identifies the group. | - |
| MailboxMoveEnabled | Write | Boolean | The MailboxMoveEnabled parameter specifies whether the organization relationship enables moving mailboxes to or from the external organization. | - |
| MailboxMoveCapability | Write | String | The MailboxMoveCapability parameter is used in cross-tenant mailbox migrations. | `Inbound`, `Outbound`, `RemoteInbound`, `RemoteOutbound`, `None` |
| MailboxMovePublishedScopes | Write | StringArray\[\] | The MailboxMovePublishedScopes parameter is used in cross-tenant mailbox migrations to specify the mail-enabled security groups whose members are allowed to migrate. | - |
| MailTipsAccessEnabled | Write | Boolean | The MailTipsAccessEnabled parameter specifies whether MailTips for users in this organization are returned over this organization relationship. | - |
| MailTipsAccessLevel | Write | String | The MailTipsAccessLevel parameter specifies the level of MailTips data externally shared over this organization relationship. This parameter can have the following values: All, Limited, None | `None`, `All`, `Limited` |
| MailTipsAccessScope | Write | String | The MailTipsAccessScope parameter specifies a mail-enabled security group in the internal organization that contains users whose free/busy information is accessible by an external organization. You can use any value that uniquely identifies the group. | - |
| OauthApplicationId | Write | String | The OAuthApplicationId is used in cross-tenant mailbox migrations to specify the application ID of the mailbox migration app that you consented to. | - |
| OrganizationContact | Write | String | The OrganizationContact parameter specifies the email address that can be used to contact the external organization \(for example, administrator@fourthcoffee.com\). | - |
| PhotosEnabled | Write | Boolean | The PhotosEnabled parameter specifies whether photos for users in the internal organization are returned over the organization relationship. | - |
| TargetApplicationUri | Write | String | The TargetApplicationUri parameter specifies the target Uniform Resource Identifier \(URI\) of the external organization. The TargetApplicationUri parameter is specified by Exchange when requesting a delegated token to retrieve free and busy information, for example, mail.contoso.com. | - |
| TargetAutodiscoverEpr | Write | String | The TargetAutodiscoverEpr parameter specifies the Autodiscover URL of Exchange Web Services for the external organization. Exchange uses Autodiscover to automatically detect the correct Exchangeserver endpoint to use for external requests. | - |
| TargetOwaURL | Write | String | The TargetOwaURL parameter specifies the Outlook on the web \(formerly Outlook Web App\) URL of the external organization that's defined in the organization relationship. It's used for Outlook on the web redirection in a cross-premise Exchange scenario. Configuring this attribute enables users in the organization to use their current Outlook on the web URL to access Outlook on the web in the external organization. | - |
| TargetSharingEpr | Write | String | The TargetSharingEpr parameter specifies the URL of the target Exchange Web Services for the external organization. | - |
| Ensure | Write | String | Specify if the OrganizationRelationship should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Federated Sharing, Organization Transport Settings, View-Only Configuration, Mail Tips, Message Tracking, Organization Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## outboundConnector resource type

### Description

Create a new Inbound connector in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the outbound connector that you want to modify. | - |
| Enabled | Write | Boolean | Specifies whether connector is enabled. | - |
| UseMXRecord | Write | Boolean | Specifies whether connector should use MXRecords for target resolution. | - |
| Comment | Write | String | The Comment parameter specifies an optional comment. | - |
| ConnectorSource | Write | String | The ConnectorSource parameter specifies how the connector is created. DO NOT CHANGE THIS! | `Default`, `Migrated`, `HybridWizard` |
| ConnectorType | Write | String | The ConnectorType parameter specifies a category for the domains that are serviced by the connector. | `Partner`, `OnPremises` |
| RecipientDomains | Write | StringArray\[\] | The RecipientDomains parameter specifies the domain that the Outbound connector routes mail to. You can specify multiple domains separated by commas. | - |
| SmartHosts | Write | StringArray\[\] | The SmartHosts parameter specifies the smart hosts the Outbound connector uses to route mail. This parameter is required if you set the UseMxRecord parameter to $false and must be specified on the same command line. | - |
| TlsDomain | Write | String | The TlsDomain parameter specifies the domain name that the Outbound connector uses to verify the FQDN of the target certificate when establishing a TLS secured connection. This parameter is only used if the TlsSettings parameter is set to DomainValidation. Valid input for the TlsDomain parameter is an SMTP domain. You can use a wildcard character to specify all subdomains of a specified domain, as shown in the following example: *.contoso.com. However, you can't embed a wildcard character, as shown in the following example: domain.*.contoso.com | - |
| TlsSettings | Write | String | The TlsSettings parameter specifies the TLS authentication level that's used for outbound TLS connections established by this Outbound connector. | `EncryptionOnly`, `CertificateValidation`, `DomainValidation` |
| IsTransportRuleScoped | Write | Boolean | The IsTransportRuleScoped parameter specifies whether the Outbound connector is associated with a transport rule \(also known as a mail flow rule\). | - |
| RouteAllMessagesViaOnPremises | Write | Boolean | The RouteAllMessagesViaOnPremises parameter specifies that all messages serviced by this connector are first routed through the on-premises messaging system \(Centralized mailrouting\). | - |
| CloudServicesMailEnabled | Write | Boolean | The CloudServicesMailEnabled parameter specifies whether the connector is used for hybrid mail flow between an on-premises Exchange environment and Microsoft Office 365. Specifically, this parameter controls how certain internal X-MS-Exchange-Organization-\* message headers are handled in messages that are sent between accepted domains in the on-premises and cloud organizations. These headers are collectively known as cross-premises headers. DO NOT USE MANUALLY! | - |
| AllAcceptedDomains | Write | Boolean | The AllAcceptedDomains parameter specifies whether the Outbound connector is used in hybrid organizations where message recipients are in accepted domains of the cloud-based organization. | - |
| SenderRewritingEnabled | Write | Boolean | The SenderRewritingEnabled parameter specifies that all messages that normally qualify for SRS rewriting are rewritten for routing through the on-premises email system. | - |
| TestMode | Write | Boolean | The TestMode parameter specifies whether you want to enabled or disable test mode for the Outbound connector. | - |
| ValidationRecipients | Write | StringArray\[\] | The ValidationRecipients parameter specifies the email addresses of the validation recipients for the Outbound connector. You can specify multiple email addresses separated by commas. | - |
| Ensure | Write | String | Specifies if this Outbound connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Remote and Accepted Domains, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## owaMailboxPolicy resource type

### Description

This resource configures OWA Mailbox Policies in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name for the policy. The maximum length is 64 characters. | - |
| AccountTransferEnabled | Write | Boolean | The AccountTransferEnabled parameter specifies whether to enable or disable QR code sign-in. By default, QR code sign-in is enabled. | - |
| ActionForUnknownFileAndMIMETypes | Write | String | The ActionForUnknownFileAndMIMETypes parameter specifies how to handle file types that aren't specified in the Allow, Block, and Force Save lists for file types and MIME types | `Allow`, `ForceSave`, `Block` |
| ActiveSyncIntegrationEnabled | Write | Boolean | The ActiveSyncIntegrationEnabled parameter specifies whether to enable or disable Exchange ActiveSync settings in Outlook on the web. | - |
| AdditionalAccountsEnabled | Write | Boolean | No description available. | - |
| AdditionalStorageProvidersAvailable | Write | Boolean | The AdditionalStorageProvidersAvailable parameter specifies whether to allow additional storage providers \(for example, Box, Dropbox, Facebook, Google Drive, Egnyte, personal OneDrive\) attachments in Outlook on the web. | - |
| AllAddressListsEnabled | Write | Boolean | The AllAddressListsEnabled parameter specifies which address lists are available in Outlook on the web. | - |
| AllowCopyContactsToDeviceAddressBook | Write | Boolean | The AllowCopyContactsToDeviceAddressBook parameter specifies whether users can copy the contents of their Contacts folder to a mobile device's native address book when using Outlook on the web for devices. | - |
| AllowedFileTypes | Write | StringArray\[\] | The AllowedFileTypes parameter specifies the attachment file types \(file extensions\) that can be saved locally or viewed from Outlook on the web. | - |
| AllowedMimeTypes | Write | StringArray\[\] | The AllowedMimeTypes parameter specifies the MIME extensions of attachments that allow the attachments to be saved locally or viewed from Outlook on the web. | - |
| BlockedFileTypes | Write | StringArray\[\] | The BlockedFileTypes parameter specifies a list of attachment file types \(file extensions\) that can't be saved locally or viewed from Outlook on the web. | - |
| BlockedMimeTypes | Write | StringArray\[\] | The BlockedMimeTypes parameter specifies MIME extensions in attachments that prevent the attachments from being saved locally or viewed from Outlook on the web. | - |
| BookingsMailboxCreationEnabled | Write | Boolean | No description available. | - |
| ChangeSettingsAccountEnabled | Write | Boolean | No description available. | - |
| ClassicAttachmentsEnabled | Write | Boolean | The ClassicAttachmentsEnabled parameter specifies whether users can attach local files as regular email attachments in Outlook on the web. | - |
| ConditionalAccessPolicy | Write | String | The ConditionalAccessPolicy parameter specifies the Outlook on the Web Policy for limited access. For this feature to work properly, you also need to configure a Conditional Access policy in the Microsoft Entra Portal. | `Off`, `ReadOnly`, `ReadOnlyPlusAttachmentsBlocked` |
| DefaultTheme | Write | String | The DefaultTheme parameter specifies the default theme that's used in Outlook on the web when the user hasn't selected a theme. The default value is blank \($null\). | - |
| DirectFileAccessOnPrivateComputersEnabled | Write | Boolean | The DirectFileAccessOnPrivateComputersEnabled parameter specifies the left-click options for attachments in Outlook on the web for private computer sessions. | - |
| DirectFileAccessOnPublicComputersEnabled | Write | Boolean | The DirectFileAccessOnPrivateComputersEnabled parameter specifies the left-click options for attachments in Outlook on the web for public computer sessions. | - |
| DisableFacebook | Write | Boolean | The DisableFacebook switch specifies whether users can synchronize their Facebook contacts to their Contacts folder in Outlook on the web. By default, Facebook integration is enabled. | - |
| DisplayPhotosEnabled | Write | Boolean | The DisplayPhotosEnabled parameter specifies whether users see sender photos in Outlook on the web. | - |
| ExplicitLogonEnabled | Write | Boolean | The ExplicitLogonEnabled parameter specifies whether to allow a user to open someone else's mailbox in Outlook on the web \(provided that user has permissions to the mailbox\). | - |
| ExternalImageProxyEnabled | Write | Boolean | The ExternalImageProxyEnabled parameter specifies whether to load all external images through the Outlook external image proxy. | - |
| ExternalSPMySiteHostURL | Write | String | The ExternalSPMySiteHostURL specifies the My Site Host URL for external users. | - |
| FeedbackEnabled | Write | Boolean | The FeedbackEnabled parameter specifies whether to enable or disable inline feedback surveys in Outlook on the web. | - |
| ForceSaveAttachmentFilteringEnabled | Write | Boolean | The ForceSaveAttachmentFilteringEnabled parameter specifies whether files are filtered before they can be saved from Outlook on the web. | - |
| ForceSaveFileTypes | Write | StringArray\[\] | The ForceSaveFileTypes parameter specifies the attachment file types \(file extensions\) that can only be saved from Outlook on the web \(not opened\). | - |
| ForceSaveMimeTypes | Write | StringArray\[\] | The ForceSaveMimeTypes parameter specifies the MIME extensions in attachments that only allow the attachments to be saved locally \(not opened\). | - |
| ForceWacViewingFirstOnPrivateComputers | Write | Boolean | The ForceWacViewingFirstOnPrivateComputers parameter specifies whether private computers must first preview an Office file as a web page in Office Online Server \(formerly known as Office Web Apps Server and Web Access Companion Server\) before opening the file in the local application. | - |
| ForceWacViewingFirstOnPublicComputers | Write | Boolean | The ForceWacViewingFirstOnPublicComputers parameter specifies whether public computers must first preview an Office file as a web page in Office Online Server before opening the file in the local application. | - |
| FreCardsEnabled | Write | Boolean | The FreCardsEnabled parameter specifies whether the theme, signature, and phone cards are available in Outlook on the web. | - |
| GlobalAddressListEnabled | Write | Boolean | The GlobalAddressListEnabled parameter specifies whether the global address list is available in Outlook on the web. | - |
| GroupCreationEnabled | Write | Boolean | The GroupCreationEnabled parameter specifies whether Office 365 group creation is available in Outlook on the web. | - |
| InstantMessagingEnabled | Write | Boolean | The InstantMessagingEnabled parameter specifies whether instant messaging is available in Outlook on the web. | - |
| InstantMessagingType | Write | String | The InstantMessagingType parameter specifies the type of instant messaging provider in Outlook on the web. | `None`, `Ocs` |
| InterestingCalendarsEnabled | Write | Boolean | The InterestingCalendarsEnabled parameter specifies whether interesting calendars are available in Outlook on the web. | - |
| InternalSPMySiteHostURL | Write | String | The InternalSPMySiteHostURL specifies the My Site Host URL for internal users. | - |
| IRMEnabled | Write | Boolean | The IRMEnabled parameter specifies whether Information Rights Management \(IRM\) features are available in Outlook on the web. | - |
| ItemsToOtherAccountsEnabled | Write | Boolean | No description available. | - |
| IsDefault | Write | Boolean | The IsDefault switch specifies whether the Outlook on the web policy is the default policy that's used to configure the Outlook on the web settings for new mailboxes. | - |
| JournalEnabled | Write | Boolean | The JournalEnabled parameter specifies whether the Journal folder is available in Outlook on the web. | - |
| LocalEventsEnabled | Write | Boolean | The LocalEventsEnabled parameter specifies whether local events calendars are available in Outlook on the web. | - |
| LogonAndErrorLanguage | Write | SInt32 | The LogonAndErrorLanguage parameter specifies the language that used in Outlook on the web for forms-based authentication and for error messages when a user's current language setting can't be read. A valid value is a supported Microsoft Windows Language Code Identifier \(LCID\). For example, 1033 is US English. | - |
| MessagePreviewsDisabled | Write | Boolean | No description available. | - |
| NotesEnabled | Write | Boolean | The NotesEnabled parameter specifies whether the Notes folder is available in Outlook on the web. | - |
| NpsSurveysEnabled | Write | Boolean | The NpsSurveysEnabled parameter specifies whether to enable or disable the Net Promoter Score \(NPS\) survey in Outlook on the web. The survey allows uses to rate Outlook on the web on a scale of 1 to 5, and to provide feedback and suggested improvements in free text. | - |
| OneWinNativeOutlookEnabled | Write | Boolean | The OneWinNativeOutlookEnabled parameter controls the availability of the new Outlook for Windows App. | - |
| OrganizationEnabled | Write | Boolean | When the OrganizationEnabled parameter is set to $false, the Automatic Reply option doesn't include external and internal options, the address book doesn't show the organization hierarchy, and the Resources tab in Calendar forms is disabled. | - |
| OnSendAddinsEnabled | Write | Boolean | The OnSendAddinsEnabled parameter specifies whether to enable or disable on send add-ins in Outlook on the web \(add-ins that support events when a user clicks Send\). | - |
| OutboundCharset | Write | String | The OutboundCharset parameter specifies the character set that's used for outgoing messages in Outlook on the web. | `AutoDetect`, `AlwaysUTF8`, `UserLanguageChoice` |
| OutlookBetaToggleEnabled | Write | Boolean | The OutlookBetaToggleEnabled parameter specifies whether to enable or disable the Outlook on the web Preview toggle. The Preview toggle allows users to try the new Outlook on the web experience. | - |
| OWALightEnabled | Write | Boolean | The OWALightEnabled parameter controls the availability of the light version of Outlook on the web. | - |
| PersonalAccountsEnabled | Write | Boolean | No description available. | - |
| PersonalAccountCalendarsEnabled | Write | Boolean | The PersonalAccountCalendarsEnabled parameter specifies whether to allow users to connect to their personal Outlook.com or Google Calendar in Outlook on the web. | - |
| PhoneticSupportEnabled | Write | Boolean | The PhoneticSupportEnabled parameter specifies phonetically spelled entries in the address book. This parameter is available for use in Japan. | - |
| PlacesEnabled | Write | Boolean | The PlacesEnabled parameter specifies whether to enable or disable Places in Outlook on the web. Places lets users search, share, and map location details by using Bing. | - |
| PremiumClientEnabled | Write | Boolean | The PremiumClientEnabled parameter controls the availability of the full version of Outlook Web App. | - |
| PrintWithoutDownloadEnabled | Write | Boolean | The PrintWithoutDownloadEnabled specifies whether to allow printing of supported files without downloading the attachment in Outlook on the web. | - |
| ProjectMocaEnabled | Write | Boolean | The ProjectMocaEnabled parameter enables or disables access to Project Moca in Outlook on the web. | - |
| PublicFoldersEnabled | Write | Boolean | The PublicFoldersEnabled parameter specifies whether a user can browse or read items in public folders in Outlook Web App. | - |
| RecoverDeletedItemsEnabled | Write | Boolean | The RecoverDeletedItemsEnabled parameter specifies whether a user can use Outlook Web App to view, recover, or delete permanently items that have been deleted from the Deleted Items folder. | - |
| ReferenceAttachmentsEnabled | Write | Boolean | The ReferenceAttachmentsEnabled parameter specifies whether users can attach files from the cloud as linked attachments in Outlook on the web. | - |
| RemindersAndNotificationsEnabled | Write | Boolean | The RemindersAndNotificationsEnabled parameter specifies whether notifications and reminders are enabled in Outlook on the web. | - |
| ReportJunkEmailEnabled | Write | Boolean | The ReportJunkEmailEnabled parameter specifies whether users can report messages to Microsoft or unsubscribe from messages in Outlook on the web. | - |
| RulesEnabled | Write | Boolean | The RulesEnabled parameter specifies whether a user can view, create, or modify server-side rules in Outlook on the web. | - |
| SatisfactionEnabled | Write | Boolean | The SatisfactionEnabled parameter specifies whether to enable or disable the satisfaction survey. | - |
| SaveAttachmentsToCloudEnabled | Write | Boolean | The SaveAttachmentsToCloudEnabled parameter specifies whether users can save regular email attachments to the cloud. | - |
| SearchFoldersEnabled | Write | Boolean | The SearchFoldersEnabled parameter specifies whether Search Folders are available in Outlook on the web. | - |
| SetPhotoEnabled | Write | Boolean | The SetPhotoEnabled parameter specifies whether users can add, change, and remove their sender photo in Outlook on the web. | - |
| SetPhotoURL | Write | String | The SetPhotoURL parameter controls where users go to select their photo. Note that you can't specify a URL that contains one or more picture files, as there's no mechanism to copy a URL photo to the properties of the users' Exchange Online mailboxes. | - |
| ShowOnlineArchiveEnabled | Write | Boolean | No description available. | - |
| SignaturesEnabled | Write | Boolean | The SignaturesEnabled parameter specifies whether to enable or disable the use of signatures in Outlook on the web. | - |
| SkipCreateUnifiedGroupCustomSharepointClassification | Write | Boolean | The SkipCreateUnifiedGroupCustomSharepointClassification parameter specifies whether to skip a custom SharePoint page during the creation of Office 365 Groups in Outlook web app. | - |
| TeamSnapCalendarsEnabled | Write | Boolean | The TeamSnapCalendarsEnabled parameter specifies whether to allow users to connect to their personal TeamSnap calendars in Outlook on the web. | - |
| TextMessagingEnabled | Write | Boolean | The TextMessagingEnabled parameter specifies whether users can send and receive text messages in Outlook on the web. | - |
| ThemeSelectionEnabled | Write | Boolean | The ThemeSelectionEnabled parameter specifies whether users can change the theme in Outlook on the web. | - |
| UMIntegrationEnabled | Write | Boolean | The UMIntegrationEnabled parameter specifies whether Unified Messaging \(UM\) integration is enabled in Outlook on the web. | - |
| UseGB18030 | Write | Boolean | The UseGB18030 parameter specifies whether to use the GB18030 character set instead of GB2312 in Outlook on the web. | - |
| UseISO885915 | Write | Boolean | The UseISO885915 parameter specifies whether to use the character set ISO8859-15 instead of ISO8859-1 in Outlook on the web. | - |
| UserVoiceEnabled | Write | Boolean | The UserVoiceEnabled parameter specifies whether to enable or disable Outlook UserVoice in Outlook on the web. Outlook UserVoice is a customer feedback area that's available in Office 365. | - |
| WacEditingEnabled | Write | Boolean | The WacEditingEnabled parameter specifies whether to enable or disable editing documents in Outlook on the web by using Office Online Server \(formerly known as Office Web Apps Server and Web Access Companion Server\). | - |
| WacExternalServicesEnabled | Write | Boolean | The WacExternalServicesEnabled parameter specifies whether to enable or disable external services when viewing documents in Outlook on the web \(for example, machine translation\) by using Office Online Server. | - |
| WacOMEXEnabled | Write | Boolean | The WacOMEXEnabled parameter specifies whether to enable or disable apps for Outlook in Outlook on the web in Office Online Server. | - |
| WacViewingOnPrivateComputersEnabled | Write | Boolean | The WacViewingOnPrivateComputersEnabled parameter specifies whether to enable or disable web viewing of supported Office documents private computer sessions in Office Online Server \(formerly known as Office Web Apps Server and Web Access Companion Server\). By default, all Outlook on the web sessions are considered to be on private computers. | - |
| WacViewingOnPublicComputersEnabled | Write | Boolean | The WacViewingOnPublicComputersEnabled parameter specifies whether to enable or disable web viewing of supported Office documents in public computer sessions in Office Online Server. | - |
| WeatherEnabled | Write | Boolean | The WeatherEnabled parameter specifies whether to enable or disable weather information in the calendar in Outlook on the web. | - |
| WebPartsFrameOptionsType | Write | String | The WebPartsFrameOptionsType parameter specifies what sources can access web parts in IFRAME or FRAME elements in Outlook on the web. | `None`, `SameOrigin`, `Deny` |
| Ensure | Write | String | Specify if the OWA Mailbox Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Recipient Policies, View-Only Configuration, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## partnerApplication resource type

### Description

This resource configures Partner Applications in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies a new name for the partner application. | - |
| ApplicationIdentifier | Write | String | The ApplicationIdentifier parameter specifies a unique application identifier for the partner application that uses an authorization server. | - |
| AcceptSecurityIdentifierInformation | Write | Boolean | The AcceptSecurityIdentifierInformation parameter specifies whether Exchange should accept security identifiers \(SIDs\) from another trusted Active Directory forest for the partner application. | - |
| AccountType | Write | String | The AccountType parameter specifies the type of Microsoft account that's required for the partner application. | `OrganizationalAccount`, `ConsumerAccount` |
| Enabled | Write | Boolean | The Enabled parameter specifies whether the partner application is enabled. | - |
| LinkedAccount | Write | String | The LinkedAccount parameter specifies a linked Active Directory user account for the application. | - |
| Ensure | Write | String | Specify if the Partner Application should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Organization Client Access, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## perimeterConfiguration resource type

### Description

Modify the perimeter Configuration policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| GatewayIPAddresses | Write | StringArray\[\] | Use the GatewayIPAddresses parameter to create or modify a list of gateway server IP addresses to add to IP safelists. | - |
| Ensure | Write | String | Specifies if this Outbound connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- View-Only Configuration, Organization Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## place resource type

### Description

This resource configures a place in Exchange Online \(e.g., room\).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the room mailbox that you want to modify. You can use any value that uniquely identifies the room. | - |
| DisplayName | Write | String | The display name of the place. | - |
| AudioDeviceName | Write | String | The AudioDeviceName parameter specifies the name of the audio device in the room. If the value contains spaces, enclose the value in quotation marks. | - |
| Building | Write | String | The Building parameter specifies the building name or building number that the room is in. If the value contains spaces, enclose the value in quotation marks. | - |
| Capacity | Write | UInt32 | The Capacity parameter specifies the capacity of the room. A valid value is an integer. | - |
| City | Write | String | The City parameter specifies the room's city. If the value contains spaces, enclose the value in quotation marks. | - |
| CountryOrRegion | Write | String | The CountryOrRegion parameter specifies the room's country or region. A valid value is a valid ISO 3166-1 two-letter country/region code \(for example, AU for Australia\) or the corresponding friendly name for the country/region \(which might be different from the official ISO 3166 Maintenance Agency short name\). | - |
| Desks | Write | StringArray\[\] | N/A | - |
| DisplayDeviceName | Write | String | The DisplayDeviceName parameter specifies the name of the display device in the room. If the value contains spaces, enclose the value in quotation marks. | - |
| Floor | Write | String | The Floor parameter specifies the floor number that the room is on. | - |
| FloorLabel | Write | String | The FloorLabel parameter specifies a descriptive label for the floor that the room is on. If the value contains spaces, enclose the value in quotation marks. | - |
| GeoCoordinates | Write | String | The GeoCoordinates parameter specifies the room's location in latitude, longitude and \(optionally\) altitude coordinates. | - |
| IsWheelChairAccessible | Write | Boolean | The IsWheelChairAccessible parameter specifies whether the room is wheelchair accessible. | - |
| Label | Write | String | The Label parameter specifies a descriptive label for the room \(for example, a number or name\). If the value contains spaces, enclose the value in quotation marks. | - |
| MTREnabled | Write | Boolean | The MTREnabled parameter identifies the room as configured with a Microsoft Teams room system. You can add Teams room systems as audio sources in Teams meetings that involve the room. | - |
| ParentId | Write | String | The ParentId parameter specifies the ID of a Place in the parent location hierarchy in Microsoft Places. | - |
| ParentType | Write | String | The ParentType parameter specifies the parent type of the ParentId in Microsoft Places. Valid values are: Floor, Section | `Floor`, `Section`, `None` |
| Phone | Write | String | The Phone parameter specifies the room's telephone number. | - |
| PostalCode | Write | String | The PostalCode parameter specifies the room's postal code. | - |
| State | Write | String | The State parameter specifies the room's state or province. | - |
| Street | Write | String | The Street parameter specifies the room's physical address. | - |
| Tags | Write | StringArray\[\] | The Tags parameter specifies additional features of the room \(for example, details like the type of view or furniture type\). | - |
| VideoDeviceName | Write | String | The VideoDeviceName parameter specifies the name of the video device in the room. If the value contains spaces, enclose the value in quotation marks. | - |
| Ensure | Write | String | Specifies if this Outbound connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Remote and Accepted Domains, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## policyTipConfig resource type

### Description

This resource configures Policy Tips in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the custom Policy Tip you want to modify. | - |
| Value | Write | String | The Value parameter specifies the text that's displayed by the Policy Tip. | - |
| Ensure | Write | String | Specify if the Policy Tip Config should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Data Loss Prevention, View-Only Configuration

##### Role Groups

- Organization Management, Compliance Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## quarantinePolicy resource type

### Description

Create or modify a EXOQuarantinePolicy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the QuarantinePolicy you want to modify. | - |
| EndUserQuarantinePermissionsValue | Write | UInt32 | The EndUserQuarantinePermissionsValue parameter specifies the end-user permissions for the quarantine policy. | - |
| ESNEnabled | Write | Boolean | The ESNEnabled parameter specifies whether to enable quarantine notifications \(formerly known as end-user spam notifications\) for the policy. | - |
| MultiLanguageCustomDisclaimer | Write | StringArray\[\] | The MultiLanguageCustomDisclaimer parameter specifies the custom disclaimer text to use near the bottom of quarantine notifications. | - |
| MultiLanguageSenderName | Write | StringArray\[\] | The MultiLanguageSenderName parameter specifies the email sender's display name to use in quarantine notifications. | - |
| MultiLanguageSetting | Write | StringArray\[\] | The MultiLanguageSetting parameter specifies the language of quarantine notifications. | - |
| OrganizationBrandingEnabled | Write | Boolean | The OrganizationBrandingEnabled parameter enables or disables organization branding in the end-user quarantine notification messages. | - |
| Ensure | Write | String | Specifies if this QuarantinePolicy should exist. | `Present`, `Absent` |
| EndUserSpamNotificationFrequency | Write | String | The EndUserSpamNotificationFrequency parameter species how often quarantine notifications are sent to users. Valid values are: 04:00:00 \(4 hours\),1.00:00:00 \(1 day\),7.00:00:00 \(7 days\) | - |
| QuarantinePolicyType | Write | String | The QuarantinePolicyType parameter filters the results by the specified quarantine policy type. Valid values are: QuarantinePolicy, GlobalQuarantinePolicy | - |
| EndUserSpamNotificationFrequencyInDays | Write | String | This parameter is reserved for internal Microsoft use. | - |
| CustomDisclaimer | Write | String | This parameter is reserved for internal Microsoft use. | - |
| EndUserSpamNotificationCustomFromAddress | Write | String | The EndUserSpamNotificationCustomFromAddress specifies the email address of an existing internal sender to use as the sender for quarantine notifications. To set this parameter back to the default email address quarantine@messaging.microsoft.com, use the value $null. | - |
| EsnCustomSubject | Write | StringArray\[\] | The EsnCustomSubject parameter specifies the text to use in the Subject field of quarantine notifications.This setting is available only in the built-in quarantine policy named DefaultGlobalTag that controls global quarantine policy settings. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## recipientPermission resource type

### Description

This resource allows users to retrieve Office 365 Recipient Permissions.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The mailbox the permission should be given on. | - |
| Trustee | Key | String | The account to give the permission to. | - |
| AccessRights | Write | StringArray\[\] | The access rights granted to the account. Only 'SendAs' is supported. | - |
| Ensure | Write | String | Present ensures the group exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Mail Enabled Public Folders, MyName, Public Folders, Compliance Admin, User Options, Message Tracking, View-Only Recipients, Role Management, Legal Hold, Audit Logs, Retention Management, Distribution Groups, Move Mailboxes, Information Rights Management, Mail Recipient Creation, Reset Password, View-Only Audit Logs, Mail Recipients, Mailbox Search, UM Mailboxes, Security Group Creation and Membership, Mailbox Import Export, MyMailboxDelegation, MyDisplayName

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## remoteDomain resource type

### Description

This resource configures the Remote Email Domains in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specify the Identity for the RemoteDomain. | - |
| DomainName | Write | String | The DomainName parameter specifies the SMTP domain that you want to establish as a remote domain. A valid value is an SMTP domain \(for example, contoso.com\). The maximum length is 256 characters. | - |
| Ensure | Write | String | Specify if the RemoteDomain should exist or not. | `Present`, `Absent` |
| AllowedOOFType | Write | String | The AllowedOOFType parameter specifies the type of automatic replies or out-of-office \(also known as OOF\) notifications than can be sent to recipients in the remote domain. Valid values are: External, ExternalLegacy, InternalLegacy or None | `External`, `ExternalLegacy`, `InternalLegacy`, `None` |
| AutoForwardEnabled | Write | Boolean | The AutoForwardEnabled parameter specifies whether to allow messages that are auto-forwarded by client email programs in your organization. | - |
| AutoReplyEnabled | Write | Boolean | The AutoReplyEnabled parameter specifies whether to allow messages that are automatic replies from client email programs in your organization \(for example, automatic reply messages that are generated by rules in Outlook\). | - |
| ByteEncoderTypeFor7BitCharsets | Write | String | The ByteEncoderTypeFor7BitCharsets parameter specifies the 7-bit transfer encoding method for MIME format for messages sent to this remote domain. | `Use7Bit`, `UseQP`, `UseBase64`, `UseQPHtmlDetectTextPlain`, `UseBase64HtmlDetectTextPlain`, `UseQPHtml7BitTextPlain`, `UseBase64Html7BitTextPlain`, `Undefined` |
| CharacterSet | Write | String | The CharacterSet parameter specifies a character set for MIME messages without defined character sets that are sent from your organization to recipients in the remote domain. | - |
| ContentType | Write | String | The ContentType parameter specifies the outbound message content type and formatting. | `MimeHtmlText`, `MimeText`, `MimeHtml` |
| DeliveryReportEnabled | Write | Boolean | The DeliveryReportEnabled parameter specifies whether to allow delivery reports from client software in your organization to recipients in the remote domain. | - |
| DisplaySenderName | Write | Boolean | The DisplaySenderName parameter specifies whether to show the sender's Display Name in the From email address for messages sent to recipients in the remote domain. | - |
| IsInternal | Write | Boolean | The IsInternal parameter specifies whether the recipients in the remote domain are considered to be internal recipients. | - |
| LineWrapSize | Write | String | The LineWrapSize parameter specifies the line-wrap size for messages to recipients in the remote domain. Valid values are an integer from 0 through 132 or the value to unlimited. The default value is unlimited. | - |
| MeetingForwardNotificationEnabled | Write | Boolean | The MeetingForwardNotificationEnabled parameter specifies whether to enable meeting forward notifications for recipients in the remote domain. | - |
| Name | Write | String | The Name parameter specifies a unique name for the remote domain object. The maximum length is 64 characters. If the value contains spaces, enclose the value in quotation marks. | - |
| NDREnabled | Write | Boolean | The NDREnabled parameter specifies whether to allow non-delivery reports \(also known NDRs or bounce messages\) from your organization to recipients in the remote domain. | - |
| NonMimeCharacterSet | Write | String | The NonMimeCharacterSet parameter specifies a character set for plain text messages without defined character sets that are sent from your organization to recipients in the remote domain. | - |
| PreferredInternetCodePageForShiftJis | Write | String | The PreferredInternetCodePageForShiftJis parameter specifies the specific code page to use for Shift JIS character encoding in messages that are sent to recipients in the remote domain. | `50220`, `50221`, `50222`, `Undefined` |
| RequiredCharsetCoverage | Write | SInt32 | The RequiredCharsetCoverage parameter specifies a percentage threshold for characters in a message that must match to apply your organization's preferred character set before switching to automatic character set detection. | - |
| TargetDeliveryDomain | Write | Boolean | The TargetDeliveryDomain parameter specifies whether the remote domain is used in cross-forest deployments to generate target email addresses for new mail users that represent users in the other organization \(for example, all mailboxes hosted on Exchange Online are represented as mail users in your on-premises organization\). | - |
| TNEFEnabled | Write | Boolean | The TNEFEnabled parameter specifies whether Transport Neutral Encapsulation Format \(TNEF\) message encoding is used on messages sent to the remote domain. | - |
| TrustedMailInboundEnabled | Write | Boolean | The TrustedMailInboundEnabled parameter specifies whether messages from senders in the remote domain are treated as trusted messages. | - |
| TrustedMailOutboundEnabled | Write | Boolean | The TrustedMailOutboundEnabled parameter specifies whether messages sent to recipients in the remote domain are treated as trusted messages. | - |
| UseSimpleDisplayName | Write | Boolean | The UseSimpleDisplayName parameter specifies whether the sender's simple display name is used for the From email address in messages sent to recipients in the remote domain. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Remote and Accepted Domains, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## reportSubmissionPolicy resource type

### Description

Create or modify an EXOReportSubmissionPolicy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Specifies the resource is a single instance, the value must be 'Yes'. | `Yes` |
| DisableQuarantineReportingOption | Write | Boolean | The DisableQuarantineReportingOption parameter allows or prevents users from reporting messages in quarantine. | - |
| EnableCustomNotificationSender | Write | Boolean | The EnableCustomNotificationSender parameter specifies whether a custom sender email address is used for result messages after an admin reviews and marks the reported messages as junk, not junk, or phishing. | - |
| EnableOrganizationBranding | Write | Boolean | The EnableOrganizationBranding parameter specifies whether to show the company logo in the footer of result messages that users receive after an admin reviews and marks the reported messages as junk, not junk, or phishing. | - |
| EnableReportToMicrosoft | Write | Boolean | The EnableReportToMicrosoft parameter specifies whether Microsoft integrated reporting experience is enabled or disabled. | - |
| EnableThirdPartyAddress | Write | Boolean | The EnableThirdPartyAddress parameter specifies whether you're using third-party reporting tools in Outlook instead of Microsoft tools to send messages to the reporting mailbox in Exchange Online. | - |
| EnableUserEmailNotification | Write | Boolean | The EnableUserEmailNotification parameter species whether users receive result messages after an admin reviews and marks the reported messages as junk, not junk, or phishing. | - |
| JunkReviewResultMessage | Write | String | The JunkReviewResultMessage parameter specifies the custom text to use in result messages after an admin reviews and marks the reported messages as junk. | - |
| NotJunkReviewResultMessage | Write | String | The NotJunkReviewResultMessage parameter specifies the custom text to use in result messages after an admin reviews and marks the reported messages as not junk. | - |
| NotificationFooterMessage | Write | String | The NotificationFooterMessage parameter specifies the custom footer text to use in email notifications after an admin reviews and marks the reported messages as junk, not junk, or phishing. | - |
| NotificationSenderAddress | Write | String | The NotificationSenderAddress parameter specifies the sender email address to use in result messages after an admin reviews and marks the reported messages as junk, not junk, or phishing. | - |
| PhishingReviewResultMessage | Write | String | The PhishingReviewResultMessage parameter specifies the custom text to use in result messages after an admin reviews and marks the reported messages as phishing. | - |
| PostSubmitMessage | Write | String | The PostSubmitMessage parameter specifies the custom pop-up message text to use in Outlook notifications after users report messages. | - |
| PostSubmitMessageEnabled | Write | Boolean | The PostSubmitMessageEnabled parameter enables or disables the pop-up Outlook notifications that users see after they report messages using Microsoft reporting tools. | - |
| PostSubmitMessageTitle | Write | String | The PostSubmitMessage parameter parameter specifies the custom pop-up message title to use in Outlook notifications after users report messages. | - |
| PreSubmitMessage | Write | String | The PreSubmitMessage parameter specifies the custom pop-up message text to use in Outlook notifications before users report messages. | - |
| PreSubmitMessageEnabled | Write | Boolean | The PreSubmitMessageEnabled parameter enables or disables the pop-up Outlook notifications that users see before they report messages using Microsoft reporting tools. | - |
| PreSubmitMessageTitle | Write | String | The PreSubmitMessage parameter parameter specifies the custom pop-up message title to use in Outlook notifications before users report messages. | - |
| ReportJunkAddresses | Write | StringArray\[\] | The ReportJunkAddresses parameter specifies the email address of the reporting mailbox in Exchange Online to receive user reported messages in reporting in Outlook using Microsoft or third-party reporting tools in Outlook. | - |
| ReportJunkToCustomizedAddress | Write | Boolean | The ReportJunkToCustomizedAddress parameter specifies whether to send user reported messages from Outlook \(using Microsoft or third-party reporting tools\) to the reporting mailbox as part of reporting in Outlook. | - |
| ReportNotJunkAddresses | Write | StringArray\[\] | The ReportNotJunkAddresses parameter specifies the email address of the reporting mailbox in Exchange Online to receive user reported messages in reporting in Outlook using Microsoft or third-party reporting tools in Outlook. | - |
| ReportNotJunkToCustomizedAddress | Write | Boolean | The ReportNotJunkToCustomizedAddress parameter specifies whether to send user reported messages from Outlook \(using Microsoft or third-party reporting tools\) to the reporting mailbox as part of reporting in Outlook. | - |
| ReportPhishAddresses | Write | StringArray\[\] | The ReportPhishAddresses parameter specifies the email address of the reporting mailbox in Exchange Online to receive user reported messages in reporting in Outlook using Microsoft or third-party reporting tools in Outlook. | - |
| ReportPhishToCustomizedAddress | Write | Boolean | The ReportPhishToCustomizedAddress parameter specifies whether to send user reported messages from Outlook \(using Microsoft or third-party reporting tools\) to the reporting mailbox as part of reporting in Outlook. | - |
| ThirdPartyReportAddresses | Write | StringArray\[\] | Use the ThirdPartyReportAddresses parameter to specify the email address of the reporting mailbox when you're using a third-party product for user submissions instead of reporting in Outlook. | - |
| Ensure | Write | String | Specifies if this report submission policy should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## reportSubmissionRule resource type

### Description

Create or modify an EXOReportSubmissionRule in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Specifies the resource is a single instance, the value must be 'Yes'. | `Yes` |
| Identity | Write | String | The Identity parameter specifies the report submission rule that you want to modify. | - |
| Comments | Write | String | The Comments parameter specifies informative comments for the rule, such as what the rule is used for or how it has changed over time. | - |
| SentTo | Write | StringArray\[\] | The SentTo parameter specifies the email address of the reporting mailbox in Exchange Online where user reported messages are sent. | - |
| Ensure | Write | String | Specifies if this report submission rule should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## resourceConfiguration resource type

### Description

Modify the resource Configuration policy in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| ResourcePropertySchema | Write | StringArray\[\] | The ResourcePropertySchema parameter specifies the custom resource property that you want to make available to room or equipment mailboxes. This parameter uses the syntax Room/<Text> or Equipment/<Text> where the <Text> value doesn't contain spaces. For example, Room/Whiteboard or Equipment/Van. | - |
| Ensure | Write | String | Specifies if this Outbound connector should exist. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Organization Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## roleAssignmentPolicy resource type

### Description

This resource configures Role Assignment Policies in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the new name of the assignment policy. The maximum length is 64 characters. | - |
| Description | Write | String | The Description parameter specifies the description that's displayed when the role assignment policy is viewed using the Get-RoleAssignmentPolicy cmdlet. | - |
| IsDefault | Write | Boolean | The IsDefault switch makes the assignment policy the default assignment policy. | - |
| Roles | Write | StringArray\[\] | The Roles parameter specifies the management roles to assign to the role assignment policy when it's created. | - |
| Ensure | Write | String | Specify if the Role Assignment Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Role Management, Mail Recipient Creation, View-Only Configuration, Mail Recipients

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## roleGroup resource type

### Description

This resource configures Role Groups in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the name of the role. The maximum length of the name is 64 characters. | - |
| Description | Write | String | The Description parameter specifies the description that's displayed when the role group is viewed using the Get-RoleGroup cmdlet. Enclose the description in quotation marks | - |
| Members | Write | StringArray\[\] | The Members parameter specifies the mailboxes or mail-enabled USGs to add as a member of the role group. You can identify the user or group by the name, DN, or primary SMTP address value. You can specify multiple members separated by commas \(Value1,Value2,...ValueN\). If the value contains spaces, enclose the value in quotation marks | - |
| Roles | Write | StringArray\[\] | The Roles parameter specifies the management roles to assign to the role group when it's created. If a role name contains spaces, enclose the name in quotation marks. If you want to assign more that one role, separate the role names with commas. | - |
| Ensure | Write | String | Specify if the Role Group should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Role Management, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## safeAttachmentPolicy resource type

### Description

This resource configures the settings of the Safe Attachments policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the SafeAttachmentpolicy that you want to modify. | - |
| Action | Write | String | The Action parameter specifies the action for the Safe Attachments policy. | `Block`, `Replace`, `Allow`, `DynamicDelivery` |
| ActionOnError | Write | Boolean | The ActionOnError parameter specifies the error handling option for Safe Attachments scanning \(what to do if scanning times out or an error occurs\). Valid values are: $true: The action specified by the Action parameter is applied to messages even when the attachments aren't successfully scanned. $false: The action specified by the Action parameter isn't applied to messages when the attachments aren't successfully scanned. This is the default value. | - |
| AdminDisplayName | Write | String | The AdminDisplayName parameter specifies a description for the policy. | - |
| Enable | Write | Boolean | Specify if this policy should be enabled. Default is $true. | - |
| QuarantineTag | Write | String | The QuarantineTag specifies the quarantine policy that's used on messages that are quarantined as malware by Safe Attachments. | - |
| Redirect | Write | Boolean | The Redirect parameter specifies whether to send detected malware attachments to another email address. Valid values are: $true: Malware attachments are sent to the email address specified by the RedirectAddress parameter. $false: Malware attachments aren't sent to another email address. This is the default value. | - |
| RedirectAddress | Write | String | The RedirectAddress parameter specifies the email address where detected malware attachments are sent when the Redirect parameter is set to the value $true. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## safeAttachmentRule resource type

### Description

This resource configures an Safe Attachment Rule in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the SafeAttachment rule that you want to modify. | - |
| SafeAttachmentPolicy | Required | String | The SafeAttachmentPolicy parameter specifies the name of the SafeAttachment policy that's associated with the SafeAttachment rule. | - |
| Enabled | Write | Boolean | Specify if this rule should be enabled. Default is $true. | - |
| Priority | Write | UInt32 | The Priority parameter specifies a priority value for the rule that determines the order of rule processing. A lower integer value indicates a higher priority, the value 0 is the highest priority, and rules can't have the same priority value. | - |
| Comments | Write | String | The Comments parameter specifies informative comments for the rule, such as what the rule is used for or how it has changed over time. The length of the comment can't exceed 1,024 characters. | - |
| ExceptIfRecipientDomainIs | Write | StringArray\[\] | The ExceptIfRecipientDomainIs parameter specifies an exception that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| ExceptIfSentTo | Write | StringArray\[\] | The ExceptIfSentTo parameter specifies an exception that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| ExceptIfSentToMemberOf | Write | StringArray\[\] | The ExceptIfSentToMemberOf parameter specifies an exception that looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |
| RecipientDomainIs | Write | StringArray\[\] | The RecipientDomainIs parameter specifies a condition that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| SentTo | Write | StringArray\[\] | The SentTo parameter specifies a condition that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| SentToMemberOf | Write | StringArray\[\] | The SentToMemberOf parameter looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## safeLinksPolicy resource type

### Description

This resource configures the settings of the SafeLinks policies in your cloud-based organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the SafeLinks policy that you want to modify. | - |
| Ensure | Write | String | Specify if this policy should exist or not. | `Present`, `Absent` |
| AdminDisplayName | Write | String | The AdminDisplayName parameter specifies a description for the policy. | - |
| AllowClickThrough | Write | Boolean | The AllowClickThrough parameter specifies whether to allow users to click through to the original URL on warning pages. | - |
| CustomNotificationText | Write | String | The custom notification text specifies the customized notification text to show to users. | - |
| DeliverMessageAfterScan | Write | Boolean | The DeliverMessageAfterScan parameter specifies whether to deliver email messages only after Safe Links scanning is complete. Valid values are: $true: Wait until Safe Links scanning is complete before delivering the message. $false: If Safe Links scanning can't complete, deliver the message anyway. This is the default value. | - |
| DoNotRewriteUrls | Write | StringArray\[\] | The DoNotRewriteUrls parameter specifies a URL that's skipped by Safe Links scanning. You can specify multiple values separated by commas. | - |
| EnableForInternalSenders | Write | Boolean | The EnableForInternalSenders parameter specifies whether the Safe Links policy is applied to messages sent between internal senders and internal recipients within the same Exchange Online organization. | - |
| EnableOrganizationBranding | Write | Boolean | The EnableOrganizationBranding parameter specifies whether your organization's logo is displayed on Safe Links warning and notification pages. | - |
| EnableSafeLinksForOffice | Write | Boolean | The EnableSafeLinksForOffice parameter specifies whether to enable Safe Links protection for supported Office desktop, mobile, or web apps. | - |
| EnableSafeLinksForTeams | Write | Boolean | The EnableSafeLinksForTeams parameter specifies whether Safe Links is enabled for Microsoft Teams. Valid values are: $true: Safe Links is enabled for Teams. If a protected user clicks a malicious link in a Teams conversation, group chat, or from channels, a warning page will appear in the default web browser. $false: Safe Links isn't enabled for Teams. This is the default value. | - |
| EnableSafeLinksForEmail | Write | Boolean | The EnableSafeLinksForEmail parameter specifies whether to enable Safe Links protection for email messages. Valid values are: $true: Safe Links is enabled for email. When a user clicks a link in an email, the link is checked by Safe Links. If the link is found to be malicious, a warning page appears in the default web browser. $false: Safe Links isn't enabled for email. This is the default value. | - |
| DisableUrlRewrite | Write | Boolean | The DisableUrlRewrite parameter specifies whether to rewrite \(wrap\) URLs in email messages. Valid values are: $true: URLs in messages are not rewritten, but messages are still scanned by Safe Links prior to delivery. Time of click checks on links are done using the Safe Links API in supported Outlook clients \(currently, Outlook for Windows and Outlook for Mac\). Typically, we don't recommend using this value. $false: URLs in messages are rewritten. API checks still occur on unwrapped URLs in supported clients if the user is in a valid Safe Links policy. This is the default value. | - |
| ScanUrls | Write | Boolean | The ScanUrls parameter specifies whether to enable or disable the scanning of links in email messages. Valid values are: $true: Scanning links in email messages is enabled. $false: Scanning links in email messages is disabled. This is the default value. | - |
| TrackClicks | Write | Boolean | The TrackClicks parameter specifies whether to track user clicks related to Safe Links protection of links. | - |
| UseTranslatedNotificationText | Write | Boolean | The UseTranslatedNotificationText specifies whether to use Microsoft Translator to automatically localize the custom notification text that you specified with the CustomNotificationText parameter. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## safeLinksRule resource type

### Description

This resource configures an SafeLinks Rule in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter specifies the name of the SafeLink rule that you want to modify. | - |
| Ensure | Write | String | Specify if this rule should exist or not. | `Present`, `Absent` |
| SafeLinksPolicy | Required | String | The SafeLinksPolicy parameter specifies the name of the SafeLink policy that's associated with the SafeLinksing rule. | - |
| Enabled | Write | Boolean | Specify if this rule should be enabled. Default is $true. | - |
| Priority | Write | UInt32 | The Priority parameter specifies a priority value for the rule that determines the order of rule processing. A lower integer value indicates a higher priority, the value 0 is the highest priority, and rules can't have the same priority value. | - |
| Comments | Write | String | The Comments parameter specifies informative comments for the rule, such as what the rule is used for or how it has changed over time. The length of the comment can't exceed 1,024 characters. | - |
| ExceptIfRecipientDomainIs | Write | StringArray\[\] | The ExceptIfRecipientDomainIs parameter specifies an exception that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| ExceptIfSentTo | Write | StringArray\[\] | The ExceptIfSentTo parameter specifies an exception that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| ExceptIfSentToMemberOf | Write | StringArray\[\] | The ExceptIfSentToMemberOf parameter specifies an exception that looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |
| RecipientDomainIs | Write | StringArray\[\] | The RecipientDomainIs parameter specifies a condition that looks for recipients with email address in the specified domains. You can specify multiple domains separated by commas. | - |
| SentTo | Write | StringArray\[\] | The SentTo parameter specifies a condition that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| SentToMemberOf | Write | StringArray\[\] | The SentToMemberOf parameter looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Transport Hygiene, Security Admin, View-Only Configuration, Security Reader

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## sharedMailbox resource type

### Description

This resource allows users to create Office 365 Shared Mailboxes.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The display name of the Shared Mailbox | - |
| Identity | Write | String | The unique identifier of the Shared Mailbox | - |
| PrimarySMTPAddress | Write | String | The primary email address of the Shared Mailbox | - |
| Alias | Write | String | The alias of the Shared Mailbox | - |
| EmailAddresses | Write | StringArray\[\] | The EmailAddresses parameter specifies all the email addresses \(proxy addresses\) for the Shared Mailbox | - |
| Ensure | Write | String | Present ensures the group exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Mail Enabled Public Folders, MyName, Public Folders, Compliance Admin, User Options, Message Tracking, View-Only Recipients, Role Management, Legal Hold, Audit Logs, Retention Management, Distribution Groups, Move Mailboxes, Information Rights Management, Mail Recipient Creation, Reset Password, View-Only Audit Logs, Mail Recipients, Mailbox Search, UM Mailboxes, Security Group Creation and Membership, Mailbox Import Export, MyMailboxDelegation, MyDisplayName

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## sharingPolicy resource type

### Description

This resource configures Sharing Policies in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the unique name of the sharing policy. The maximum length is 64 characters. | - |
| Default | Write | Boolean | The Default switch specifies that the sharing policy is the default sharing policy for all mailboxes. | - |
| Enabled | Write | Boolean | The Enabled parameter specifies whether to enable the sharing policy. Valid values for this parameter are $true or $false. | - |
| Domains | Write | StringArray\[\] | The Domains parameter specifies domains to which this policy applies and the sharing policy action. | - |
| Ensure | Write | String | Specify if the Sharing Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Federated Sharing, Mail Recipient Creation, View-Only Configuration

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## transportConfig resource type

### Description

This resource configures the Exchange Online transport settings.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Specifies the resource is a single instance, the value must be 'Yes'. | `Yes` |
| AddressBookPolicyRoutingEnabled | Write | Boolean | The AddressBookPolicyRoutingEnabled parameter controls how recipients are resolved in an organization that uses address book policies to create separate virtual organizations within the same Exchange organization. | - |
| AllowLegacyTLSClients | Write | Boolean | Allow legacy TLS clients | - |
| ClearCategories | Write | Boolean | The ClearCategories parameter keeps or removes Microsoft Outlook message categories during content conversion. | - |
| ConvertDisclaimerWrapperToEml | Write | Boolean | The ConvertDisclaimerWrapperToEml parameter specifies whether the original message will be added as a TNEF attachment or a regular EML attachment to a disclaimer. | - |
| DSNConversionMode | Write | String | The DSNConversionMode parameter controls how Exchange handles delivery status notifications that are generated by earlier versions of Exchange or other messaging systems. | - |
| ExternalDelayDsnEnabled | Write | Boolean | The ExternalDelayDsnEnabled parameter specifies whether a delay delivery status notification \(DSN\) message should be created for external messages that couldn't be immediately delivered. | - |
| ExternalDsnDefaultLanguage | Write | String | The ExternalDsnDefaultLanguage parameter specifies which Exchange server language should be used by default when you create external DSN messages. | - |
| ExternalDsnLanguageDetectionEnabled | Write | Boolean | The ExternalDsnLanguageDetectionEnabled parameter specifies whether the server should try to send an external DSN message in the same language as the original message that generated the notification. | - |
| ExternalDsnReportingAuthority | Write | String | The ExternalDsnReportingAuthority parameter specifies the domain in the machine-readable part of external DSN messages. | - |
| ExternalDsnSendHtml | Write | Boolean | The ExternalDsnSendHtml parameter specifies whether external DSN messages should be HTML or plain text. | - |
| ExternalPostmasterAddress | Write | String | The ExternalPostmasterAddress parameter specifies the email address in the From header field of an external DSN message. | - |
| HeaderPromotionModeSetting | Write | String | The HeaderPromotionModeSetting parameter specifies whether named properties are created for custom X-headers on messages received. | - |
| InternalDelayDsnEnabled | Write | Boolean | The InternalDelayDsnEnabled parameter specifies whether a delay DSN message should be created for messages sent to or from recipients or senders in the same Exchange organization that couldn't be immediately delivered. | - |
| InternalDsnDefaultLanguage | Write | String | The InternalDsnDefaultLanguage parameter specifies which Exchange server language should be used by default when you create internal DSN messages. | - |
| InternalDsnLanguageDetectionEnabled | Write | Boolean | The InternalDsnLanguageDetectionEnabled parameter specifies whether the server should try to send an internal DSN message in the same language as the original message that generated the notification. | - |
| InternalDsnReportingAuthority | Write | String | The InternalDsnReportingAuthority parameter specifies the domain in the machine-readable part of internal DSN messages. | - |
| InternalDsnSendHtml | Write | Boolean | The InternalDsnSendHtml parameter specifies whether internal DSN messages should be HTML or plain text. | - |
| JournalMessageExpirationDays | Write | SInt32 | The JournalMessageExpirationDays parameter extends the number of days that undeliverable journal reports are queued before they expire. | - |
| JournalingReportNdrTo | Write | String | The JournalingReportNdrTo parameter specifies the email address to which journal reports are sent if the journaling mailbox is unavailable. | - |
| MaxRecipientEnvelopeLimit | Write | String | The MaxRecipientEnvelopeLimit parameter specifies the maximum number of recipients in a message. | - |
| ReplyAllStormBlockDurationHours | Write | SInt32 | Reply all storm block duration hours. | - |
| ReplyAllStormDetectionMinimumRecipients | Write | SInt32 | Reply all storm detection minimum recipients. | - |
| ReplyAllStormDetectionMinimumReplies | Write | SInt32 | Reply all storm detection minimum replies. | - |
| ReplyAllStormProtectionEnabled | Write | Boolean | Reply all storm protection enabled. | - |
| Rfc2231EncodingEnabled | Write | Boolean | The Rfc2231EncodingEnabled parameter specifies whether the RFC 2231 encoding of MIME parameters for outbound messages is enabled in your organization. | - |
| SmtpClientAuthenticationDisabled | Write | Boolean | The SmtpClientAuthenticationDisabled parameter specifies whether to disable authenticated SMTP \(SMTP AUTH\) for the whole organization. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Organization Transport Settings, View-Only Configuration, Journaling

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## transportRule resource type

### Description

This resource configures Transport Rules in Exchange Online.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies the display name of the transport rule to be created. The maximum length is 64 characters. | - |
| ADComparisonAttribute | Write | String | This parameter specifies a condition or part of a condition for the rule. The name of the corresponding exception parameter starts with ExceptIf. | - |
| ADComparisonOperator | Write | String | This parameter specifies a condition or part of a condition for the rule. The name of the corresponding exception parameter starts with ExceptIf. | `Equal`, `NotEqual` |
| ActivationDate | Write | String | The ActivationDate parameter specifies when the rule starts processing messages. The rule won't take any action on messages until the specified date/time. | - |
| AddManagerAsRecipientType | Write | String | The AddManagerAsRecipientType parameter specifies an action that delivers or redirects messages to the user that's defined in the sender's Manager attribute. | `To`, `Cc`, `Bcc`, `Redirect` |
| AddToRecipients | Write | StringArray\[\] | The AddToRecipients parameter specifies an action that adds recipients to the To field of messages. | - |
| AnyOfCcHeader | Write | StringArray\[\] | The AnyOfCcHeader parameter specifies a condition that looks for recipients in the Cc field of messages. | - |
| AnyOfCcHeaderMemberOf | Write | StringArray\[\] | The AnyOfCcHeaderMemberOf parameter specifies a condition that looks for group members in the Cc field of messages. | - |
| AnyOfRecipientAddressContainsWords | Write | StringArray\[\] | The AnyOfRecipientAddressContainsWords parameter specifies a condition that looks for words in recipient email addresses. | - |
| AnyOfRecipientAddressMatchesPatterns | Write | StringArray\[\] | The AnyOfRecipientAddressMatchesPatterns parameter specifies a condition that looks for text patterns in recipient email addresses by using regular expressions. | - |
| AnyOfToCcHeader | Write | StringArray\[\] | The AnyOfToCcHeader parameter specifies a condition that looks for recipients in the To or Cc fields of messages. | - |
| AnyOfToCcHeaderMemberOf | Write | StringArray\[\] | The AnyOfToCcHeaderMemberOf parameter specifies a condition that looks for group members in the To and Cc fields of messages. | - |
| AnyOfToHeader | Write | StringArray\[\] | The AnyOfToHeader parameter specifies a condition that looks for recipients in the To field of messages. | - |
| AnyOfToHeaderMemberOf | Write | StringArray\[\] | The AnyOfToHeaderMemberOf parameter specifies a condition that looks for group members in the To field of messages. | - |
| ApplyClassification | Write | String | The ApplyClassification parameter specifies an action that applies a message classification to messages. | - |
| ApplyHtmlDisclaimerFallbackAction | Write | String | The ApplyHtmlDisclaimerFallbackAction parameter specifies what to do if the HTML disclaimer can't be added to a message. | `Wrap`, `Ignore`, `Reject` |
| ApplyHtmlDisclaimerLocation | Write | String | The ApplyHtmlDisclaimerLocation parameter specifies where to insert the HTML disclaimer text in the body of messages. | `Append`, `Prepend` |
| ApplyHtmlDisclaimerText | Write | String | The ApplyHtmlDisclaimerText parameter specifies an action that adds the disclaimer text to messages. | - |
| ApplyOME | Write | Boolean | The ApplyOME parameter specifies an action that encrypts messages and their attachments by using Office 365 Message Encryption. | - |
| ApplyRightsProtectionCustomizationTemplate | Write | String | The ApplyRightsProtectionCustomizationTemplate parameter specifies an action that applies a custom branding template for OME encrypted messages. | - |
| ApplyRightsProtectionTemplate | Write | String | The ApplyRightsProtectionTemplate parameter specifies an action that applies rights management service \(RMS\) templates to messages. | - |
| AttachmentContainsWords | Write | StringArray\[\] | The AttachmentContainsWords parameter specifies a condition that looks for words in message attachments. | - |
| AttachmentExtensionMatchesWords | Write | StringArray\[\] | The AttachmentExtensionMatchesWords parameter specifies a condition that looks for words in the file name extensions of message attachments. | - |
| AttachmentHasExecutableContent | Write | Boolean | The AttachmentHasExecutableContent parameter specifies a condition that looks for executable content in message attachments. | - |
| AttachmentIsPasswordProtected | Write | Boolean | The AttachmentIsPasswordProtected parameter specifies a condition that looks for password protected files in messages \(because the contents of the file can't be inspected\). | - |
| AttachmentIsUnsupported | Write | Boolean | The AttachmentIsUnsupported parameter specifies a condition that looks for unsupported file types in messages. | - |
| AttachmentMatchesPatterns | Write | StringArray\[\] | The AttachmentMatchesPatterns parameter specifies a condition that looks for text patterns in the content of message attachments by using regular expressions. | - |
| AttachmentNameMatchesPatterns | Write | StringArray\[\] | The AttachmentNameMatchesPatterns parameter specifies a condition that looks for text patterns in the file name of message attachments by using regular expressions. | - |
| AttachmentProcessingLimitExceeded | Write | Boolean | The AttachmentProcessingLimitExceeded parameter specifies a condition that looks for messages where attachment scanning didn't complete. | - |
| AttachmentPropertyContainsWords | Write | StringArray\[\] | The AttachmentPropertyContainsWords parameter specifies a condition that looks for words in the properties of attached Office documents. | - |
| AttachmentSizeOver | Write | String | The AttachmentSizeOver parameter specifies a condition that looks for messages where any attachment is greater than the specified size. | - |
| BetweenMemberOf1 | Write | StringArray\[\] | The BetweenMemberOf1 parameter specifies a condition that looks for messages that are sent between group members. | - |
| BetweenMemberOf2 | Write | StringArray\[\] | The BetweenMemberOf2 parameter specifies a condition that looks for messages that are sent between group members. | - |
| BlindCopyTo | Write | StringArray\[\] | The BlindCopyTo parameter specifies an action that adds recipients to the Bcc field of messages. | - |
| Comments | Write | String | The Comments parameter specifies optional descriptive text for the rule. The length of the comment can't exceed 1,024 characters. | - |
| ContentCharacterSetContainsWords | Write | StringArray\[\] | The ContentCharacterSetContainsWords parameter specifies a condition that looks for character set names in messages. | - |
| CopyTo | Write | StringArray\[\] | The CopyTo parameter specifies an action that adds recipients to the Cc field of messages. | - |
| DeleteMessage | Write | Boolean | The DeleteMessage parameter specifies an action that silently drops messages without an NDR. | - |
| DlpPolicy | Write | String | The DlpPolicy parameter specifies the data loss prevention \(DLP\) policy that's associated with the rule. | - |
| Enabled | Write | Boolean | The Enabled parameter specifies whether the new rule is created as enabled or disabled. | - |
| ExceptIfADComparisonAttribute | Write | String | The ExceptIfADComparisonAttribute parameter specifies an exception that compares an Active Directory attribute between the sender and all recipients of the message. | - |
| ExceptIfADComparisonOperator | Write | String | The ExceptIfADComparisonOperator parameter specifies the comparison operator for the ExceptIfADComparisonAttribute parameter. | `Equal`, `NotEqual` |
| ExceptIfAnyOfCcHeader | Write | StringArray\[\] | The ExceptIfAnyOfCcHeader parameter specifies an exception that looks for recipients in the Cc field of messages. | - |
| ExceptIfAnyOfCcHeaderMemberOf | Write | StringArray\[\] | The ExceptIfAnyOfCcHeaderMemberOf parameter specifies an exception that looks for group members in the Cc field of messages. You can use any value that uniquely identifies the group. | - |
| ExceptIfAnyOfRecipientAddressContainsWords | Write | StringArray\[\] | The ExceptIfAnyOfRecipientAddressContainsWords parameter specifies an exception that looks for words in recipient email addresses. | - |
| ExceptIfAnyOfRecipientAddressMatchesPatterns | Write | StringArray\[\] | The ExceptIfAnyOfRecipientAddressMatchesPatterns parameter specifies an exception that looks for text patterns in recipient email addresses by using regular expressions. | - |
| ExceptIfAnyOfToCcHeader | Write | StringArray\[\] | The ExceptIfAnyOfToCcHeader parameter specifies an exception that looks for recipients in the To or Cc fields of messages. | - |
| ExceptIfAnyOfToCcHeaderMemberOf | Write | StringArray\[\] | The ExceptIfAnyOfToCcHeaderMemberOf parameter specifies an exception that looks for group members in the To and Cc fields of messages. | - |
| ExceptIfAnyOfToHeader | Write | StringArray\[\] | The ExceptIfAnyOfToHeader parameter specifies an exception that looks for recipients in the To field of messages. | - |
| ExceptIfAnyOfToHeaderMemberOf | Write | StringArray\[\] | The ExceptIfAnyOfToHeaderMemberOf parameter specifies an exception that looks for group members in the To field of messages. | - |
| ExceptIfAttachmentContainsWords | Write | StringArray\[\] | The ExceptIfAttachmentContainsWords parameter specifies an exception that looks for words in message attachments. | - |
| ExceptIfAttachmentExtensionMatchesWords | Write | StringArray\[\] | The ExceptIfAttachmentExtensionMatchesWords parameter specifies an exception that looks for words in the file name extensions of message attachments. | - |
| ExceptIfAttachmentHasExecutableContent | Write | Boolean | The ExceptIfAttachmentHasExecutableContent parameter specifies an exception that looks for executable content in message attachments. | - |
| ExceptIfAttachmentIsPasswordProtected | Write | Boolean | The ExceptIfAttachmentIsPasswordProtected parameter specifies an exception that looks for password protected files in messages \(because the contents of the file can't be inspected\). | - |
| ExceptIfAttachmentIsUnsupported | Write | Boolean | The ExceptIfAttachmentIsUnsupported parameter specifies an exception that looks for unsupported file types in messages. | - |
| ExceptIfAttachmentMatchesPatterns | Write | StringArray\[\] | The ExceptIfAttachmentMatchesPatterns parameter specifies an exception that looks for text patterns in the content of message attachments by using regular expressions. | - |
| ExceptIfAttachmentNameMatchesPatterns | Write | StringArray\[\] | The ExceptIfAttachmentNameMatchesPatterns parameter specifies an exception that looks for text patterns in the file name of message attachments by using regular expressions. | - |
| ExceptIfAttachmentPropertyContainsWords | Write | StringArray\[\] | The ExceptIfAttachmentPropertyContainsWords parameter specifies an exception that looks for words in the properties of attached Office documents. | - |
| ExceptIfAttachmentProcessingLimitExceeded | Write | Boolean | The ExceptIfAttachmentProcessingLimitExceeded parameter specifies an exception that looks for messages where attachment scanning didn't complete. | - |
| ExceptIfAttachmentSizeOver | Write | String | The ExceptIfAttachmentSizeOver parameter specifies an exception that looks for messages where any attachment is greater than the specified size. | - |
| ExceptIfBetweenMemberOf1 | Write | StringArray\[\] | The ExceptIfBetweenMemberOf1 parameter specifies an exception that looks for messages that are sent between group members. | - |
| ExceptIfBetweenMemberOf2 | Write | StringArray\[\] | The ExceptIfBetweenMemberOf2 parameter specifies an exception that looks for messages that are sent between group members. | - |
| ExceptIfContentCharacterSetContainsWords | Write | StringArray\[\] | The ExceptIfContentCharacterSetContainsWords parameter specifies an exception that looks for character set names in messages. | - |
| ExceptIfFrom | Write | StringArray\[\] | The ExceptIfFrom parameter specifies an exception that looks for messages from specific senders. | - |
| ExceptIfFromAddressContainsWords | Write | StringArray\[\] | The ExceptIfFromAddressContainsWords parameter specifies an exception that looks for words in the sender's email address. | - |
| ExceptIfFromAddressMatchesPatterns | Write | StringArray\[\] | The ExceptIfFromAddressMatchesPatterns parameter specifies an exception that looks for text patterns in the sender's email address by using regular expressions. | - |
| ExceptIfFromMemberOf | Write | StringArray\[\] | The ExceptIfFromMemberOf parameter specifies an exception that looks for messages sent by group members. | - |
| ExceptIfFromScope | Write | String | The ExceptIfFromScope parameter specifies an exception that looks for the location of message senders. | `InOrganization`, `NotInOrganization` |
| ExceptIfHasClassification | Write | String | The ExceptIfHasClassification parameter specifies an exception that looks for messages with the specified message classification. | - |
| ExceptIfHasNoClassification | Write | Boolean | The ExceptIfHasNoClassification parameter specifies an exception that looks for messages with or without any message classifications. | - |
| ExceptIfHasSenderOverride | Write | Boolean | DEPRECATED | - |
| ExceptIfHeaderContainsMessageHeader | Write | String | The ExceptIfHeaderContainsMessageHeader parameter specifies the name of header field in the message header when searching for the words specified by the ExceptIfHeaderContainsWords parameter. | - |
| ExceptIfHeaderContainsWords | Write | StringArray\[\] | The ExceptIfHeaderContainsWords parameter specifies an exception that looks for words in a header field. | - |
| ExceptIfHeaderMatchesMessageHeader | Write | String | The ExceptIfHeaderMatchesMessageHeader parameter specifies the name of header field in the message header when searching for the text patterns specified by the ExceptIfHeaderMatchesPatterns parameter. | - |
| ExceptIfHeaderMatchesPatterns | Write | StringArray\[\] | The ExceptIfHeaderMatchesPatterns parameter specifies an exception that looks for text patterns in a header field by using regular expressions. | - |
| ExceptIfManagerAddresses | Write | StringArray\[\] | The ExceptIfManagerAddresses parameter specifies the users \(managers\) for the ExceptIfManagerForEvaluatedUser parameter. | - |
| ExceptIfManagerForEvaluatedUser | Write | String | The ExceptIfManagerForEvaluatedUser parameter specifies an exception that looks for users in the Manager attribute of senders or recipients. | - |
| ExceptIfMessageTypeMatches | Write | String | The ExceptIfMessageTypeMatches parameter specifies an exception that looks for messages of the specified type. | `OOF`, `AutoForward`, `Encrypted`, `Calendaring`, `PermissionControlled`, `Voicemail`, `Signed`, `ApprovalRequest`, `ReadReceipt` |
| ExceptIfMessageContainsDataClassifications | Write | StringArray\[\] | DEPRECATED | - |
| ExceptIfMessageSizeOver | Write | String | The ExceptIfMessageSizeOver parameter specifies an exception that looks for messages larger than the specified size. | - |
| ExceptIfRecipientADAttributeContainsWords | Write | StringArray\[\] | The ExceptIfRecipientADAttributeContainsWords parameter specifies an exception that looks for words in the Active Directory attributes of recipients. | - |
| ExceptIfRecipientADAttributeMatchesPatterns | Write | StringArray\[\] | The ExceptIfRecipientADAttributeMatchesPatterns parameter specifies an exception that looks for text patterns in the Active Directory attributes of recipients by using regular expressions. | - |
| ExceptIfRecipientAddressContainsWords | Write | StringArray\[\] | The ExceptIfRecipientAddressContainsWords parameter specifies an exception that looks for words in recipient email addresses. | - |
| ExceptIfRecipientAddressMatchesPatterns | Write | StringArray\[\] | The ExceptIfRecipientAddressMatchesPatterns parameter specifies an exception that looks for text patterns in recipient email addresses by using regular expressions. | - |
| ExceptIfRecipientDomainIs | Write | StringArray\[\] | The ExceptIfRecipientDomainIs parameter specifies an exception that looks for recipients with email address in the specified domains. | - |
| ExceptIfRecipientInSenderList | Write | StringArray\[\] | This parameter is reserved for internal Microsoft use. | - |
| ExceptIfSCLOver | Write | String | The ExceptIfSCLOver parameter specifies an exception that looks for the SCL value of messages | - |
| ExceptIfSenderADAttributeContainsWords | Write | StringArray\[\] | The ExceptIfSenderADAttributeContainsWords parameter specifies an exception that looks for words in Active Directory attributes of message senders. | - |
| ExceptIfSenderADAttributeMatchesPatterns | Write | StringArray\[\] | The ExceptIfSenderADAttributeMatchesPatterns parameter specifies an exception that looks for text patterns in Active Directory attributes of message senders by using regular expressions. | - |
| ExceptIfSenderDomainIs | Write | StringArray\[\] | The ExceptIfSenderDomainIs parameter specifies an exception that looks for senders with email address in the specified domains. | - |
| ExceptIfSenderInRecipientList | Write | StringArray\[\] | This parameter is reserved for internal Microsoft use. | - |
| ExceptIfSenderIpRanges | Write | StringArray\[\] | The ExceptIfSenderIpRanges parameter specifies an exception that looks for senders whose IP addresses matches the specified value, or fall within the specified ranges. | - |
| ExceptIfSenderManagementRelationship | Write | String | The ExceptIfSenderManagementRelationship parameter specifies an exception that looks for the relationship between the sender and recipients in messages. | `Manager`, `DirectReport` |
| ExceptIfSentTo | Write | StringArray\[\] | The ExceptIfSentTo parameter specifies an exception that looks for recipients in messages. You can use any value that uniquely identifies the recipient. | - |
| ExceptIfSentToMemberOf | Write | StringArray\[\] | The ExceptIfSentToMemberOf parameter specifies an exception that looks for messages sent to members of groups. You can use any value that uniquely identifies the group. | - |
| ExceptIfSentToScope | Write | String | The ExceptIfSentToScope parameter specifies an exception that looks for the location of a recipient. | `InOrganization`, `NotInOrganization`, `ExternalPartner`, `ExternalNonPartner` |
| ExceptIfSubjectContainsWords | Write | StringArray\[\] | The ExceptIfSubjectContainsWords parameter specifies an exception that looks for words in the Subject field of messages. | - |
| ExceptIfSubjectMatchesPatterns | Write | StringArray\[\] | The ExceptIfSubjectMatchesPatterns parameter specifies an exception that looks for text patterns in the Subject field of messages by using regular expressions. | - |
| ExceptIfSubjectOrBodyContainsWords | Write | StringArray\[\] | The ExceptIfSubjectOrBodyContainsWords parameter specifies an exception that looks for words in the Subject field or body of messages. | - |
| ExceptIfSubjectOrBodyMatchesPatterns | Write | StringArray\[\] | The ExceptIfSubjectOrBodyMatchesPatterns parameter specifies an exception that looks for text patterns in the Subject field or body of messages. | - |
| ExceptIfWithImportance | Write | String | The ExceptIfWithImportance parameter specifies an exception that looks for messages with the specified importance level. | `Low`, `Normal`, `High` |
| ExpiryDate | Write | String | The ExpiryDate parameter specifies when this rule will stop processing messages. The rule won't take any action on messages after the specified date/time. | - |
| From | Write | StringArray\[\] | The From parameter specifies a condition that looks for messages from specific senders. You can use any value that uniquely identifies the sender. | - |
| FromAddressContainsWords | Write | StringArray\[\] | The FromAddressContainsWords parameter specifies a condition that looks for words in the sender's email address. | - |
| FromAddressMatchesPatterns | Write | StringArray\[\] | The FromAddressMatchesPatterns parameter specifies a condition that looks for text patterns in the sender's email address by using regular expressions. | - |
| FromMemberOf | Write | StringArray\[\] | The FromMemberOf parameter specifies a condition that looks for messages sent by group members. | - |
| FromScope | Write | String | The FromScope parameter specifies a condition that looks for the location of message senders. | `InOrganization`, `NotInOrganization` |
| GenerateIncidentReport | Write | String | The GenerateIncidentReport parameter specifies where to send the incident report that's defined by the IncidentReportContent parameter. | - |
| GenerateNotification | Write | String | The GenerateNotification parameter specifies an action that sends a notification message to recipients. | - |
| HasClassification | Write | String | The HasClassification parameter specifies a condition that looks for messages with the specified message classification. | - |
| HasNoClassification | Write | Boolean | The HasNoClassification parameter specifies a condition that looks for messages with or without any message classifications. | - |
| HasSenderOverride | Write | Boolean | DEPRECATED | - |
| HeaderContainsMessageHeader | Write | String | The HeaderContainsMessageHeader parameter specifies the name of header field in the message header when searching for the words specified by the HeaderContainsWords parameter. | - |
| HeaderContainsWords | Write | StringArray\[\] | The HeaderContainsWords parameter specifies a condition that looks for words in a header field. | - |
| HeaderMatchesMessageHeader | Write | String | The HeaderMatchesMessageHeader parameter specifies the name of header field in the message header when searching for the text patterns specified by the HeaderMatchesPatterns parameter. | - |
| HeaderMatchesPatterns | Write | StringArray\[\] | The HeaderMatchesPatterns parameter specifies a condition that looks for text patterns in a header field by using regular expressions. | - |
| IncidentReportContent | Write | StringArray\[\] | The IncidentReportContent parameter specifies the message properties that are included in the incident report that's generated when a message violates a DLP policy. | - |
| ManagerAddresses | Write | StringArray\[\] | The ManagerAddresses parameter specifies the users \(managers\) for the ExceptIfManagerForEvaluatedUser parameter. | - |
| ManagerForEvaluatedUser | Write | String | The ManagerForEvaluatedUser parameter specifies a condition that looks for users in the Manager attribute of senders or recipients. | `Recipient`, `Sender` |
| MessageContainsDataClassifications | Write | StringArray\[\] | DEPRECATED | - |
| MessageSizeOver | Write | String | The MessageSizeOver parameter specifies a condition that looks for messages larger than the specified size. The size includes the message and all attachments. | - |
| MessageTypeMatches | Write | String | The MessageTypeMatches parameter specifies a condition that looks for messages of the specified type. | `OOF`, `AutoForward`, `Encrypted`, `Calendaring`, `PermissionControlled`, `Voicemail`, `Signed`, `ApprovalRequest`, `ReadReceipt` |
| Mode | Write | String | The Mode parameter specifies how the rule operates. | `Audit`, `AuditAndNotify`, `Enforce` |
| ModerateMessageByManager | Write | Boolean | The ModerateMessageByManager parameter specifies an action that forwards messages for approval to the user that's specified in the sender's Manager attribute. | - |
| ModerateMessageByUser | Write | StringArray\[\] | The ModerateMessageByUser parameter specifies an action that forwards messages for approval to the specified users. | - |
| NotifySender | Write | String | DEPRECATED | `NotifyOnly`, `RejectMessage`, `RejectUnlessFalsePositiveOverride`, `RejectUnlessSilentOverride`, `RejectUnlessExplicitOverride` |
| PrependSubject | Write | String | The PrependSubject parameter specifies an action that adds text to add to the beginning of the Subject field of messages. | - |
| Priority | Write | UInt32 | The Priority parameter specifies a priority value for the rule that determines the order of rule processing. | - |
| Quarantine | Write | Boolean | The Quarantine parameter specifies an action that quarantines messages. | - |
| RecipientADAttributeContainsWords | Write | StringArray\[\] | The RecipientADAttributeContainsWords parameter specifies a condition that looks for words in the Active Directory attributes of recipients. | - |
| RecipientADAttributeMatchesPatterns | Write | StringArray\[\] | The RecipientADAttributeMatchesPatterns parameter specifies a condition that looks for text patterns in the Active Directory attributes of recipients by using regular expressions. | - |
| RecipientAddressContainsWords | Write | StringArray\[\] | The RecipientAddressContainsWords parameter specifies a condition that looks for words in recipient email addresses. | - |
| RecipientAddressMatchesPatterns | Write | StringArray\[\] | The RecipientAddressMatchesPatterns parameter specifies a condition that looks for text patterns in recipient email addresses by using regular expressions. | - |
| RecipientAddressType | Write | String | The RecipientAddressType parameter specifies how conditions and exceptions check recipient email addresses. | `Original`, `Resolved` |
| RecipientDomainIs | Write | StringArray\[\] | The RecipientDomainIs parameter specifies a condition that looks for recipients with email address in the specified domains. | - |
| RecipientInSenderList | Write | StringArray\[\] | This parameter is reserved for internal Microsoft use. | - |
| RedirectMessageTo | Write | StringArray\[\] | The RedirectMessageTo parameter specifies a rule action that redirects messages to the specified recipients. | - |
| RejectMessageEnhancedStatusCode | Write | String | The RejectMessageEnhancedStatusCode parameter specifies the enhanced status code that's used when the rule rejects messages. | - |
| RejectMessageReasonText | Write | String | The RejectMessageReasonText parameter specifies the explanation text that's used when the rule rejects messages. | - |
| RemoveHeader | Write | String | The RemoveHeader parameter specifies an action that removes a header field from the message header. | - |
| RemoveOME | Write | Boolean | The RemoveOME parameter specifies an action that removes the previous version of Office 365 Message Encryption from messages and their attachments. | - |
| RemoveOMEv2 | Write | Boolean | The RemoveOMEv2 parameter specifies an action that removes Office 365 Message Encryption from messages and their attachments. | - |
| RemoveRMSAttachmentEncryption | Write | Boolean | This parameter specifies an action or part of an action for the rule. | - |
| RouteMessageOutboundConnector | Write | String | The RouteMessageOutboundConnector parameter specifies an action that routes messages through the specified Outbound connector in Office 365. | - |
| RouteMessageOutboundRequireTls | Write | Boolean | The RouteMessageOutboundRequireTls parameter specifies an action that uses Transport Layer Security \(TLS\) encryption to deliver messages outside your organization. | - |
| RuleErrorAction | Write | String | The RuleErrorAction parameter specifies what to do if rule processing can't be completed on messages. | `Ignore`, `Defer` |
| RuleSubType | Write | String | The RuleSubType parameter specifies the rule type. | `Dlp`, `None` |
| SCLOver | Write | String | The SCLOver parameter specifies a condition that looks for the SCL value of messages | - |
| SenderADAttributeContainsWords | Write | StringArray\[\] | The SenderADAttributeContainsWords parameter specifies a condition that looks for words in Active Directory attributes of message senders. | - |
| SenderADAttributeMatchesPatterns | Write | StringArray\[\] | The SenderADAttributeMatchesPatterns parameter specifies a condition that looks for text patterns in Active Directory attributes of message senders by using regular expressions. | - |
| SenderAddressLocation | Write | String | The SenderAddressLocation parameter specifies where to look for sender addresses in conditions and exceptions that examine sender email addresses. | `Header`, `Envelope`, `HeaderOrEnvelope` |
| SenderDomainIs | Write | StringArray\[\] | The SenderDomainIs parameter specifies a condition that looks for senders with email address in the specified domains. | - |
| SenderInRecipientList | Write | String | This parameter is reserved for internal Microsoft use. | - |
| SenderIpRanges | Write | StringArray\[\] | The SenderIpRanges parameter specifies a condition that looks for senders whose IP addresses matches the specified value, or fall within the specified ranges. | - |
| SenderManagementRelationship | Write | String | The SenderManagementRelationship parameter specifies a condition that looks for the relationship between the sender and recipients in messages. | `Manager`, `DirectReport` |
| SentTo | Write | StringArray\[\] | The SentTo parameter specifies a condition that looks for recipients in messages. | - |
| SentToMemberOf | Write | StringArray\[\] | The SentToMemberOf parameter specifies a condition that looks for messages sent to members of distribution groups, dynamic distribution groups, or mail-enabled security groups. | - |
| SentToScope | Write | String | The SentToScope parameter specifies a condition that looks for the location of recipients. | `InOrganization`, `NotInOrganization`, `ExternalPartner`, `ExternalNonPartner` |
| SetAuditSeverity | Write | String | The SetAuditSeverity parameter specifies an action that sets the severity level of the incident report and the corresponding entry that's written to the message tracking log when messages violate DLP policies. | `DoNotAudit`, `Low`, `Medium`, `High` |
| SetHeaderName | Write | String | The SetHeaderName parameter specifies an action that adds or modifies a header field in the message header. | - |
| SetHeaderValue | Write | String | The SetHeaderValue parameter specifies an action that adds or modifies a header field in the message header. | - |
| SetSCL | Write | String | The SetSCL parameter specifies an action that adds or modifies the SCL value of messages. | - |
| StopRuleProcessing | Write | Boolean | The StopRuleProcessing parameter specifies an action that stops processing more rules. | - |
| SubjectContainsWords | Write | StringArray\[\] | The SubjectContainsWords parameter specifies a condition that looks for words in the Subject field of messages. | - |
| SubjectMatchesPatterns | Write | StringArray\[\] | The SubjectMatchesPatterns parameter specifies a condition that looks for text patterns in the Subject field of messages by using regular expressions. | - |
| SubjectOrBodyContainsWords | Write | StringArray\[\] | The SubjectOrBodyContainsWords parameter specifies a condition that looks for words in the Subject field or body of messages. | - |
| SubjectOrBodyMatchesPatterns | Write | StringArray\[\] | The SubjectOrBodyMatchesPatterns parameter specifies a condition that looks for text patterns in the Subject field or body of messages. | - |
| WithImportance | Write | String | The WithImportance parameter specifies a condition that looks for messages with the specified importance level. | `Low`, `Normal`, `High` |
| Ensure | Write | String | Specify if the Transport Rule should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Exchange Administrator |

#### Exchange

To authenticate with Microsoft Exchange, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Roles

- Security Admin, Data Loss Prevention, Transport Rules, View-Only Configuration, Security Reader, Information Rights Management

##### Role Groups

- Organization Management

#### Office 365 Exchange Online

To authenticate with Exchange Online, this resource requires the following application permissions. Delegated scenarios aren't supported.

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Exchange.ManageAsApp |
| Update | None |

## Related content

- [Overview of the Tenant Configuration Management APIs](https://learn.microsoft.com/en-us/graph/unified-tenant-configuration-management-concept-overview)
- [Set up authentication for TCM](https://learn.microsoft.com/en-us/graph/utcm-authentication-setup)
