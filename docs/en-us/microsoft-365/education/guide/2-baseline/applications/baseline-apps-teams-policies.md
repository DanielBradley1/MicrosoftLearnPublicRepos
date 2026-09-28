<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-teams-policies -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 6: Configure Microsoft Teams policies and settings for education organizations

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Microsoft Teams policies and configuration settings are essential for managing users configurations, settings and feature availability, ensuring compliance, and enhancing security, especially in educational environments. This article outlines various policy configurations and best practices recommended by Microsoft. Sometimes, you have multiple ways to achieve a similar goal \(for example, limiting students' ability to chat with other students or non-educational staff\). Because these multiple ways might be mutually exclusive or have a dependency on other parts of your configuration, we'll highlight that to make it easier to make the right decision.

## Teams meetings policies

Teams meeting policies control what features are available to users in meetings, as well as what options the meeting organizer and other meeting roles have available during the meeting lifecycle.

Use these policies to control the meeting experience for students, faculty, and staff. For example, you can disable the ability for students to schedule meetings in channels, but allow faculty and staff to do so. You can also control who can register for meetings, whether anonymous users can join meetings, and more.

| **Identity** | **Global** | **Faculty** | **Staff** | **Default** |
| --- | --- | --- | --- | --- |
| DesignatedPresenterRoleMode | EveryoneUserOverride | **OrganizerOnlyUserOverride** | EveryoneUserOverride | EveryoneUserOverride |
| [AllowChannelMeetingScheduling](https://learn.microsoft.com/en-us/powershell/module/teams/new-csteamsmeetingpolicy?view=teams-ps#-allowchannelmeetingscheduling&preserve-view=true) | **FALSE** | TRUE | TRUE | TRUE |
| AllowMeetNow | **FALSE** | TRUE | TRUE | TRUE |
| AllowPrivateMeetNow | **FALSE** | TRUE | TRUE | TRUE |
| [MeetingChatEnabledType](https://learn.microsoft.com/en-us/powershell/module/teams/set-csteamsmeetingpolicy?view=teams-ps#-meetingchatenabledtype&preserve-view=true) | **EnabledExceptAnonymous** | **EnabledExceptAnonymous** | Enabled | Enabled |
| AllowExternalNonTrustedMeetingChat | **FALSE** | **FALSE** | TRUE | TRUE |
| AllowAnonymousUsersToJoinMeeting | **FALSE** | **FALSE** | TRUE | TRUE |
| AutoRecording | **Disabled** | **Disabled** | Enabled | Enabled |
| AllowPrivateMeetingScheduling | **FALSE** | TRUE | TRUE | TRUE |
| AutoAdmittedUsers | **OrganizerOnly** | **OrganizerOnly** | EveryoneInCompany | EveryoneInCompany |
| AllowOutlookAddIn | **FALSE** | TRUE | TRUE | TRUE |
| AllowParticipantGiveRequestControl | **FALSE** | TRUE | TRUE | TRUE |
| VideoFiltersMode | **BlurAndDefaultBackgrounds** | AllFilters | AllFilters | AllFilters |
| **WhoCanRegister** | **EveryoneInCompany** | **EveryoneInCompany** | Everyone | Everyone |
| ChannelRecordingDownload | **Allow** | Allow | Allow | Allow |
| ExternalMeetingJoin | **Disabled** | EnabledForAnyone | EnabledForAnyone | EnabledForAnyone |

## Teams meeting configuration settings

Teams meeting configurations policies are tenant wide settings used to control what features and capabilities are available to users.

Microsoft recommends preventing students from removing other students, muting them, and otherwise disrupting class if they're added to a meeting as a presenter.

| **Identity** | **Global** | **Default** | **Description** |
| --- | :---: | :---: | --- |
| **LimitPresenterRolePermissions** | **TRUE** | FALSE | Prevents students from removing other students, muting them, and otherwise disrupting class if they're added to a meeting as a presenter. |

## Teams events policy

Microsoft recommends disabling Webinars and townhalls as well as [using PowerShell to set live events policies](https://learn.microsoft.com/en-us/microsoftteams/teams-live-events/set-teams-live-events-policies-using-powershell) to turn off live events scheduling for students and [managing who can schedule webinars in Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/set-up-webinars) to turn off events scheduling for students.

| **Identity** | **Global** | **Faculty** | **Staff** | **Default** | **Description** |
| --- | --- | --- | --- | --- | --- |
| AllowWebinars | Disabled | Enabled | Enabled | Enabled | Prevents students from hosting webinars where they would be able to invite other students, use the meeting chat, etc. |
| AllowTownhalls | Disabled | Enabled | Enabled | Enabled | Prevents students from townhalls where they would be able to invite other students, use the meeting chat, etc. |

## Teams messaging policy

Sometimes students use chat in a way that's not only disruptive for class or other users within the tenant, but also harmful \(such as bullying\) and illegal. To prevent this disruption, districts typically:

- Disable chat for students or a subset of the students \(for example, some grade levels\),
- Limit who students can search for and message in Teams, or
- Implement Supervised Chat, where students can only send messages to their teachers \(depending on the scope and chat role\), staff can send messages to educators and other staff, and educators can send messages to anyone.

Depending on your requirements, you can choose one or more of these methods but remember that some policy settings and configurations might depend on each other.

Disabling chat entirely for students prevents educators from having a 1:1 or group chat with students. However, Microsoft generally leans towards keeping chat available but controlled. The best approach depends on many factors, like regional laws and regulations, school culture, students willingness to listen to what they're told, etc.

We recommend using the following settings to control chat in Teams:

| **Identity** | **Global** | **Faculty** | **Staff** | **Default** |
| --- | --- | --- | --- | --- |
| **Description** | K12 students policy | Educators | Other staff |  |
| **AllowOwnerDeleteMessage** | FALSE | TRUE | TRUE | FALSE |
| **AllowUserEditMessage** | **FALSE** | TRUE | TRUE | TRUE |
| **AllowUserDeleteMessage** | **FALSE** | TRUE | TRUE | TRUE |
| **AllowUserDeleteChat** | **FALSE** | TRUE | TRUE | TRUE |
| **AllowUserChat** | TRUE | TRUE | TRUE | TRUE |
| **AllowRemoveUser** | **FALSE** | TRUE | TRUE | TRUE |
| **GiphyRatingType** | **Strict** | Moderate | Moderate | Moderate |
| **AllowPriorityMessages** | **FALSE** | TRUE | TRUE | TRUE |
| **ChatPermissionRole** | Restricted | **Full** | **Limited** | Restricted |

## Teams messaging configuration

Microsoft recommends disabling the ability for students to create custom emojis to prevent inappropriate content from being uploaded.

| **Identity** | **Global** | **Justification** |
| --- | --- | --- |
| **CustomEmojis** | **FALSE** | Prevents students from uploading inappropriate custom emojis \(that would be available for everyone within the tenant\) |

## Teams channel policy

Teams channel policies are used to control what settings or features are available to users when they're using teams and channels.

Microsoft recommends modifying the global policy setting to implement the following best practices for Teams channels for student safety and compliance reasons.

| **Identity** | **Global** | **Faculty** | **Staff** | **Default** | **Description** | **Justification** |
| --- | --- | --- | --- | --- | --- | --- |
| [AllowPrivateChannelCreation](https://learn.microsoft.com/en-us/powershell/module/teams/set-csteamschannelspolicy?view=teams-ps#-allowprivatechannelcreation&preserve-view=true) | **FALSE** | TRUE | TRUE | TRUE | When On, team owners and members can create private channels that contain a subset of team members. | Students shouldn't be able to create private channels for student safety and compliance reasons. |
| [AllowSharedChannelCreation](https://learn.microsoft.com/en-us/powershell/module/teams/set-csteamschannelspolicy?view=teams-ps#-allowsharedchannelcreation&preserve-view=true) | **FALSE** | TRUE | TRUE | TRUE | When On, team owners can create shared channels for people within and outside the organization. | Students shouldn't be able to create shared channels for student safety and compliance reasons. |
| [AllowChannelSharingToExternalUser](https://learn.microsoft.com/en-us/powershell/module/teams/set-csteamschannelspolicy?view=teams-ps#-allowchannelsharingtoexternaluser&preserve-view=true) | **FALSE** | TRUE | TRUE | TRUE | When On, owners of a shared channel can invite external people in other Microsoft Entra organizations to join the channel, if Microsoft Entra cross-tenant access settings are configured. | Students shouldn't be able to share channels with external users for student safety and compliance reasons. |
| [AllowUserToParticipateInExternalSharedChannel](https://learn.microsoft.com/en-us/powershell/module/teams/set-csteamschannelspolicy?view=teams-ps#-allowusertoparticipateinexternalsharedchannel&preserve-view=true) | **FALSE** | TRUE | TRUE | TRUE | When On, users and teams can be invited to external shared channels, if Microsoft Entra cross-tenant access settings are configured. | Students shouldn't be able to participate in external share channels for student safety and compliance reasons. |

The equivalent of these policies in the Teams admin center can be found in the [Teams settings and policies reference.](https://learn.microsoft.com/en-us/microsoftteams/settings-policies-reference)

## Teams client configuration

To work with or collaborate on files in a secure and seamless manner, it's recommended to disable third-party cloud storage like Box, ShareFile, etc. If there's a need within your organization, you should only enable the service you require and make that app available exclusively to users with such a requirement, as students could potentially use it to circumvent other security measures, and we don't have the same auditing capabilities when using a third-party service.

| **Identity** | **Global** | **Default** | **Justification** |
| --- | --- | --- | --- |
| AllowEmailIntoChannel | TRUE | TRUE |  |
| RestrictedSenderList |  |  |  |
| **AllowDropBox** | **FALSE** | TRUE | Third party file sharing services should be disabled for security and compliance reasons. |
| **AllowBox** | **FALSE** | TRUE | Third party file sharing services should be disabled for security and compliance reasons. |
| **AllowGoogleDrive** | **FALSE** | TRUE | Third party file sharing services should be disabled for security and compliance reasons. |
| **AllowShareFile** | **FALSE** | TRUE | Third party file sharing services should be disabled for security and compliance reasons. |
| **AllowEgnyte** | **FALSE** | TRUE | Third party file sharing services should be disabled for security and compliance reasons. |
| **AllowOrganizationTab** | **FALSE** | TRUE | The organization tab should be disabled to prevent students from browsing the org chart. |

## Teams calling policy

Microsoft recommends using the following settings to control calling in Teams:

| **Identity** | **Global** | **Faculty** | **Staff** | **Default** |
| --- | --- | --- | --- | --- |
| **AllowPrivateCalling** | **FALSE** | TRUE | TRUE | TRUE |
| **AllowWebPSTNCalling** | **FALSE** | TRUE | TRUE | TRUE |
| **AllowSIPDevicesCalling** | **FALSE** | FALSE | FALSE | FALSE |
| **AllowCallGroups** | **FALSE** | TRUE | TRUE | TRUE |

## External access policy

Allowing consumer access allows anyone with a Microsoft account to reach out to users in your tenant and is a potential student safety risk and can pose as a distraction in class. We recommend disabling this feature.

| **Identity** | **Global** | **Faculty** | **Staff** | **Default** |
| --- | --- | --- | --- | --- |
| **EnableTeamsConsumerAccess** | **FALSE** | TRUE | TRUE | TRUE |
| **EnableTeamsConsumerInbound** | **FALSE** | TRUE | TRUE | TRUE |

## Tenant federation configuration

The tenant federation configuration is the external access settings on the tenant level.

| **Identity** | **Global** |
| --- | --- |
| AllowedDomains | AllowAllKnownDomains |
| BlockedDomains | {} |
| AllowFederatedUsers | TRUE |
| AllowPublicUsers | TRUE |
| AllowTeamsConsumer | TRUE |
| AllowTeamsConsumerInbound | TRUE |
| TreatDiscoveredPartnersAsUnverified | FALSE |
| SharedSipAddressSpace | FALSE |
| RestrictTeamsConsumerToExternalUserProfiles | FALSE |
| BlockAllSubdomains | FALSE |
