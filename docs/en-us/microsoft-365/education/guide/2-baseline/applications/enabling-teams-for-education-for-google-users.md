<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/enabling-teams-for-education-for-google-users -->
<!-- Sitemap-Last-Modified: 2026-02-20 -->

# Enabling Teams for Education for Google users without an Exchange mailbox

Tip

Some of the URLs in this article will take you to another document set. If you would like to maintain your place in this document set's table of contents, please right click on URLs to open them in a new window.

Many of our customers operate in mixed environments where both Office 365 and Google solutions are used. Customers in this situation can still benefit from the powerful collaboration and communication tools made available within Microsoft Teams.

The following guide provides details about how administrators can set up Microsoft Teams for Google users without an Exchange mailbox within their environment. Any experience limitations related to this set up are also documented later in this article.

Note

This document assumes that Teams has already been enabled at the tenant level. Click here if you need more information on [Getting Started with Teams.](https://learn.microsoft.com/en-us/education/get-started/enable-microsoft-teams).

## Setting up Microsoft Teams for Google users

### Step 1: Create a mail user account through the Exchange Admin Center.

Users don't need to have the Exchange product license enabled in order to use Teams. Instead, admins should ensure that users are created as mail users within their Exchange environment. The external email address for these users should be set to their Google email address. This setting ensures that email and calendar invites sent via Teams arrive in their Gmail inbox.

You can do this through the [Exchange admin center](https://learn.microsoft.com/en-us/exchange/exchange-admin-center). [Learn more about managing mail users in Exchange](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-mail-users).

### Step 2: Assign Office 365 and product licenses for the user.

Users who use Google services for mail and other capabilities need to be provisioned with an Office 365 license before they can apply Teams capabilities. [Learn more about assigning Office 365 licenses to users.](https://learn.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users).

After a user license is created, ensure that the following product licenses are enabled to ensure core Teams capabilities are functional:

- Microsoft Teams
- SharePoint
- Office 365 Pro Plus

[Learn more about managing user access to Teams](https://learn.microsoft.com/en-us/microsoftteams/user-access), including how to manage add-on licensing for Audio Conferencing and Phone System capabilities.

If users desire to use more services such as Stream, Planner and Forms, then product licenses for these services must also be enabled separately.

### Step 3: Make calendar availability information visible between Exchange and Google users.

If you would like to make calendar availability information visible between Exchange and Google users in your environment, you can use [Google Calendar Interop](https://support.google.com/a/answer/7441020?hl=en) to do so.

If Google Calendar Interop isn't enabled, then users will be unable to view the availability of Google calendar users from within Teams.

### Step 4: Reduce the number of account names users need to remember.

After following the earlier steps, users will have separate Google and Office 365 accounts. Using Google credentials directly in Teams isn't supported. If you would like to sync your users’ Office 365 and Google accounts to reduce the number of account names a user needs to remember, you can do so through [Microsoft Entra Connect](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/whatis-azure-ad-connect) or by [integrating GSuite with Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/google-apps-tutorial).

## Expected capabilities and limitations

After the setup steps above are taken, Teams capabilities and limitations should be as follows:

| Area | Feature | Enabled | Details |
| :--- | :--- | :--- | :--- |
| **User notifications and views**  <br> | Activity Feed  <br> | Yes  <br> | N/A  <br> |
|   <br> | Notifications  <br> | Yes  <br> | Must be mail-enabled user  <br> |
|   <br> | Notification Email  <br> | No  <br> | Notifications emails from both Teams and SharePoint may be blocked by Google due to DMARC policy. In these cases, users will not receive notifications in their Gmail inbox. [Learn more about how Exchange and Teams interact.](https://learn.microsoft.com/en-us/MicrosoftTeams/exchange-teams-interact)  <br> |
|   <br> | Presence  <br> | Yes  <br> |   <br> |
| **Chat and calling**  <br> | Private 1.1 chat, call and video call  <br> | Yes  <br> |   <br> |
|   <br> | Private group chat, call and video call  <br> | Yes  <br> |   <br> |
|   <br> | File sharing in private chats and calls  <br> | Yes  <br> | SharePoint license required  <br> |
|   <br> | Adding tabs in private chats  <br> | Yes  <br> |   <br> |
|   <br> | Adding contact to a private chat and calls  <br> | Yes  <br> |   <br> |
| **Team**  <br> | Create a team  <br> | Yes  <br> |   <br> |
|   <br> | Add a member to team  <br> | Yes  <br> |   <br> |
|   <br> | Add a channel  <br> | Yes  <br> |   <br> |
|   <br> | Conversation in Channel  <br> | Yes  <br> |   <br> |
|   <br> | Teams Notifications  <br> | Yes  <br> |   <br> |
|   <br> | Threaded conversation  <br> | Yes  <br> |   <br> |
|   <br> | Co-authoring documents within a team  <br> | Yes  <br> | SharePoint license required  <br> |
|   <br> | Hiding a team  <br> | Yes  <br> |   <br> |
|   <br> | Leave a team  <br> | Yes  <br> |   <br> |
|   <br> | Join team from a code  <br> | Yes  <br> |   <br> |
| **Meetings**  <br> | View “Meetings” tab  <br> | No  <br> |   <br> |
|   <br> | Create a new meeting  <br> | No  <br> |   <br> |
|   <br> | Receive a meeting invite from an Exchange user  <br> | Yes  <br> | Invite subject and Teams meeting join link may appear in unexpected format.  <br> |
|   <br> | Respond to an invite from an Exchange user \(ex. accept, decline, tentative\)  <br> | Yes  <br> |   <br> |
|   <br> | Response from Google user visible to meeting organizer  <br> | Yes  <br> |   <br> |
|   <br> | See Google user availability within a Teams meeting item  <br> | Yes  <br> | [Google Calendar Interop is required](https://support.google.com/a/answer/7441020?hl=en)  <br> |
|   <br> | See Exchange user availability within Google calendar  <br> | Yes  <br> | [Google Calendar Interop is required](https://support.google.com/a/answer/7441020?hl=en)  <br> |
|   <br> | Start a meeting within a channel using “Meet now”  <br> | Yes  <br> |   <br> |
|   <br> | Scheduling a meeting within a channel  <br> | No  <br> |   <br> |
| **Assignments**  <br> | Receive Assignments within a team  <br> | Yes  <br> |   <br> |
|   <br> | Turn in and manage assignments within a team  <br> | Yes  <br> |   <br> |
|   <br> | See grading information within a team  <br> | Yes  <br> |   <br> |
| **Governance**  <br> | eDiscovery 1.1 chat  <br> | Yes  <br> |   <br> |
|   <br> | eDiscovery teams and channel conversations  <br> | Yes  <br> |   <br> |
|   <br> | Data loss prevention \(DLP\) in 1.1 chat  <br> | Yes  <br> |   <br> |
|   <br> | Data loss prevention \(DLP\) in teams and channel conversations  <br> | Yes  <br> |   <br> |
|   <br> | Data loss prevention \(DLP\) in Files  <br> | Yes  <br> | SharePoint license required  <br> |
