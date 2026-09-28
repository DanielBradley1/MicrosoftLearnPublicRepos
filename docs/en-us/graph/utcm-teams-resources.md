<!-- Source: https://learn.microsoft.com/en-us/graph/utcm-teams-resources -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# Supported Microsoft Teams resources for Tenant Configuration Management

This article lists the supported resource types for Microsoft Teams in the Tenant Configuration Management \(TCM\) APIs in Microsoft Graph. Use these resource types to monitor and manage your Microsoft Teams configuration settings.

For the complete schema, required permissions, and examples for each resource type, see the [TCM schema store](https://json.schemastore.org/utcm-monitor.json).

## appPermissionPolicy resource type

### Description

Manages the Teams App Permission Policies.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier to be assigned to the new Teams app permission policy. Use the 'Global' Identity if you wish to assign this policy to the entire tenant. | - |
| Description | Write | String | Enables administrators to provide explanatory text to accompany a Teams app permission policy. | - |
| GlobalCatalogAppsType | Write | String | The types of apps for the Global Catalog. | - |
| PrivateCatalogAppsType | Write | String | The types of apps for the Private Catalog. | - |
| DefaultCatalogAppsType | Write | String | The types of apps for the Default Catalog. | - |
| GlobalCatalogApps | Write | StringArray\[\] | The list of apps for the Global Catalog. | - |
| PrivateCatalogApps | Write | StringArray\[\] | The list of apps for the Private Catalog. | - |
| DefaultCatalogApps | Write | StringArray\[\] | The list of apps for the Default Catalog. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## appSetupPolicy resource type

### Description

Manages Teams app setup policies in your tenant.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier to be assigned to the new Teams app setup policy. Use the 'Global' Identity if you wish to assign this policy to the entire tenant. | - |
| Description | Write | String | Enables administrators to provide explanatory text to accompany a Teams app setup policy. | - |
| AppPresetList | Write | StringArray\[\] | Choose which apps and messaging extensions you want to be installed in your users' personal Teams environment and in meetings they create. Users can install other available apps from the Teams app store. | - |
| AppPresetMeetingList | Write | StringArray\[\] | Choose which apps and meeting extensions you want to be installed in your users' personal Teams environment and in meetings they create. Users can install other available apps from the Teams app store. | - |
| PinnedAppBarApps | Write | StringArray\[\] | Pinning an app displays the app in the app bar in Teams client. Admins can pin apps and they can allow users to pin apps. Pinning is used to highlight apps that are needed the most by users and promote ease of access. | - |
| PinnedMessageBarApps | Write | StringArray\[\] | Apps are pinned in messaging extensions and into the ellipsis menu. | - |
| AllowUserPinning | Write | Boolean | If you turn this on, the user's existing app pins will be added to the list of pinned apps set in this policy. Users can rearrange, add, and remove pins as they choose. If you turn this off, the user's existing app pins will be removed and replaced with the apps defined in this policy. | - |
| AllowSideLoading | Write | Boolean | This is also known as side loading. This setting determines if a user can upload a custom app package in the Teams app. Turning it on lets you create or develop a custom app to be used personally or across your organization without having to submit it to the Teams app store. Uploading a custom app also lets you test an app before you distribute it more widely by only assigning it to a single user or group of users. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## audioConferencingPolicy resource type

### Description

Configures a Teams Audio Conferencing Policy.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specify the name of the policy that you are creating | - |
| AllowTollFreeDialin | Write | Boolean | Determines whether users of the Policy can have Toll free numbers | - |
| MeetingInvitePhoneNumbers | Write | String | Determines the list of audio-conferencing Toll- and Toll-free telephone numbers that will be included in meetings invites created by users of this policy. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## callHoldPolicy resource type

### Description

Creates a new Teams call hold policy in your tenant. The Teams call hold policy is used to customize the call hold experience for Teams clients.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier to be assigned to the new Teams call hold policy. Use the 'Global' Identity if you wish to assign this policy to the entire tenant. | - |
| AudioFileId | Write | String | A string representing the ID referencing an audio file uploaded via the Import-CsOnlineAudioFile cmdlet. | - |
| Description | Write | String | Enables administrators to provide explanatory text to accompany a Teams call hold policy. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## callingPolicy resource type

### Description

This resource configures a [Teams Calling Policy](https://learn.microsoft.com/en-us/microsoftteams/teams-calling-policy).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Calling Policy. | - |
| Description | Write | String | Description of the Teams Calling Policy. | - |
| AllowPrivateCalling | Write | Boolean | Controls all calling capabilities in Teams. Turning this off will turn off all calling functionality in Teams. If you use Skype for Business for calling, this policy will not affect calling functionality in Skype for Business. | - |
| AllowVoicemail | Write | String | Enables inbound calls to be routed to voice mail. Valid options are: AlwaysEnabled, AlwaysDisabled, UserOverride. | `AlwaysEnabled`, `AlwaysDisabled`, `UserOverride` |
| AllowCallGroups | Write | Boolean | Enables inbound calls to be routed to call groups. | - |
| AllowDelegation | Write | Boolean | Enables inbound calls to be routed to delegates; allows delegates to make outbound calls on behalf of the users for whom they have delegated permissions. | - |
| AllowCallForwardingToUser | Write | Boolean | Enables call forwarding or simultaneous ringing of inbound calls to other users in your tenant. | - |
| AllowCallForwardingToPhone | Write | Boolean | Enables call forwarding or simultaneous ringing of inbound calls to any phone number. | - |
| AllowCallRedirect | Write | String | Setting this parameter provides the ability to configure call redirection capabilities on Teams phones. | `Enabled`, `Disabled`, `UserOverride` |
| AllowSIPDevicesCalling | Write | Boolean | Determines whether the user is allowed to use SIP devices for calling on behalf of a Teams client. | - |
| AllowWebPSTNCalling | Write | Boolean | Allows PSTN calling from the Team web client | - |
| PreventTollBypass | Write | Boolean | Setting this parameter to True will send calls through PSTN and incur charges rather than going through the network and bypassing the tolls. | - |
| BusyOnBusyEnabledType | Write | String | Setting this parameter lets you configure how incoming calls are handled when a user is already in a call or conference or has a call placed on hold. New or incoming calls will be rejected with a busy signal. Valid options are: Enabled, Disabled and Unanswered. | `Enabled`, `Disabled`, `Unanswered`, `UserOverride` |
| CallRecordingExpirationDays | Write | UInt32 | Sets the expiration of the recorded 1:1 calls. | - |
| MusicOnHoldEnabledType | Write | String | Setting this parameter allows you to turn on or turn off music on hold when a PSTN caller is placed on hold. It's turned on by default. Valid options are: Enabled, Disabled, UserOverride. For now setting the value to UserOverride is the same as Enabled. This setting does not apply to call park and SLA boss delegate features. Valid options are: Enabled, Disabled, UserOverride. | `Enabled`, `Disabled`, `UserOverride` |
| SafeTransferEnabled | Write | String | This parameter is not available for use. Valid options are: Enabled, Disabled, UserOverride. | `Enabled`, `Disabled`, `UserOverride` |
| AllowCloudRecordingForCalls | Write | Boolean | Setting this parameter to True will allows 1:1 Calls to be recorded. | - |
| AllowTranscriptionforCalling | Write | Boolean | Determines whether post-meeting captions and transcriptions are allowed in a user's meetings. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| LiveCaptionsEnabledTypeForCalling | Write | String | Determines whether real-time captions are available for the user in Teams meetings. Set this to DisabledUserOverride to allow user to turn on live captions. Set this to Disabled to prohibit. | `DisabledUserOverride`, `Disabled` |
| AutoAnswerEnabledType | Write | String | This setting allows the tenant admin to enable or disable the Auto-Answer setting. Valid options are: Enabled, Disabled. | `Enabled`, `Disabled` |
| SpamFilteringEnabledType | Write | String | Setting this parameter determines whether calls identified as Spam will be rejected or not \(probably\). Valid options are: Enabled, Disabled. | `Enabled`, `Disabled` |
| Ensure | Write | String | Present ensures the policyexists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## callParkPolicy resource type

### Description

The TeamsCallParkPolicy controls whether or not users are able to leverage the call park feature in Microsoft Teams. Call park allows enterprise voice customers to place a call on hold and then perform a number of actions on that call: transfer to another department, retrieve via the same phone, or retrieve via a different Teams phone. The New-CsTeamsCallParkPolicy resource lets you create a new custom policy that can then be assigned to one or more specific users.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | A unique identifier for the policy - this will be used to retrieve the policy later on to assign it to specific users. | - |
| AllowCallPark | Write | Boolean | If set to true, customers will be able to leverage the call park feature to place calls on hold and then decide how the call should be handled - transferred to another department, retrieved using the same phone, or retrieved using a different phone. | - |
| Description | Write | String | Description of the Teams Call Park Policy. | - |
| ParkTimeoutSeconds | Write | UInt64 | Specify the number of seconds to wait before ringing the parker when the parked call hasn't been picked up. Value can be from 120 to 1800 \(seconds\). | - |
| PickupRangeEnd | Write | UInt64 | Specify the maximum value that a rendered pickup code can take. Value can be from 10 to 9999. Note: PickupRangeStart must be smaller than PickupRangeEnd. | - |
| PickupRangeStart | Write | UInt64 | Specify the minimum value that a rendered pickup code can take. Value can be from 10 to 9999. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## callQueue resource type

### Description

This resource is used to manage Call Queue in your Skype for Business Online organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Key | String | The Name parameter specifies a unique name for the Call Queue. | - |
| AgentAlertTime | Write | UInt16 | The Name parameter specifies a unique name for the Call Queue. | - |
| AllowOptOut | Write | Boolean | The AllowOptOut parameter indicates whether or not agents can opt in or opt out from taking calls from a Call Queue. | - |
| DistributionLists | Write | StringArray\[\] | The DistributionLists parameter lets you add all the members of the distribution lists to the Call Queue. This is a list of distribution list GUIDs. A service wide configurable maximum number of DLs per Call Queue are allowed. Only the first N \(service wide configurable\) agents from all distribution lists combined are considered for accepting the call. Nested DLs are supported. O365 Groups can also be used to add members to the Call Queue. | - |
| UseDefaultMusicOnHold | Write | Boolean | The UseDefaultMusicOnHold parameter indicates that this Call Queue uses the default music on hold. This parameter can't be specified together with MusicOnHoldAudioFileId. | - |
| WelcomeMusicAudioFileId | Write | String | The WelcomeMusicAudioFileId parameter represents the audio file to play when callers are connected with the Call Queue. This is the unique identifier of the audio file. | - |
| MusicOnHoldAudioFileId | Write | String | The MusicOnHoldFileContent parameter represents music to play when callers are placed on hold. This is the unique identifier of the audio file. This parameter is required if the UseDefaultMusicOnHold parameter is not specified. | - |
| OverflowAction | Write | String | The OverflowAction parameter designates the action to take if the overflow threshold is reached. The OverflowAction property must be set to one of the following values: DisconnectWithBusy, Forward, Voicemail, and SharedVoicemail. The default value is DisconnectWithBusy. | `DisconnectWithBusy`, `Forward`, `Voicemail`, `SharedVoicemail` |
| OverflowActionTarget | Write | String | The OverflowActionTarget parameter represents the target of the overflow action. If the OverFlowAction is set to Forward, this parameter must be set to a Guid or a telephone number with a mandatory 'tel:' prefix. If the OverflowAction is set to SharedVoicemail, this parameter must be set to a group ID \(Microsoft 365, Distribution list, or Mail-enabled security\). Otherwise, this parameter is optional. | - |
| OverflowThreshold | Write | UInt16 | The OverflowThreshold parameter defines the number of calls that can be in the queue at any one time before the overflow action is triggered. The OverflowThreshold can be any integer value between 0 and 200, inclusive. A value of 0 causes calls not to reach agents and the overflow action to be taken immediately. | - |
| TimeoutAction | Write | String | The TimeoutAction parameter defines the action to take if the timeout threshold is reached. The TimeoutAction property must be set to one of the following values: Disconnect, Forward, Voicemail, and SharedVoicemail. The default value is Disconnect. | `Disconnect`, `Forward`, `Voicemail`, `SharedVoicemail` |
| TimeoutActionTarget | Write | String | The TimeoutActionTarget represents the target of the timeout action. If the TimeoutAction is set to Forward, this parameter must be set to a Guid or a telephone number with a mandatory 'tel:' prefix. If the TimeoutAction is set to SharedVoicemail, this parameter must be set to an Office 365 Group ID. Otherwise, this field is optional. | - |
| TimeoutThreshold | Write | UInt16 | The TimeoutThreshold parameter defines the time \(in seconds\) that a call can be in the queue before that call times out. At that point, the system will take the action specified by the TimeoutAction parameter. The TimeoutThreshold can be any integer value between 0 and 2700 seconds \(inclusive\), and is rounded to the nearest 15th interval. For example, if set to 47 seconds, then it's rounded down to 45. If set to 0, welcome music is played, and then the timeout action will be taken. | - |
| RoutingMethod | Write | String | The RoutingMethod defines how agents will be called in a Call Queue. If the routing method is set to Serial, then agents will be called one at a time. If the routing method is set to Attendant, then agents will be called in parallel. If routing method is set to RoundRobin, the agents will be called using Round Robin strategy so that all agents share the call-load equally. If routing method is set to LongestIdle, the agents will be called based on their idle time, i.e., the agent that has been idle for the longest period will be called. | `Attendant`, `Serial`, `RoundRobin`, `LongestIdle` |
| PresenceBasedRouting | Write | Boolean | The PresenceBasedRouting parameter indicates whether or not presence based routing will be applied while call being routed to Call Queue agents. When set to False, calls will be routed to agents who have opted in to receive calls, regardless of their presence state. When set to True, opted-in agents will receive calls only when their presence state is Available. | - |
| ConferenceMode | Write | Boolean | The ConferenceMode parameter indicates whether or not Conference mode will be applied on calls for this Call queue. Conference mode significantly reduces the amount of time it takes for a caller to be connected to an agent, after the agent accepts the call. | - |
| Users | Write | StringArray\[\] | The Users parameter lets you add agents to the Call Queue. This parameter expects a list of user unique identifiers \(GUID\). | - |
| LanguageId | Write | String | The LanguageId parameter indicates the language that is used to play shared voicemail prompts. This parameter becomes a required parameter If either OverflowAction or TimeoutAction is set to SharedVoicemail. You can query the supported languages using the Get-CsAutoAttendantSupportedLanguage cmdlet. | - |
| OboResourceAccountIds | Write | StringArray\[\] | The OboResourceAccountIds parameter lets you add resource account with phone number to the Call Queue. The agents in the Call Queue will be able to make outbound calls using the phone number on the resource accounts. This is a list of resource account GUIDs. Only Call Queue managed by a Teams Channel will be able to use this feature. | - |
| OverflowDisconnectTextToSpeechPrompt | Write | String | The OverflowDisconnectTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being disconnected due to overflow. | - |
| OverflowDisconnectAudioFilePrompt | Write | String | The OverflowDisconnectAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being disconnected due to overflow. | - |
| OverflowRedirectPersonTextToSpeechPrompt | Write | String | The OverflowRedirectPersonTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to a person in the organization due to overflow. | - |
| OverflowRedirectPersonAudioFilePrompt | Write | String | The OverflowRedirectPersonAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being redirected to a person in the organization due to overflow. | - |
| OverflowRedirectVoiceAppTextToSpeechPrompt | Write | String | The OverflowRedirectVoiceAppsTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to a voice application due to overflow. | - |
| OverflowRedirectVoiceAppAudioFilePrompt | Write | String | The OverflowRedirectVoiceAppAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being redirected to a voice application due to overflow. | - |
| OverflowRedirectPhoneNumberTextToSpeechPrompt | Write | String | The OverflowRedirectPhoneNumberTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to an external PSTN phone number due to overflow. | - |
| OverflowRedirectPhoneNumberAudioFilePrompt | Write | String | The OverflowRedirectPhoneNumberAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being redirected to an external PSTN phone number due to overflow. | - |
| OverflowRedirectVoicemailTextToSpeechPrompt | Write | String | The OverflowRedirectVoicemailTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to a person's voicemail due to overflow. | - |
| OverflowRedirectVoicemailAudioFilePrompt | Write | String | The OverflowRedirectVoiceMailAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being redirected to a person's voicemail due to overflow. | - |
| OverflowSharedVoicemailTextToSpeechPrompt | Write | String | The OverflowRedirectVoicemailTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to a person's voicemail due to overflow. | - |
| OverflowSharedVoicemailAudioFilePrompt | Write | String | The OverflowSharedVoicemailAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is to be played as a greeting to the caller when transferred to shared voicemail on overflow. This parameter becomes a required parameter when OverflowAction is SharedVoicemail and OverflowSharedVoicemailTextToSpeechPrompt is null. | - |
| EnableOverflowSharedVoicemailTranscription | Write | Boolean | The EnableOverflowSharedVoicemailTranscription parameter is used to turn on transcription for voicemails left by a caller on overflow. This parameter is only applicable when OverflowAction is set to SharedVoicemail. | - |
| TimeoutDisconnectTextToSpeechPrompt | Write | String | The TimeoutDisconnectTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being disconnected due to timeout. | - |
| TimeoutDisconnectAudioFilePrompt | Write | String | The TimeoutDisconnectAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being disconnected due to timeout. | - |
| TimeoutRedirectPersonTextToSpeechPrompt | Write | String | The TimeoutRedirectPersonTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to a person in the organization due to timeout. | - |
| TimeoutRedirectPersonAudioFilePrompt | Write | String | The TimeoutRedirectPersonAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being redirected to a person in the organization due to timeout. | - |
| TimeoutRedirectVoiceAppTextToSpeechPrompt | Write | String | The TimeoutRedirectVoiceAppsTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to a voice application due to timeout. | - |
| TimeoutRedirectVoiceAppAudioFilePrompt | Write | String | The TimeoutRedirectVoiceAppAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being redirected to a voice application due to timeout. | - |
| TimeoutRedirectPhoneNumberTextToSpeechPrompt | Write | String | The TimeoutRedirectPhoneNumberTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to an external PSTN phone number due to timeout. | - |
| TimeoutRedirectPhoneNumberAudioFilePrompt | Write | String | The TimeoutRedirectPhoneNumberAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being redirected to an external PSTN phone number due to timeout. | - |
| TimeoutRedirectVoicemailTextToSpeechPrompt | Write | String | The TimeoutRedirectVoicemailTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is played to the caller when being redirected to a person's voicemail due to timeout. | - |
| TimeoutRedirectVoicemailAudioFilePrompt | Write | String | The TimeoutRedirectVoiceMailAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is played to the caller when being redirected to a person's voicemail due to timeout. | - |
| TimeoutSharedVoicemailTextToSpeechPrompt | Write | String | The TimeoutSharedVoicemailTextToSpeechPrompt parameter indicates the Text-to-Speech \(TTS\) prompt which is to be played as a greeting to the caller when transferred to shared voicemail on timeout. This parameter becomes a required parameter when TimeoutAction is SharedVoicemail and TimeoutSharedVoicemailAudioFilePrompt is null. | - |
| TimeoutSharedVoicemailAudioFilePrompt | Write | String | The TimeoutSharedVoicemailAudioFilePrompt parameter indicates the unique identifier for the Audio file prompt which is to be played as a greeting to the caller when transferred to shared voicemail on timeout. This parameter becomes a required parameter when TimeoutAction is SharedVoicemail and TimeoutSharedVoicemailTextToSpeechPrompt is null. | - |
| EnableTimeoutSharedVoicemailTranscription | Write | Boolean | The EnableTimeoutSharedVoicemailTranscription parameter is used to turn on transcription for voicemails left by a caller on timeout. This parameter is only applicable when TimeoutAction is set to SharedVoicemail. | - |
| ChannelId | Write | String | Id of the channel to connect a call queue to. | - |
| ChannelUserObjectId | Write | String | Guid should contain 32 digits with 4 dashes \(xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx\). This is the GUID of one of the owners of the team the channels belongs to. | - |
| AuthorizedUsers | Write | StringArray\[\] | This is a list of GUIDs for users who are authorized to make changes to this call queue. The users must also have a TeamsVoiceApplications policy assigned. The GUID should contain 32 digits with 4 dashes \(xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx\). | - |
| Ensure | Write | String | Present ensures the Team Message Policy exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## channelsPolicy resource type

### Description

This resource configures a [Teams Channel Policy](https://learn.microsoft.com/en-us/microsoftteams/teams-policies).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Channel Policy. | - |
| Description | Write | String | Description of the Teams Channel Policy. | - |
| AllowChannelSharingToExternalUser | Write | Boolean | Determines whether a user is allowed to share a shared channel with an external user. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowOrgWideTeamCreation | Write | Boolean | Determines whether a user is allowed to create an org-wide team. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| EnablePrivateTeamDiscovery | Write | Boolean | Determines whether a user is allowed to discover private teams in suggestions and search results. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowPrivateChannelCreation | Write | Boolean | Determines whether a user is allowed to create a private channel. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowSharedChannelCreation | Write | Boolean | Determines whether a user is allowed to create a shared channel. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowUserToParticipateInExternalSharedChannel | Write | Boolean | Determines whether a user is allowed to participate in a shared channel that has been shared by an external user. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## clientConfiguration resource type

### Description

This resource is used to configure the [Teams client settings](https://learn.microsoft.com/en-us/microsoftteams/enable-features-office-365#teams-settings-and-teams-upgrade-settings-in-the-microsoft-teams-admin-center).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The only valid input is Global - the tenant wide configuration | `Global` |
| AllowBox | Write | Boolean | Designates whether users are able to leverage Box as a third party storage solution in Microsoft Teams. If $true, users will be able to add Box in the client and interact with the files stored there. | - |
| AllowDropBox | Write | Boolean | Designates whether users are able to leverage DropBox as a third party storage solution in Microsoft Teams. If $true, users will be able to add DropBox in the client and interact with the files stored there. | - |
| AllowEmailIntoChannel | Write | Boolean | When set to $true, mail hooks are enabled, and users can post messages to a channel by sending an email to the email address of Teams channel. | - |
| AllowGoogleDrive | Write | Boolean | Designates whether users are able to leverage GoogleDrive as a third party storage solution in Microsoft Teams. If $true, users will be able to add Google Drive in the client and interact with the files stored there. | - |
| AllowGuestUser | Write | Boolean | Designates whether or not guest users in your organization will have access to the Teams client. If $true, guests in your tenant will be able to access the Teams client. Note that this setting has a core dependency on Guest Access being enabled in your Office 365 tenant. | - |
| AllowOrganizationTab | Write | Boolean | When set to $true, users will be able to see the organizational chart icon other users' contact cards, and when clicked, this icon will display the detailed organizational chart. | - |
| AllowResourceAccountSendMessage | Write | Boolean | Surface Hub uses a device account to provide email and collaboration services \(IM, video, voice\). This device account is used as the originating identity \(the from party\) when sending email, IM, and placing calls. As this account is not coming from an individual, identifiable user, it's deemed anonymous because it originated from the Surface Hub's device account. If set to $true, these device accounts will be able to send chat messages in Skype for Business Online \(does not apply to Microsoft Teams\). | - |
| AllowScopedPeopleSearchandAccess | Write | Boolean | If set to $true, the Exchange address book policy \(ABP\) will be used to provide customized view of the global address book for each user. This is only a virtual separation and not a legal separation. | - |
| AllowShareFile | Write | Boolean | Designates whether users are able to leverage ShareFile as a third party storage solution in Microsoft Teams. If $true, users will be able to add ShareFile in the client and interact with the files stored there. | - |
| AllowSkypeBusinessInterop | Write | Boolean | When set to $true, Teams conversations automatically show up in Skype for Business for users that aren't enabled for Teams. | - |
| AllowEgnyte | Write | Boolean | Designates whether users are able to leverage Egnyte as a third party storage solution in Microsoft Teams. If $true, users will be able to add Egnyte in the client and interact with the files stored there. | - |
| ContentPin | Write | String | This setting applies only to Skype for Business Online \(not Microsoft Teams\) and defines whether the user must provide a secondary form of authentication to access the meeting content from a resource device account. Meeting content is defined as files that are shared to the Content Bin - files that have been attached to the meeting. | `NotRequired`, `RequiredOutsideScheduleMeeting`, `AlwaysRequired` |
| ResourceAccountContentAccess | Write | String | Require a secondary form of authentication to access meeting content. | `NoAccess`, `PartialAccess`, `FullAccess` |
| RestrictedSenderList | Write | StringArray\[\] | Senders domains can be further restricted to ensure that only allowed SMTP domains can send emails to the Teams channels. This is a comma-separated string of the domains you'd like to allow to send emails to Teams channels. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## complianceRecordingPolicy resource type

### Description

Creates a new Teams recording policy for governing automatic policy-based recording in your tenant. Automatic policy-based recording is only applicable to Microsoft Teams users.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier of the application instance of a policy-based recording application to be retrieved. | - |
| ComplianceRecordingApplications | Write | StringArray\[\] | A list of application instances of policy-based recording applications to assign to this policy. The Id of each of these application instances must be the ObjectId of the application instance as obtained by the Get-CsOnlineApplicationInstance cmdlet. | - |
| Description | Write | String | Enables administrators to provide explanatory text to accompany a Teams recording policy. For example, the Description might include information about the users the policy should be assigned to. | - |
| DisableComplianceRecordingAudioNotificationForCalls | Write | Boolean | Setting this attribute to true disables recording audio notifications for 1:1 calls that are under compliance recording. | - |
| Enabled | Write | Boolean | Controls whether this Teams recording policy is active or not. | - |
| WarnUserOnRemoval | Write | Boolean | This parameter is reserved for future use. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## cortanaPolicy resource type

### Description

The CsTeamsCortanaPolicy resources enable administrators to control settings for Cortana voice assistant in Microsoft Teams.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier for Teams cortana policy you're creating. | - |
| CortanaVoiceInvocationMode | Write | String | The value of this field indicates if Cortana is enabled and mode of invocation. | `Disabled`, `PushToTalkUserOverride`, `WakeWordPushToTalkUserOverride` |
| Description | Write | String | Provide a description of your policy to identify purpose of creating it. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## dialInConferencingTenantSettings resource type

### Description

This resource configures a [Teams User's Calling Settings](https://learn.microsoft.com/en-us/microsoftteams/user-call-settings).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only accepted value is Yes. | `Yes` |
| AllowPSTNOnlyMeetingsByDefault | Write | Boolean | Specifies the default value that gets assigned to the 'AllowPSTNOnlyMeetings' setting of users when they are enabled for dial-in conferencing, or when a user's dial-in conferencing provider is set to Microsoft. If set to $true, the 'AllowPSTNOnlyMeetings' setting of the user will also be set to true. If $false, the user setting will be false. The default value for AllowPSTNOnlyMeetingsByDefault is $false. | - |
| AutomaticallyMigrateUserMeetings | Write | Boolean | Automatically Migrate User Meetings. | - |
| AutomaticallyReplaceAcpProvider | Write | Boolean | Automatically replace ACP Provider. | - |
| AutomaticallySendEmailsToUsers | Write | Boolean | Specifies whether advisory emails will be sent to users when the events listed below occur. Setting the parameter to $true enables the emails to be sent, $false disables the emails. The default is $true. | - |
| EnableDialOutJoinConfirmation | Write | Boolean | Enable Dial out join confirmation. | - |
| EnableEntryExitNotifications | Write | Boolean | Specifies if, by default, announcements are made as users enter and exit a conference call. Set to $true to enable notifications, $false to disable notifications. The default is $true. | - |
| EntryExitAnnouncementsType | Write | String | Supported entry and exit announcement type. | - |
| MaskPstnNumbersType | Write | String | This parameter allows tenant administrators to configure masking of PSTN participant phone numbers in the roster view for Microsoft Teams meetings enabled for Audio Conferencing, scheduled within the organization. Possible values are MaskedForExternalUsers, MaskedForAllUsers or NoMasking | `MaskedForExternalUsers`, `MaskedForAllUsers`, `NoMasking` |
| PinLength | Write | UInt32 | Specifies the number of digits in the automatically generated PINs. Organizers can enter their PIN to start a meeting they scheduled if they join via phone and are the first person to join. The minimum value is 4, the maximum is 12, and the default is 5. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## emergencyCallingPolicy resource type

### Description

This resource configures the [Teams Emergency Calling Policies](https://learn.microsoft.com/en-us/microsoftteams/manage-emergency-calling-policies).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Emergency Calling Policy. | - |
| Description | Write | String | Description of the Teams Emergency Calling Policy. | - |
| EnhancedEmergencyServiceDisclaimer | Write | String | Allows the tenant administrator to configure a text string, which is shown at the top of the Calls app. | - |
| ExternalLocationLookupMode | Write | String | Enables ExternalLocationLookupMode. This mode allows users to set Emergency addresses for remote locations. | `Disabled`, `Enabled` |
| NotificationDialOutNumber | Write | String | This parameter represents PSTN number which can be dialed out if NotificationMode is set to either of the two Conference values. | - |
| NotificationGroup | Write | String | NotificationGroup is a email list of users and groups to be notified of an emergency call. | - |
| NotificationMode | Write | String | The type of conference experience for security desk notification. | `NotificationOnly`, `ConferenceMuted`, `ConferenceUnMuted` |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## emergencyCallRoutingPolicy resource type

### Description

This resource configures the [Teams Emergency Call Routing Policies](https://learn.microsoft.com/en-us/microsoftteams/manage-emergency-call-routing-policies).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Emergency Call Routing Policy. | - |
| Description | Write | String | Description of the Teams Emergency Call Routing Policy. | - |
| EmergencyNumbers | Write | MSFT\_TeamsEmergencyNumber\[\] | Emergency number\(s\) associated with the policy. | - |
| AllowEnhancedEmergencyServices | Write | Boolean | Flag to enable Enhanced Emergency Services | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_TeamsEmergencyNumber

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| EmergencyDialString | Write | String | Specifies the emergency phone number. | - |
| EmergencyDialMask | Write | String | For each Teams emergency number, you can specify zero or more emergency dial masks. A dial mask is a number that you want to translate into the value of the emergency dial number value when it's dialed. | - |
| OnlinePSTNUsage | Write | String | Specify the online public switched telephone network \(PSTN\) usage | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## enhancedEncryptionPolicy resource type

### Description

Use this resource to create a new Teams enhanced encryption policy.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier assigned to the Teams enhanced encryption policy. | - |
| CallingEndtoEndEncryptionEnabledType | Write | String | Determines whether End-to-end encrypted calling is available for the user in Teams. Set this to DisabledUserOverride to allow user to turn on End-to-end encrypted calls. Set this to Disabled to prohibit. | - |
| Description | Write | String | Enables administrators to provide explanatory text to accompany a Teams enhanced encryption policy. | - |
| MeetingEndToEndEncryption | Write | String | N/A | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## eventsPolicy resource type

### Description

This resource configures the Teams Events Policies.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Events Policy. | - |
| Description | Write | String | Description of the Teams Events Policy. | - |
| AllowEmailEditing | Write | String | This setting governs if a user is allowed to edit the communication emails in Teams Town Hall or Teams Webinar events. | `Disabled`, `Enabled` |
| AllowEventIntegrations | Write | Boolean | This setting governs access to the integrations tab in the event creation workflow. | - |
| AllowWebinars | Write | String | Determines if webinars are allowed by the policy or not. | `Disabled`, `Enabled` |
| AllowTownhalls | Write | String | This setting governs if a user can create town halls using Teams Events. | `Disabled`, `Enabled` |
| AllowedQuestionTypesInRegistrationForm | Write | String | This setting governs which users in a tenant can add which registration form questions to an event registration page for attendees to answer when registering for the event. | `DefaultOnly`, `DefaultAndPredefinedOnly`, `AllQuestions` |
| AllowedTownhallTypesForRecordingPublish | Write | String | This setting describes how IT admins can control which types of Town Hall attendees can have their recordings published. | `None`, `InviteOnly`, `EveryoneInCompanyIncludingGuests`, `Everyone` |
| AllowedWebinarTypesForRecordingPublish | Write | String | This setting describes how IT admins can control which types of webinar attendees can have their recordings published. | `None`, `InviteOnly`, `EveryoneInCompanyIncludingGuests`, `Everyone` |
| EventAccessType | Write | String | Defines who is allowed to join the event. | `Everyone`, `EveryoneInCompanyExcludingGuests` |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |
| TownhallChatExperience | Write | String | This setting governs whether the user can enable the Comment Stream chat experience for Town Halls. | `Optimized`, `None` |
| UseMicrosoftECDN | Write | Boolean | This setting governs whether the global admin disables this property and prevents the organizers from creating town halls that use Microsoft eCDN even though they have been assigned a Teams Premium license. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## federationConfiguration resource type

### Description

This resource is used to configure the Teams Federation Configuration \(CsTenantFederationConfiguration\). In the Teams admin center this is available in 'External access' in the Users section.

For more information see [Manage external meetings and chat with people and organizations using Microsoft identities](https://learn.microsoft.com/en-us/microsoftteams/manage-external-access).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The only valid input is Global - the tenant wide configuration | `Global` |
| AllowFederatedUsers | Write | Boolean | When set to True users will be potentially allowed to communicate with users from other domains. | - |
| AllowedDomains | Write | StringArray\[\] | List of federated domains to allow. | - |
| BlockedDomains | Write | StringArray\[\] | List of federated domains to block. | - |
| AllowPublicUsers | Write | Boolean | When set to True users will be potentially allowed to communicate with users who have accounts on public IM and presence providers. | - |
| AllowTeamsConsumer | Write | Boolean | Allows federation with people using Teams with an account that's not managed by an organization. | - |
| AllowTeamsConsumerInbound | Write | Boolean | Allows people using Teams with an account that's not managed by an organization, to discover and start communication with users in your organization. | - |
| ExternalAccessWithTrialTenants | Write | String | When set to Blocked, all external access with users from Teams subscriptions that contain only trial licenses will be blocked. This means users from these trial-only tenants will not be able to reach to your users via chats, Teams calls, and meetings \(using the users authenticated identity\) and your users will not be able to reach users in these trial-only tenants. If this setting is set to Blocked, users from the trial-only tenant will also be removed from existing chats. | `Allowed`, `Blocked` |
| TreatDiscoveredPartnersAsUnverified | Write | Boolean | When set to True, messages sent from discovered partners are considered unverified. That means that those messages will be delivered only if they were sent from a person who is on the recipient's Contacts list. | - |
| SharedSipAddressSpace | Write | Boolean | When set to True, indicates that the users homed on Skype for Business Online use the same SIP domain as users homed on the on-premises version of Skype for Business Server. | - |
| RestrictTeamsConsumerToExternalUserProfiles | Write | Boolean | When set to True, Teamsconsumer have access only to external user profiles | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## feedbackPolicy resource type

### Description

This resource configures a Teams Feedback Policy.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specify the name of the Teams Feedback Policy. | - |
| UserInitiatedMode | Write | String | Specifies if users are allowed to give feedback. | - |
| ReceiveSurveysMode | Write | String | Specifies if users are allowed to receive the survey. | `Enabled`, `Disabled`, `EnabledUserOverride` |
| AllowScreenshotCollection | Write | Boolean | Specifies if Screenshot Collection is enabled or not. | - |
| AllowEmailCollection | Write | Boolean | Specifies if Email Collection is enabled or not. | - |
| AllowLogCollection | Write | Boolean | Specifies if Log Collection is enabled or not. | - |
| EnableFeatureSuggestions | Write | Boolean | Specifies if users are allowed to provide feature suggestions | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## filesPolicy resource type

### Description

This resource configures a Teams Files Policy.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specifies the policy instance name | - |
| NativeFileEntryPoints | Write | String | Specifies whether users see the options to upload files from OneDrive for Business, other cloud storage services configured for the user account, and SharePoint Online | `Enabled`, `Disabled` |
| SPChannelFilesTab | Write | String | Specifies whether users see the Teams Files channel tab in any channel or in Teams chat. | `Enabled`, `Disabled` |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## groupPolicyAssignment resource type

### Description

This resource is used to assign Teams policy to a specified group

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| GroupDisplayName | Key | String | Group Displayname of the group the policys are assigned to | - |
| GroupId | Write | String | GroupId, alternatively to Group Displayname | - |
| PolicyType | Key | String | Teams PolicyType. The type of the policy to be assigned. Possible values: | `ApplicationAccessPolicy`, `CallingLineIdentity`, `OnlineAudioConferencingRoutingPolicy`, `OnlineVoicemailPolicy`, `OnlineVoiceRoutingPolicy`, `TeamsAudioConferencingPolicy`, `TeamsCallHoldPolicy`, `TeamsCallParkPolicy`, `TeamsChannelsPolicy`, `TeamsComplianceRecordingPolicy`, `TeamsCortanaPolicy`, `TeamsEmergencyCallingPolicy`, `TeamsEnhancedEncryptionPolicy`, `TeamsFeedbackPolicy`, `TeamsFilesPolicy`, `TeamsIPPhonePolicy`, `TeamsMediaLoggingPolicy`, `TeamsMeetingBroadcastPolicy`, `TeamsMeetingPolicy`, `TeamsMessagingPolicy`, `TeamsMobilityPolicy`, `TeamsRoomVideoTeleConferencingPolicy`, `TeamsShiftsPolicy`, `TeamsUpdateManagementPolicy`, `TeamsVdiPolicy`, `TeamsVideoInteropServicePolicy`, `TenantDialPlan`, `ExternalAccessPolicy`, `TeamsAppSetupPolicy`, `TeamsCallingPolicy`, `TeamsEventsPolicy`, `TeamsMeetingBrandingPolicy`, `TeamsMeetingTemplatePermissionPolicy`, `TeamsVerticalPackagePolicy` |
| PolicyName | Write | String | Teams PolicyName. The name of the policy to be assigned. | - |
| Priority | Write | String | Teams Priority. The rank of the policy assignment, relative to other group policy assignments for the same policy type | - |
| Ensure | Write | String | Present ensures the group policy assignment exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## guestCallingConfiguration resource type

### Description

This resource is used to configure the [Teams guest calling configuration](https://learn.microsoft.com/en-us/microsoftteams/set-up-guests).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The only valid input is Global - the tenant wide configuration | `Global` |
| AllowPrivateCalling | Required | Boolean | Designates whether guests who have been enabled for Teams can use calling functionality. If $false, guests can't call. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## guestMeetingConfiguration resource type

### Description

This resource is used to configure the [Teams Guest Meetings Configuration](https://learn.microsoft.com/en-us/microsoftteams/set-up-guests).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The only valid input is Global - the tenant wide configuration | `Global` |
| AllowIPVideo | Write | Boolean | Determines whether video is enabled in a user's meetings or calls. Set this to TRUE to allow guests to share their video. Set this to FALSE to prohibit guests from sharing their video. | - |
| LiveCaptionsEnabledType | Write | String | Determines whether real-time captions are available for guests in Teams meetings. | `Disabled`, `DisabledUserOverride` |
| ScreenSharingMode | Write | String | Determines the mode in which guests can share a screen in calls or meetings. Set this to SingleApplication to allow the user to share an application at a given point in time. Set this to EntireScreen to allow the user to share anything on their screens. Set this to Disabled to prohibit the user from sharing their screens. | `Disabled`, `EntireScreen`, `SingleApplication` |
| AllowMeetNow | Write | Boolean | Determines whether guests can start ad-hoc meetings. Set this to TRUE to allow guests to start ad-hoc meetings. Set this to FALSE to prohibit guests from starting ad-hoc meetings. | - |
| AllowTranscription | Write | Boolean | Determines whether guests can enable post-meeting captions and transcriptions in meetings. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## guestMessagingConfiguration resource type

### Description

This resource is used to configure the [Teams Guest Messaging Configuration](https://learn.microsoft.com/en-us/microsoftteams/set-up-guests).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The only valid input is Global - the tenant wide configuration | `Global` |
| AllowUserEditMessage | Write | Boolean | Determines if a user is allowed to edit their own messages. | - |
| AllowUserDeleteMessage | Write | Boolean | Determines if a user is allowed to delete their own messages. | - |
| AllowUserChat | Write | Boolean | Determines if a user is allowed to chat. | - |
| AllowUserDeleteChat | Write | Boolean | Turn this setting on to allow users to permanently delete their one-on-one chat, group chat, and meeting chat as participants \(this deletes the chat only for them, not other users in the chat\). | - |
| GiphyRatingType | Write | String | Determines Giphy content restrictions. Default value is Moderate, other options are Strict and NoRestriction. | `Moderate`, `Strict`, `NoRestriction` |
| AllowMemes | Write | Boolean | Determines if memes are available for use. | - |
| AllowStickers | Write | Boolean | Determines if stickers are available for use. | - |
| AllowGiphy | Write | Boolean | Determines if Giphy are available for use. | - |
| AllowImmersiveReader | Write | Boolean | Determines if Immersive Reader is enabled. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## ipPhonePolicy resource type

### Description

New-CsTeamsIPPhonePolicy allows you to create a policy to manage features related to Teams phone experiences. Teams phone policies determine the features that are available to users.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specifies the policy instance name | - |
| AllowBetterTogether | Write | String | Determines whether Better Together mode is enabled, phones can lock and unlock in an integrated fashion when connected to their Windows PC running a 64-bit Teams desktop client. | `Enabled`, `Disabled` |
| AllowHomeScreen | Write | String | Determines whether the Home Screen feature of the Teams IP Phones is enabled. | `Enabled`, `EnabledUserOverride`, `Disabled` |
| AllowHotDesking | Write | Boolean | Determines whether hot desking mode is enabled. | - |
| Description | Write | String | Specifies the description of the policy | - |
| HotDeskingIdleTimeoutInMinutes | Write | UInt64 | Determines the idle timeout value in minutes for the signed in user account. When the timeout is reached, the account is logged out. | - |
| SearchOnCommonAreaPhoneMode | Write | String | Determines whether a user can search the Global Address List in Common Area Phone Mode. | `Enabled`, `Disabled` |
| SignInMode | Write | String | Determines the sign in mode for the device when signing in to Teams. | `UserSignIn`, `CommonAreaPhoneSignIn`, `MeetingSignIn` |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## meetingBroadcastConfiguration resource type

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The only valid input is Global - the tenant wide configuration | `Global` |
| SupportURL | Write | String | Specifies a URL where broadcast event attendees can find support information or FAQs specific to that event. The URL will be displayed to the attendees during the broadcast. | - |
| AllowSdnProviderForBroadcastMeeting | Write | Boolean | If set to $true, Teams meeting broadcast streams are enabled to take advantage of the network and bandwidth management capabilities of your Software Defined Network \(SDN\) provider. | - |
| SdnProviderName | Write | String | Specifies the Software Defined Network \(SDN\) provider's name. This parameter is only required if AllowSdnProviderForBroadcastMeeting is set to $true. | - |
| SdnLicenseId | Write | String | Specifies the Software Defined Network \(SDN\) license identifier. This is required and provided by some SDN providers. This parameter is only required if AllowSdnProviderForBroadcastMeeting is set to $true. | - |
| SdnApiTemplateUrl | Write | String | Specifies the Software Defined Network \(SDN\) provider's HTTP API endpoint. This information is provided to you by the SDN provider. This parameter is only required if AllowSdnProviderForBroadcastMeeting is set to $true. | - |
| SdnApiToken | Write | String | Specifies the Software Defined Network \(SDN\) provider's authentication token which is required to use their SDN license. This is required by some SDN providers who will give you the required token. This parameter is only required if AllowSdnProviderForBroadcastMeeting is set to $true. | - |

#### Description

This resource is used to configure the [Teams Meeting Broadcast Settings](https://learn.microsoft.com/en-us/microsoftteams/teams-live-events/configure-teams-live-events).

#### Permissions

##### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## meetingBroadcastPolicy resource type

### Description

This resource is used to configure the [Teams Meeting Broadcast Policies](https://learn.microsoft.com/en-us/microsoftteams/teams-live-events/set-up-for-teams-live-events).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The identifier of the Teams Meeting Broadcast Policy. | - |
| AllowBroadcastScheduling | Write | Boolean | Specifies whether this user can create broadcast events in Teams. This settng impacts broadcasts that use both self-service and external encoder production methods. | - |
| AllowBroadcastTranscription | Write | Boolean | Specifies whether real-time transcription and translation can be enabled in the broadcast event. Note: this setting is applicable to broadcast events that use Teams Meeting production only and does not apply when external encoder is used as production method. | - |
| BroadcastAttendeeVisibilityMode | Write | String | Specifies the attendee visibility mode of the broadcast events created by this user. This setting controls who can watch the broadcast event - e.g. anyone can watch this event including anonymous users or only authenticated users in my company can watch the event. Note: this setting is applicable to broadcast events that use Teams Meeting production only and does not apply when external encoder is used as production method. | `Everyone`, `EveryoneInCompany`, `InvitedUsersInCompany`, `EveryoneInCompanyAndExternal`, `InvitedUsersInCompanyAndExternal` |
| BroadcastRecordingMode | Write | String | Specifies whether broadcast events created by this user are always recorded, never recorded or user can choose whether to record or not. Note: this setting is applicable to broadcast events that use Teams Meeting production only and does not apply when external encoder is used as production method. | `AlwaysEnabled`, `AlwaysDisabled`, `UserOverride` |
| Ensure | Write | String | Present ensures the Policy exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## meetingConfiguration resource type

### Description

This resource is used to configure the [Teams Meeting Configuration](https://learn.microsoft.com/en-us/microsoftteams/meeting-settings-in-teams).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The only valid input is Global - the tenant wide configuration | `Global` |
| LogoURL | Write | String | URL to a logo image. This would be included in the meeting invite. Please ensure this URL is publicly accessible for invites that go beyond your federation boundaries. | - |
| LegalURL | Write | String | URL to a website containing legal information and meeting disclaimers. This would be included in the meeting invite. Please ensure this URL is publicly accessible for invites that go beyond your federation boundaries. | - |
| HelpURL | Write | String | URL to a website where users can obtain assistance on joining the meeting.This would be included in the meeting invite. Please ensure this URL is publicly accessible for invites that go beyond your federation boundaries. | - |
| CustomFooterText | Write | String | Text to be used on custom meeting invitations. | - |
| DisableAnonymousJoin | Write | Boolean | Determines whether anonymous users are blocked from joining meetings in the tenant. Set this to TRUE to block anonymous users from joining. Set this to FALSE to allow anonymous users to join meetings. | - |
| EnableQoS | Write | Boolean | Determines whether Quality of Service Marking for real-time media \(audio, video, screen/app sharing\) is enabled in the tenant. Set this to TRUE to enable and FALSE to disable. | - |
| ClientAudioPort | Write | UInt32 | Determines the starting port number for client audio. Minimum allowed value: 1024 Maximum allowed value: 65535 Default value: 50000. | - |
| ClientAudioPortRange | Write | UInt32 | Determines the total number of ports available for client audio. Default value is 20. | - |
| ClientVideoPort | Write | UInt32 | Determines the starting port number for client video. Minimum allowed value: 1024 Maximum allowed value: 65535 Default value: 50020. | - |
| ClientVideoPortRange | Write | UInt32 | Determines the total number of ports available for client video. Default value is 20. | - |
| ClientAppSharingPort | Write | UInt32 | Determines the starting port number for client screen sharing or application sharing. Minimum allowed value: 1024 Maximum allowed value: 65535 Default value: 50040. | - |
| ClientMediaPortRangeEnabled | Write | Boolean | Determines whether custom media port and range selections need to be enforced. When set to True, clients will use the specified port range for media traffic. When set to False \(the default value\) for any available port \(from port 1024 through port 65535\) will be used to accommodate media traffic. | - |
| ClientAppSharingPortRange | Write | UInt32 | Determines the total number of ports available for client sharing or application sharing. Default value is 20. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## meetingPolicy resource type

### Description

This resource configures the [Teams Meeting Policies](https://learn.microsoft.com/en-us/microsoftteams/meeting-policies-overview).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Meeting Policy. | - |
| Description | Write | String | Description of the Teams Meeting Policy. | - |
| AllowChannelMeetingScheduling | Write | Boolean | Determines whether a user can schedule channel meetings. Set this to TRUE to allow a user to schedule channel meetings. Set this to FALSE to prohibit the user from scheduling channel meetings. Note this only restricts from scheduling and not from joining a meeting scheduled by another user. | - |
| AllowMeetNow | Write | Boolean | Determines whether a user can start ad-hoc meetings. Set this to TRUE to allow a user to start ad-hoc meetings. Set this to FALSE to prohibit the user from starting ad-hoc meetings. | - |
| AllowPrivateMeetNow | Write | Boolean | Determines whether a user can start private ad-hoc meetings. Set this to TRUE to allow a user to start private ad-hoc meetings. Set this to FALSE to prohibit the user from starting private ad-hoc meetings. | - |
| MeetingChatEnabledType | Write | String | Determines whether or not Chat will be enabled, enabled except anonymous or disabled for meetings. | `Disabled`, `Enabled`, `EnabledExceptAnonymous` |
| LiveCaptionsEnabledType | Write | String | Determines whether a user should have the option to view live captions or not in a meeting. | `Disabled`, `DisabledUserOverride` |
| AllowIPAudio | Write | Boolean | Determines whether audio is enabled in a user's meetings or calls. Set this to TRUE to allow the user to share their audioo. Set this to FALSE to prohibit the user from sharing their audio. | - |
| AllowIPVideo | Write | Boolean | Determines whether video is enabled in a user's meetings or calls. Set this to TRUE to allow the user to share their video. Set this to FALSE to prohibit the user from sharing their video. | - |
| AllowEngagementReport | Write | String | Determines whether or not a meeting Organizer can track join and leave times for all users within their meetings as well as download a roster. | `Enabled`, `Disabled` |
| IPAudioMode | Write | String | Determines whether or not a user can use audio in a meeting that supports it. | `EnabledOutgoingIncoming`, `Disabled` |
| IPVideoMode | Write | String | Determines whether or not a user can use video in a meeting that supports it. Can only be enabled if IPAudioMode is enabled | `EnabledOutgoingIncoming`, `Disabled` |
| AllowAnonymousUsersToDialOut | Write | Boolean | CURRENTLY DISABLED: Determines whether anonymous users can use the Call Me At feature for meeting audio. | - |
| AllowAnonymousUsersToStartMeeting | Write | Boolean | Determines whether anonymous users can initiate a meeting. Set this to TRUE to allow anonymous users to initiate a meeting. Set this to FALSE to prohibit them from initiating a meeting. | - |
| AllowPrivateMeetingScheduling | Write | Boolean | Determines whether a user can schedule private meetings. Set this to TRUE to allow a user to schedule private meetings. Set this to FALSE to prohibit the user from scheduling private meetings. Note this only restricts from scheduling and not from joining a meeting scheduled by another user. | - |
| AutoAdmittedUsers | Write | String | Determines what types of participants will automatically be added to meetings organized by this user. Set this to EveryoneInCompany if you would like meetings to place every external user in the lobby but allow all users in the company to join the meeting immediately. Set this to Everyone if you'd like to admit anonymous users by default. Set this to EveryoneInSameAndFederatedCompany if you would like meetings to allow federated users to join like your company's users, but place all other external users in a lobby. Set this to InvitedUsers if you would like meetings to allow only the invited users. | `EveryoneInCompany`, `Everyone`, `EveryoneInSameAndFederatedCompany`, `OrganizerOnly`, `InvitedUsers`, `EveryoneInCompanyExcludingGuests` |
| AllowPSTNUsersToBypassLobby | Write | Boolean | Determines whether PSTN users should be automatically admitted to the meetings. Set this to TRUE to allow the PSTN user to be able bypass the meetinglobby. Set this to FALSE to prohibit the PSTN user from bypassing the meetinglobby. | - |
| AllowCloudRecording | Write | Boolean | Determines whether cloud recording is allowed in a user's meetings. Set this to TRUE to allow the user to be able to record meetings. Set this to FALSE to prohibit the user from recording meetings. | - |
| AllowRecordingStorageOutsideRegion | Write | Boolean | Determines whether cloud recording can be stored out of region for go-local tenants where recording is not yet enabled. | - |
| DesignatedPresenterRoleMode | Write | String | Determines if users can change the default value of the Who can present? setting in Meeting options in the Teams client. This policy setting affects all meetings, including Meet Now meetings. | `OrganizerOnlyUserOverride`, `EveryoneInCompanyUserOverride`, `EveryoneUserOverride` |
| AllowOutlookAddIn | Write | Boolean | Determines whether a user can schedule Teams Meetings in Outlook desktop client. Set this to TRUE to allow the user to be able to schedule Teams meetings in Outlook client. Set this to FALSE to prohibit a user from scheduling Teams meeting in Outlook client. | - |
| AllowPowerPointSharing | Write | Boolean | Determines whether Powerpoint sharing is allowed in a user's meetings. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| AllowParticipantGiveRequestControl | Write | Boolean | Determines whether participants can request or give control of screen sharing during meetings scheduled by this user. Set this to TRUE to allow the user to be able to give or request control. Set this to FALSE to prohibit the user from giving, requesting control in a meeting. | - |
| AllowExternalParticipantGiveRequestControl | Write | Boolean | Determines whether external participants can request or give control of screen sharing during meetings scheduled by this user. Set this to TRUE to allow the user to be able to give or request control. Set this to FALSE to prohibit an external user from giving or requesting control in a meeting. | - |
| AllowSharedNotes | Write | Boolean | Determines whether users are allowed to take shared notes. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| AllowWhiteboard | Write | Boolean | Determines whether whiteboard is allowed in a user's meetings. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| AllowTranscription | Write | Boolean | Determines whether real-time and/or post-meeting captions and transcriptions are allowed in a user's meetings. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| MediaBitRateKb | Write | UInt32 | Determines the media bit rate for audio/video/app sharing transmissions in meetings. | - |
| ScreenSharingMode | Write | String | Determines the mode in which a user can share a screen in calls or meetings. Set this to SingleApplication to allow the user to share an application at a given point in time. Set this to EntireScreen to allow the user to share anything on their screens. Set this to Disabled to prohibit the user from sharing their screens. | `SingleApplication`, `EntireScreen`, `Disabled` |
| VideoFiltersMode | Write | String | Determines which background filters are available to meeting attendees. | `NoFilters`, `BlurOnly`, `BlurAndDefaultBackgrounds`, `AllFilters` |
| AllowOrganizersToOverrideLobbySettings | Write | Boolean | Determines whether organizers can override lobby settings for both VOIP and PSTN. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| PreferredMeetingProviderForIslandsMode | Write | String | Determines which Outlook Add-in the user will get as preferred Meeting provider\(TeamsAndSfb or Teams\). | `TeamsAndSfb`, `Teams` |
| AllowNDIStreaming | Write | Boolean | Determines whether a user is able to use NDI \(Network Device Interface\) in meetings - both for output and input streams. | - |
| AllowUserToJoinExternalMeeting | Write | String | Determines what types of external meetings users can join. Enabled is able join all external meetings. | `Enabled`, `FederatedOnly`, `Disabled` |
| EnrollUserOverride | Write | String | Determines whether or not users will be able to enroll/capture their Biometric data: Face & Voice. | `Disabled`, `Enabled` |
| RoomAttributeUserOverride | Write | String | Determines whether or not biometric data will be used to distinguish and or attribute in the transcript. | `Off`, `Distinguish`, `Attribute` |
| StreamingAttendeeMode | Write | String | Determines whether or not meetings created by users with this policy are able to utilize the meeting overflow capability. | `Disabled`, `Enabled` |
| AllowBreakoutRooms | Write | Boolean | Determines whether or not meetings created by users with this policy are able to utilize the Breakout Rooms feature. | - |
| TeamsCameraFarEndPTZMode | Write | String | Determines whether or not meetings created by users with this policy are able to utilize the Camera Far-End PTZ Mode. | `Disabled`, `AutoAcceptInTenant`, `AutoAcceptAll` |
| AllowMeetingReactions | Write | Boolean | Determines whether or not meetings created by users with this policy are able to utilize the Meeting Reactions feature. | - |
| WhoCanRegister | Write | String | Specifies who can attend and register for webinars. | `Everyone`, `EveryoneInCompany` |
| AllowAnnotations | Write | Boolean | N/A | - |
| AllowAnonymousUsersToJoinMeeting | Write | Boolean | Determines whether anonymous users can join the meetings that impacted users organize. Set this to TRUE to allow anonymous users to join a meeting. Set this to FALSE to prohibit them from joining a meeting. | - |
| AllowMeetingCoach | Write | Boolean | N/A | - |
| AllowMeetingRegistration | Write | Boolean | Controls if a user can create a webinar meeting. The default value is True. | - |
| AllowNetworkConfigurationSettingsLookup | Write | Boolean | Determines whether network configuration setting lookups can be made by users who are not Enterprise Voice enabled. It's used to enable Network Roaming policies. | - |
| AllowWatermarkForCameraVideo | Write | Boolean | N/A | - |
| AllowWatermarkForScreenSharing | Write | Boolean | N/A | - |
| NewMeetingRecordingExpirationDays | Write | SInt32 | Specifies the number of days before meeting recordings will expire and move to the recycle bin. Value can be from 1 to 99,999 days. NOTE: You may opt to set Meeting Recordings to never expire by entering the value -1. | - |
| AllowCartCaptionsScheduling | Write | String | Determines whether a user can add a URL for captions from a Communications Access Real-Time Translation \(CART\) captioner for providing real-time captions in meetings. | `EnabledUserOverride`, `DisabledUserOverride`, `Disabled` |
| AllowDocumentCollaboration | Write | String | N/A | - |
| AllowedStreamingMediaInput | Write | String | N/A | - |
| BlockedAnonymousJoinClientTypes | Write | String | A user can join a Teams meeting anonymously using a Teams client or using a custom application built using Azure Communication Services. When anonymous meeting join is enabled, both types of clients may be used by default. This optional parameter can be used to block one of the client types that can be used. The allowed values are ACS \(to block the use of Azure Communication Services clients\) or Teams \(to block the use of Teams clients\). Both can also be specified, separated by a comma, but this is equivalent to disabling anonymous join completely. | - |
| ChannelRecordingDownload | Write | String | Determines how channel meeting recordings are saved, permissioned, and who can download them. | - |
| ExplicitRecordingConsent | Write | String | N/A | - |
| ForceStreamingAttendeeMode | Write | String | N/A | - |
| InfoShownInReportMode | Write | String | N/A | - |
| LiveInterpretationEnabledType | Write | String | Determines how meeting organizers can configure a meeting for language interpretation, select attendees of the meeting to become interpreters that other attendees can select and listen to the real-time translation they provide. | - |
| LiveStreamingMode | Write | String | Determines whether you provide support for your users to stream their Teams meetings to large audiences through Real-Time Messaging Protocol \(RTMP\). | `Disabled`, `Enabled` |
| MeetingInviteLanguages | Write | String | Controls how the join information in meeting invitations is displayed by enforcing a common language or enabling up to two languages to be displayed. Note: All Teams supported languages can be specified using language codes. | - |
| QnAEngagementMode | Write | String | N/A | - |
| RoomPeopleNameUserOverride | Write | String | N/A | - |
| SpeakerAttributionMode | Write | String | Possible values: EnabledUserOverride or Disabled. | `Disabled`, `EnabledUserOverride` |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## messagingPolicy resource type

### Description

This resource is used to configure the [Teams messaging policy](https://learn.microsoft.com/en-us/microsoftteams/messaging-policies-in-teams).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity for the teams messaging policy you're modifying. To modify the global policy, use this syntax: -Identity global. To modify a per-user policy, use syntax similar to this: -Identity TeamsMessagingPolicy. | - |
| AllowCommunicationComplianceEndUserReporting | Write | Boolean | Report inappropriate content. | - |
| AllowFluidCollaborate | Write | Boolean | Determines is Fluid Collaboration should be enabled or not. | - |
| AllowSecurityEndUserReporting | Write | Boolean | Report a security concern. | - |
| AllowGiphy | Write | Boolean | Determines whether a user is allowed to access and post Giphys. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowMemes | Write | Boolean | Determines whether a user is allowed to access and post memes. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowOwnerDeleteMessage | Write | Boolean | Determines whether owners are allowed to delete all the messages in their team. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| AllowUserEditMessage | Write | Boolean | Determines whether a user is allowed to edit their own messages. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| AllowSmartCompose | Write | Boolean | Turn on this setting to let a user get text predictions for chat messages. | - |
| AllowSmartReply | Write | Boolean | Turn this setting on to enable suggested replies for chat messages. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| AllowStickers | Write | Boolean | Determines whether a user is allowed to access and post stickers. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowUrlPreviews | Write | Boolean | Use this setting to turn automatic URL previewing on or off in messages. Set this to TRUE to turn on. Set this to FALSE to turn off. | - |
| AllowUserChat | Write | Boolean | Determines whether a user is allowed to chat. Set this to TRUE to allow a user to chat across private chat, group chat and in meetings. Set this to FALSE to prohibit all chat. | - |
| AllowUserDeleteMessage | Write | Boolean | Determines whether a user is allowed to delete their own messages. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| AllowUserTranslation | Write | Boolean | Determines whether a user is allowed to translate messages to their client languages. Set this to TRUE to allow. Set this to FALSE to prohibit. | - |
| AllowImmersiveReader | Write | Boolean | Determines whether a user is allowed to use Immersive Reader for reading conversation messages. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowRemoveUser | Write | Boolean | Determines whether a user is allowed to remove a user from a conversation. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowPriorityMessages | Write | Boolean | Determines whether a user is allowed to send priorities messages. Set this to TRUE to allow. Set this FALSE to prohibit. | - |
| AllowUserDeleteChat | Write | Boolean | Turn this setting on to allow users to permanently delete their 1:1, group chat, and meeting chat as participants \(this deletes the chat only for them, not other users in the chat\). | - |
| AllowVideoMessages | Write | Boolean | Determines whether a user is allowed to send video messages in Chat. Set this to TRUE to allow a user to send video messages. Set this to FALSE to prohibit sending video messages. | - |
| Description | Write | String | Provide a description of your policy to identify purpose of creating it. | - |
| GiphyRatingType | Write | String | Determines the Giphy content restrictions applicable to a user. Set this to STRICT, MODERATE or NORESTRICTION. | `STRICT`, `MODERATE`, `NORESTRICTION` |
| ReadReceiptsEnabledType | Write | String | Use this setting to specify whether read receipts are user controlled, enabled for everyone, or disabled. Set this to UserPreference, Everyone or None. | `UserPreference`, `Everyone`, `None` |
| ChannelsInChatListEnabledType | Write | String | Possible values are: DisabledUserOverride,EnabledUserOverride. | `DisabledUserOverride`, `EnabledUserOverride` |
| AudioMessageEnabledType | Write | String | Determines whether a user is allowed to send audio messages. Possible values are: ChatsAndChannels,ChatsOnly,Disabled. | `ChatsAndChannels`, `ChatsOnly`, `Disabled` |
| Tenant | Write | String | Globally unique identifier \(GUID\) of the tenant account whose external user communication policy are being created. | - |
| Ensure | Write | String | Present ensures the Team Message Policy exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## mobilityPolicy resource type

### Description

The TeamsMobilityPolicy allows Admins to control Teams mobile usage for users.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specify the name of the Teams Mobility Policy. | - |
| Description | Write | String | Enables administrators to provide explanatory text about the policy. For example, the Description might indicate the users the policy should be assigned to. | - |
| IPAudioMobileMode | Write | String | When set to WifiOnly, prohibits the user from making and receiving calls or joining meetings using VoIP calls on the mobile device while on a cellular data connection. Possible values are: WifiOnly, AllNetworks. | `WifiOnly`, `AllNetworks` |
| IPVideoMobileMode | Write | String | When set to WifiOnly, prohibits the user from making and receiving video calls or enabling video in meetings using VoIP calls on the mobile device while on a cellular data connection. Possible values are: WifiOnly, AllNetworks. | `WifiOnly`, `AllNetworks` |
| MobileDialerPreference | Write | String | Determines the mobile dialer preference, possible values are: Teams, Native, UserOverride. | `Teams`, `Native`, `UserOverride` |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## networkRoamingPolicy resource type

### Description

New-CsTeamsNetworkRoamingPolicy allows IT Admins to create policies for Network Roaming and Bandwidth Control experiences in Microsoft Teams.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specify the name of the Teams Network Roaming Policy. | - |
| AllowIPVideo | Write | Boolean | Determines whether video is enabled in a user's meetings or calls. Set this to TRUE to allow the user to share their video. Set this to FALSE to prohibit the user from sharing their video. | - |
| Description | Write | String | Description of the new policy to be created. | - |
| MediaBitRateKb | Write | UInt64 | Determines the media bit rate for audio/video/app sharing transmissions in meetings. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## onlineVoicemailPolicy resource type

### Description

This resource configures the [Teams Online Voicemail Policies](https://learn.microsoft.com/en-us/microsoftteams/manage-voicemail-policies).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Online Voicemail Policy. | - |
| EnableEditingCallAnswerRulesSetting | Write | Boolean | Controls if editing call answer rule settings are enabled or disabled for a user. Possible values are $true or $false. | - |
| EnableTranscription | Write | Boolean | Allows you to disable or enable voicemail transcription. Possible values are $true or $false. | - |
| EnableTranscriptionProfanityMasking | Write | Boolean | Allows you to disable or enable profanity masking for the voicemail transcriptions. Possible values are $true or $false. | - |
| EnableTranscriptionTranslation | Write | Boolean | Allows you to disable or enable translation for the voicemail transcriptions. Possible values are $true or $false. | - |
| MaximumRecordingLength | Write | String | A duration of voicemail maximum recording length. The length should be between 30 seconds to 600 seconds. | - |
| PrimarySystemPromptLanguage | Write | String | The primary \(or first\) language that voicemail system prompts will be presented in. Must also set SecondarySystemPromptLanguage. When set, this overrides the user language choice. | - |
| SecondarySystemPromptLanguage | Write | String | The secondary language that voicemail system prompts will be presented in. Must also set PrimarySystemPromptLanguage and may not be the same value as PrimarySystemPromptanguage. When set, this overrides the user language choice. | - |
| ShareData | Write | String | Specifies whether voicemail and transcription data are shared with the service for training and improving accuracy. Possible values are Defer and Deny. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## onlineVoicemailUserSettings resource type

### Description

This resource configures a Teams User's Online Voicemail Settings.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter represents the ID of the specific user in your organization; this can be either a SIP URI or an Object ID. | - |
| CallAnswerRule | Write | String | The CallAnswerRule parameter represents the value of the call answer rule, which can be any of the following: DeclineCall, PromptOnly, PromptOnlyWithTransfer, RegularVoicemail, VoicemailWithTransferOption. | `DeclineCall`, `PromptOnly`, `PromptOnlyWithTransfer`, `RegularVoicemail`, `VoicemailWithTransferOption` |
| DefaultGreetingPromptOverwrite | Write | String | The DefaultGreetingPromptOverwrite parameter represents the contents that overwrite the default normal greeting prompt. If the user's normal custom greeting is not set and DefaultGreetingPromptOverwrite is not empty, the voicemail service will play this overwrite greeting instead of the default normal greeting in the voicemail deposit scenario. | - |
| DefaultOofGreetingPromptOverwrite | Write | String | The DefaultOofGreetingPromptOverwrite parameter represents the contents that overwrite the default out-of-office greeting prompt. If the user's out-of-office custom greeting is not set and DefaultOofGreetingPromptOverwrite is not empty, the voicemail service will play this overwrite greeting instead of the default out-of-office greeting in the voicemail deposit scenario. | - |
| OofGreetingEnabled | Write | Boolean | The OofGreetingEnabled parameter represents whether to play out-of-office greeting in voicemail deposit scenario. | - |
| OofGreetingFollowAutomaticRepliesEnabled | Write | Boolean | The OofGreetingFollowAutomaticRepliesEnabled parameter represents whether to play out-of-office greeting in voicemail deposit scenario when user set automatic replies in Outlook. | - |
| OofGreetingFollowCalendarEnabled | Write | Boolean | The OofGreetingFollowCalendarEnabled parameter represents whether to play out-of-office greeting in voicemail deposit scenario when user set out-of-office in calendar. | - |
| PromptLanguage | Write | String | The PromptLanguage parameter represents the language that is used to play voicemail prompts. | - |
| ShareData | Write | Boolean | Specifies whether voicemail and transcription data is shared with the service for training and improving accuracy. | - |
| TransferTarget | Write | String | The TransferTarget parameter represents the target to transfer the call when call answer rule set to PromptOnlyWithTransfer or VoicemailWithTransferOption. Value of this parameter should be a SIP URI of another user in your organization. For user with Enterprise Voice enabled, a valid telephone number could also be accepted as TransferTarget. | - |
| VoicemailEnabled | Write | Boolean | The VoicemailEnabled parameter represents whether to enable voicemail service. If set to $false, the user has no voicemail service. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## onlineVoiceUser resource type

### Description

This resource configures the Teams Online Voice User.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specifies the identity of the target user. | - |
| LocationID | Write | String | Specifies the unique identifier of the emergency location to assign to the user. Location identities can be discovered by using the Get-CsOnlineLisLocation cmdlet. | - |
| TelephoneNumber | Write | String | Specifies the telephone number to be assigned to the user. The value must be in E.164 format: +14255043920. Setting the value to $Null clears the user's telephone number. | - |
| Ensure | Write | String | Present ensures the online voice user exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## pstnUsage resource type

### Description

This resource configures a [Teams PSTN Usage](https://learn.microsoft.com/en-us/microsoftteams/direct-routing-voice-routing).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Usage | Key | String | An online PSTN usage \(such as Local or Long Distance\) that can be used in conjunction with voice routes and voice routing policies. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## shiftsPolicy resource type

### Description

This resource allows you to create a new TeamsShiftPolicy instance and set it's properties.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Specifies the policy instance name | - |
| AccessGracePeriodMinutes | Write | UInt64 | Determines the grace period time in minutes between when the first shift starts or last shift ends and when access is blocked | - |
| AccessType | Write | String | Determines the Teams access type granted to the user. Today, only unrestricted access to Teams app is supported. | `UnrestrictedAccess_TeamsApp` |
| EnableScheduleOwnerPermissions | Write | Boolean | Determines whether a user can manage a Shifts schedule as a team member. | - |
| EnableShiftPresence | Write | Boolean | Determines whether a user is given shift-based presence \(On shift, Off shift, or Busy\). This must be set in order to have any off shift warning message-specific settings. | - |
| ShiftNoticeFrequency | Write | String | Determines the frequency of warning dialog displayed when user opens Teams. | `Always`, `ShowOnceOnChange`, `Never` |
| ShiftNoticeMessageCustom | Write | String | Specifies a custom message. Must set ShiftNoticeMessageType to 'CustomMessage' to enforce this | - |
| ShiftNoticeMessageType | Write | String | Specifies the warning message is shown in the blocking dialog when a user access Teams off shift hours. Select one of 7 Microsoft provided messages, a default message or a custom message. | `DefaultMessage`, `Message1`, `Message2`, `Message3`, `Message4`, `Message5`, `Message6`, `Message7`, `CustomMessage` |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## templatesPolicy resource type

### Description

This resource configures a [Teams Templates Policy](https://learn.microsoft.com/en-us/microsoftteams/templates-policies).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Templates Policy. | - |
| Description | Write | String | Description of the Teams Templates Policy. | - |
| HiddenTemplates | Write | StringArray\[\] | The list of Teams templates to hide. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## tenantDialPlan resource type

### Description

This resource is used to configure the [tenant-wide dial plans for Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/create-and-manage-dial-plans).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity parameter is a unique identifier that designates the name of the tenant dial plan. Identity is an alphanumeric string that can't exceed 49 characters. Valid characters are alphabetic or numeric characters, hyphen \(-\) and dot \(.\). The value should not begin with a \(.\). | - |
| Description | Write | String | The Description parameter describes the tenant dial plan - what it's for, what type of user it applies to and any other information that helps to identify the purpose of the tenant dial plan. Maximum characters: 512. | - |
| NormalizationRules | Write | MSFT\_TeamsVoiceNormalizationRule\[\] | List of normalization rules that are applied to this dial plan. | - |
| ExternalAccessPrefix | Write | String | The ExternalAccessPrefix parameter is a number \(or set of numbers\) that designates the call as external to the organization. \(For example, to tenant-dial an outside line, first press 9.\) This prefix is ignored by the normalization rules, although these rules are applied to the remainder of the number. The OptimizeDeviceDialing parameter must be set to True for this value to take effect. This parameter must match the regular expression \[0-9\]{1,4}: that is, it must be a value 0 through 9 and one to four digits in length. The default value is 9. | - |
| OptimizeDeviceDialing | Write | Boolean | Specifies if the dial plan should optimize device dialing or not. | - |
| SimpleName | Write | String | The SimpleName parameter is a display name for the tenant dial plan. This name must be unique among all tenant dial plans within the Skype for Business Server deployment.This string can be up to 49 characters long. Valid characters are alphabetic or numeric characters, hyphen \(-\), dot \(.\) and parentheses \(\(\)\). | - |
| Ensure | Write | String | Specify if this dial plan should exist or not. | `Present`, `Absent` |

#### MSFT\_TeamsVoiceNormalizationRule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Write | String | A unique identifier for the rule. The Identity specified must include the scope followed by a slash and then the name; for example: site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name. The name portion will automatically be stored in the Name property. You can't specify values for Identity and Name in the same command. | - |
| Priority | Write | UInt32 | The order in which rules are applied. A phone number might match more than one rule. This parameter sets the order in which the rules are tested against the number. | - |
| Description | Write | String | A friendly description of the normalization rule. | - |
| Pattern | Write | String | A regular expression that the dialed number must match in order for this rule to be applied. | - |
| Translation | Write | String | The regular expression pattern that will be applied to the number to convert it to E.164 format. | - |
| IsInternalExtension | Write | Boolean | If True, the result of applying this rule will be a number internal to the organization. If False, applying the rule results in an external number. This value is ignored if the value of the OptimizeDeviceDialing property of the associated dial plan is set to False. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## tenantNetworkRegion resource type

### Description

As an Admin, you can use the Windows PowerShell command, New-CsTenantNetworkRegion to define network regions. A network region interconnects various parts of a network across multiple geographic areas. The RegionID parameter is a logical name that represents the geography of the region, and has no dependencies or restrictions. Tenant network region is used for Location Based Routing.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier for the network region to be created. | - |
| CentralSite | Write | String | Name of the associated Central Site. | - |
| Description | Write | String | Provide a description of the network region to identify purpose of creating it. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## tenantNetworkSite resource type

### Description

As an Admin, you can use the Windows PowerShell command, New-CsTenantNetworkSite to define network sites. Network sites are defined as a collection of IP subnets. Each network site must be associated with a network region. Tenant network site is used for Location Based Routing.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier for the network site to be created. | - |
| Description | Write | String | Provide a description of the network site to identify purpose of creating it. | - |
| EmergencyCallingPolicy | Write | String | This parameter is used to assign a custom emergency calling policy to a network site | - |
| EmergencyCallRoutingPolicy | Write | String | This parameter is used to assign a custom emergency call routing policy to a network site | - |
| EnableLocationBasedRouting | Write | Boolean | This parameter determines whether the current site is enabled for location based routing. | - |
| LocationPolicy | Write | String | LocationPolicy is the identifier for the location policy which the current network site is associating to. | - |
| NetworkRegionID | Write | String | NetworkRegionID is the identifier for the network region which the current network site is associating to. | - |
| NetworkRoamingPolicy | Write | String | NetworkRoamingPolicy is the identifier for the network roaming policy to which the network site will associate to. | - |
| SiteAddress | Write | String | The address of current network site. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## tenantNetworkSubnet resource type

### Description

As an Admin, you can use the Windows PowerShell command, New-CsTenantNetworkSubnet to define network subnets and assign them to network sites. Each internal subnet may only be associated with one site. Tenant network subnet is used for Location Based Routing.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| MaskBits | Key | UInt32 | This parameter determines the length of bits to mask to the subnet. IPv4 format subnet accepts maskbits from 0 to 32 inclusive. IPv6 format subnet accepts maskbits from 0 to 128 inclusive. | - |
| Identity | Key | String | Unique identifier for the network subnet to be created. | - |
| Description | Write | String | Provide a description of the network subnet to identify purpose of creating it. | - |
| NetworkSiteID | Write | String | NetworkSiteID is the identifier for the network site which the current network subnet is associating to. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## tenantTrustedIPAddress resource type

### Description

As an Admin, you can use the Windows PowerShell command, New-CsTenantTrustedIPAddress to define external subnets and assign them to the tenant. You can define an unlimited number of external subnets for a tenant.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identifier for the IP address to be created. | - |
| Description | Write | String | Provide a description of the trusted IP address to identify purpose of creating it. | - |
| MaskBits | Write | UInt32 | This parameter determines the length of bits to mask to the subnet. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## translationRule resource type

### Description

Cmdlet to create a new telephone number manipulation rule.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identifier of the rule. This parameter is required and later used to assign the rule to the Inbound or Outbound Trunk Normalization policy. | - |
| Description | Write | String | A friendly description of the normalization rule. | - |
| Pattern | Write | String | A regular expression that caller or callee number must match in order for this rule to be applied. | - |
| Translation | Write | String | The regular expression pattern that will be applied to the number to convert it. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## unassignedNumberTreatment resource type

### Description

Creates a new treatment for how calls to an unassigned number range should be routed. The call can be routed to a user, an application or to an announcement service where a custom message will be played to the caller.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Id of the treatment. | - |
| Description | Write | String | Free format description of this treatment. | - |
| Pattern | Write | String | A regular expression that the called number must match in order for the treatment to take effect. It's best pratice to start the regular expression with the hat character and end it with the dollar character. You can use various regular expression test sites on the Internet to validate the expression. | - |
| Target | Write | String | The identity of the destination the call should be routed to. Depending on the TargetType it should either be the ObjectId of the user or application instance/resource account or the AudioFileId of the uploaded audio file. | - |
| TargetType | Write | String | The type of target used for the treatment. Allowed values are User, ResourceAccount and Announcement. | `User`, `ResourceAccount`, `Announcement` |
| TreatmentPriority | Write | UInt32 | The priority of the treatment. Used to distinguish identical patterns. The lower the priority the higher preference. The priority needs to be unique. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## updateManagementPolicy resource type

### Description

This resource configures the [Teams Update policies](https://learn.microsoft.com/en-us/MicrosoftTeams/public-preview-doc-updates#set-the-update-policy).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Update Management Policy. | - |
| Description | Write | String | The description of the Teams Update Management Policy. | - |
| AllowManagedUpdates | Write | Boolean | Determines if managed updates should be allowed or not. | - |
| AllowPreview | Write | Boolean | Determines if preview builds should be allowed or not. | - |
| AllowPublicPreview | Write | String | Determines the ring of public previews to subscribes to. | `Disabled`, `Enabled`, `Forced`, `FollowOfficePreview` |
| UpdateDayOfWeek | Write | UInt32 | Determines the day of week to perform the updates. Value shoud be between 0 and 6. | - |
| UpdateTime | Write | String | Determines the time of day to perform the updates. Must be a valid HH:MM format string with leading 0. For instance 08:30. | - |
| UpdateTimeOfDay | Write | String | Determines the time of day to perform the updates. Accepts a DateTime as string. Only the time will be considered. | - |
| UseNewTeamsClient | Write | String | Determines whether or not users will use the new Teams client. | `NewTeamsAsDefault`, `UserChoice`, `MicrosoftChoice`, `AdminDisabled`, `NewTeamsOnly` |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## upgradeConfiguration resource type

### Description

This resource configures the [Teams Upgrade settings](https://learn.microsoft.com/en-us/microsoftteams/migration-interop-guidance-for-teams-with-skype).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Specifies the resource is a single instance, the value must be 'Yes' | `Yes` |
| DownloadTeams | Write | Boolean | The DownloadTeams property allows admins to control whether the Skype for Business client should automatically download Teams in the background. This Boolean setting is only honored on Windows clients, and only for certain values of the user's TeamsUpgradePolicy. If NotifySfbUser=true or if Mode=TeamsOnly in TeamsUpgradePolicy, this setting is honored. Otherwise it's ignored. | - |
| SfBMeetingJoinUx | Write | String | The SfBMeetingJoinUx property allows admins to specify which app is used to join Skype for Business meetings, even after the user has been upgraded to Teams. Allowed values are: 'SkypeMeetingsApp' and 'NativeLimitedClient'. 'NativeLimitedClient' means the existing Skype for Business rich client will be used, but since the user is upgraded, only meeting functionality is available. Calling and Messaging are done via Teams. 'SkypeMeetingsApp' means use the web-downloadable app. This setting can be useful for organizations that have upgraded to Teams and no longer want to install Skype for Business on their users' computers. | `SkypeMeetingsApp`, `NativeLimitedClient` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## upgradePolicy resource type

### Description

This resource configures the [Teams Upgrade policies](https://learn.microsoft.com/en-us/microsoftteams/meetings-first#prepare-for-teams-meetings-in-meetings-first).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Upgrade Policy. | - |
| Users | Write | StringArray\[\] | List of users that will be granted the Upgrade Policy to. | - |
| MigrateMeetingsToTeams | Write | Boolean | Specifies whether to move existing Skype for Business meetings organized by the user to Teams. This parameter can only be true if the mode of the specified policy instance is either TeamsOnly or SfBWithTeamsCollabAndMeetings, and if the policy instance is being granted to a specific user. It not possible to trigger meeting migration when granting TeamsUpgradePolicy to the entire tenant. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## user resource type

### Description

This resource is used to add new users to a team

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| TeamName | Key | String | Team NAme | - |
| User | Key | String | UPN of user to add to Team | - |
| Role | Write | String | User role in Team | `Guest`, `Member`, `Owner` |
| Ensure | Write | String | Present ensures the Team user exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All, Team.ReadBasic.All |
| Update | Organization.Read.All, Team.ReadBasic.All |

## userCallingSettings resource type

### Description

This resource configures a [Teams User's Calling Settings](https://learn.microsoft.com/en-us/microsoftteams/user-call-settings).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | The Identity of the user to set call forwarding, simultaneous ringing and call group settings for. Can be specified using the ObjectId or the SIP address. | - |
| GroupNotificationOverride | Write | String | The group notification override that will be set on the specified user. The supported values are Ring, Mute and Banner. | `Ring`, `Mute`, `Banner` |
| CallGroupOrder | Write | String | The order in which to call members of the Call Group. The supported values are Simultaneous and InOrder. | - |
| CallGroupTargets | Write | StringArray\[\] | The members of the Call Group. You need to always specify the full set of members as the parameter value. What you set here will overwrite the current call group membership. | - |
| IsUnansweredEnabled | Write | Boolean | This parameter controls whether forwarding for unasnwered calls is enabled or not. | - |
| UnansweredDelay | Write | String | The time the call will ring the user before it's forwarded to the unanswered target. The supported format is hh:mm:ss and the delay range needs to be between 10 and 60 seconds in 10 seconds increments, i.e. 00:00:10, 00:00:20, 00:00:30, 00:00:40, 00:00:50 and 00:01:00. The default value is 20 seconds. | - |
| UnansweredTarget | Write | String | The unanswered target. Supported type of values are ObjectId, SIP address and phone number. For phone numbers we support the following types of formats: E.164 \(+12065551234 or +1206555000;ext=1234\) or non-E.164 like 1234. | - |
| UnansweredTargetType | Write | String | The unanswered target type. Supported values are Voicemail, SingleTarget, MyDelegates and Group. | `Group`, `MyDelegates`, `SingleTarget`, `Voicemail` |
| IsForwardingEnabled | Write | Boolean | This parameter controls whether forwarding is enabled or not. | - |
| ForwardingType | Write | String | The type of forwarding to set. Supported values are Immediate and Simultaneous | `Immediate`, `Simultaneous` |
| ForwardingTargetType | Write | String | The forwarding target type. Supported values are Voicemail, SingleTarget, MyDelegates and Group. Voicemail is only supported for Immediate forwarding. | `Group`, `MyDelegates`, `SingleTarget`, `Voicemail` |
| ForwardingTarget | Write | String | The forwarding target. Supported types of values are ObjectId's, SIP addresses and phone numbers. For phone numbers we support the following types of formats: E.164 \(+12065551234 or +1206555000;ext=1234\) or non-E.164 like 1234. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## userPolicyAssignment resource type

### Description

This resource is used to assign Teams policy to a specified user.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| User | Key | String | User Principal Name of the user representing the policy assignments. | - |
| CallingLineIdentity | Write | String | Name of the Calling Line Policy. | - |
| ExternalAccessPolicy | Write | String | Name of the External Access Policy. | - |
| OnlineVoicemailPolicy | Write | String | Name of the Online Voicemail Policy. | - |
| OnlineVoiceRoutingPolicy | Write | String | Name of the Online VOice Routing Policy. | - |
| TeamsAppPermissionPolicy | Write | String | Name of the Teams App Permission Policy. | - |
| TeamsAppSetupPolicy | Write | String | Name of the Teams App Setup Policy. | - |
| TeamsAudioConferencingPolicy | Write | String | Name of the Teams Audio Conferencing Policy. | - |
| TeamsCallHoldPolicy | Write | String | Name of the Teams Call Hold Policy. | - |
| TeamsCallingPolicy | Write | String | Name of the Teams Calling Policy. | - |
| TeamsCallParkPolicy | Write | String | Name of the Teams Call Park Policy. | - |
| TeamsChannelsPolicy | Write | String | Name of the Teams Channel Policy. | - |
| TeamsEmergencyCallingPolicy | Write | String | Name of the Teams Emergency Calling Policy. | - |
| TeamsEmergencyCallRoutingPolicy | Write | String | Name of the Teams Emergency Call Routing Policy. | - |
| TeamsEnhancedEncryptionPolicy | Write | String | Name of the Teams Enhanced Encryption Policy. | - |
| TeamsEventsPolicy | Write | String | Name of the Teams Events Policy. | - |
| TeamsMeetingBroadcastPolicy | Write | String | Name of the Teams Meeting Broadcast Policy. | - |
| TeamsMeetingPolicy | Write | String | Name of the Teams Meeting Policy. | - |
| TeamsMessagingPolicy | Write | String | Name of the Teams Messaging Policy. | - |
| TeamsMobilityPolicy | Write | String | Name of the Teams Mobility Policy. | - |
| TeamsUpdateManagementPolicy | Write | String | Name of the Teams Update Management Policy. | - |
| TeamsUpgradePolicy | Write | String | Name of the Teams Upgrade Policy. | - |
| TenantDialPlan | Write | String | Name of the Tenant Dial Plan Policy. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## vdiPolicy resource type

### Description

This resource implements Teams VDI Policies.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identity of the VDI Policy. | - |
| DisableAudioVideoInCallsAndMeetings | Write | Boolean | Disables Audio and Video in Calls and Meeting. | - |
| DisableCallsAndMeetings | Write | Boolean | Disables Calls and Meetings. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## voiceRoute resource type

### Description

This resource configures a [Teams Voice Route](https://learn.microsoft.com/en-us/microsoftteams/direct-routing-voice-routing).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Voice Route. | - |
| Description | Write | String | A description of what this online voice route is for. | - |
| NumberPattern | Write | String | A regular expression that specifies the phone numbers to which this route applies. Numbers matching this pattern will be routed according to the rest of the routing settings. | - |
| OnlinePstnGatewayList | Write | StringArray\[\] | This parameter contains a list of online gateways associated with this online voice route. Each member of this list must be the service Identity of the online PSTN gateway. | - |
| OnlinePstnUsages | Write | StringArray\[\] | A list of online PSTN usages \(such as Local, Long Distance, etc.\) that can be applied to this online voice route. The PSTN usage must be an existing usage \(PSTN usages can be retrieved by calling the Get-CsOnlinePstnUsage cmdlet\). | - |
| Priority | Write | UInt32 | A number could resolve to multiple online voice routes. The priority determines the order in which the routes will be applied if more than one route is possible. | - |
| Ensure | Write | String | Present ensures the route exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## voiceRoutingPolicy resource type

### Description

This resource configures a [Teams Voice Routing Policy](https://learn.microsoft.com/en-us/microsoftteams/manage-voice-routing-policies).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Identity of the Teams Voice Routing Policy. | - |
| OnlinePstnUsages | Write | StringArray\[\] | A list of online PSTN usages \(such as Local or Long Distance\) that can be applied to this online voice routing policy. The online PSTN usage must be an existing usage \(PSTN usages can be retrieved by calling the Get-CsOnlinePstnUsage cmdlet\). | - |
| Description | Write | String | Enables administrators to provide explanatory text to accompany an online voice routing policy. For example, the Description might include information about the users the policy should be assigned to. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## workloadPolicy resource type

### Description

This resources implements a Teams workload policy.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Key | String | Unique identity for the Teams workload policy | - |
| AllowCalling | Write | Boolean | Allows calling. | - |
| AllowCallingPinned | Write | Boolean | Allows pinning a call. | - |
| AllowMeeting | Write | Boolean | Allows meetins. | - |
| AllowMeetingPinned | Write | Boolean | Allows pinning meetings. | - |
| AllowMessaging | Write | Boolean | Allows messaging. | - |
| AllowMessagingPinned | Write | Boolean | Allows pinning a message. | - |
| Description | Write | String | Description of the policy. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Teams Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.Read.All |

## Related content

- [Overview of the Tenant Configuration Management APIs](https://learn.microsoft.com/en-us/graph/unified-tenant-configuration-management-concept-overview)
- [Set up authentication for TCM](https://learn.microsoft.com/en-us/graph/utcm-authentication-setup)
