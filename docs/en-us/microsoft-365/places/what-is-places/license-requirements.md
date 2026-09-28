<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/license-requirements -->
<!-- Sitemap-Last-Modified: 2026-09-21 -->

# License requirements

## Supported user licenses

Users with one the following plans can access Microsoft Places:

- Microsoft 365 Business Basic, Standard, Premium
- Microsoft 365 or Office 365 \(E1, E3, E5\)
- Microsoft 365 or Office 365 for Education \(A1, A3, A5\)
- Microsoft 365 for frontline workers \(F1, F3\)
- Microsoft Teams Enterprise
- Microsoft Teams Essentials
- Microsoft Teams standalone

## Core features

These features are available to all users with one of these plans. Some features need to be explicitly enabled, as described in the Configure Places section of this guide.

- Work plans and workplace presence
- In-person events and hybrid RSVP
- Automatic detection of work location
- Book room and workspaces \(also known as desk pools\)
- Desk assignment
- Places Management portal \(requires specific permissions described [here](https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/set-up-your-account-places-admin)
- Places explorer
- Places finder
- Places analytics \(with some limitations. Also requires specific enablement described [here](https://learn.microsoft.com/en-us/microsoft-365/places/enable-places-analytics/enable-places-analytics)

## Premium features

The following features used to require a Teams Premium license. As of April 1st, 2026, these features have shifted to a per-space licensing model:

- **Individual desk booking** shifts from a per-user to a per-space licensing model. To ensure a smooth transition, customers with active Teams Premium subscriptions continue to enjoy premium features until renewal.
- **Auto-release** requires rooms and desks to have a space license
- **Occupancy reports** in Places analytics requires rooms and desks to have a space license. Other analytics features don't require any other license.

## Supported space licenses

- Microsoft Teams Room \("MTR"\), which can be used on meeting rooms
- Microsoft Teams Shared Space \("MTSS"\). This was previously called Microsoft Teams Shared Device and is renamed to Shared Space for clarity. This license can be used with BYOD rooms, common area phones, and now with individual desks
- Microsoft Teams Shared Space – Single Space \("MTSS-SS"\). You can acquire 3 free MTSS-SS licenses for each purchased MTSS license. MTSS-SS licenses can be used with BYOD rooms or individual desks, but not with common area phones.

| Space type | Places features | License required |
| --- | --- | --- |
| Room | Autorelease, Occupancy reports | MTR, MTSS or MTSS-SS |
| Individual desk | Booking, Autorelease, Occupancy reports | MTSS or MTSS-SS |

Note

If you use an MTSS license for a Teams common area phone, you can’t use the 3 free MTSS-SS licenses for rooms or desks. If you use an MTSS license for a BYOD room or an individual desk, you can use the 3 free MTSS-SS licenses for 3 more rooms or desks. Refer to the FAQ section for more details.

Note

For detailed instructions on purchasing and assigning **Microsoft Teams Shared Space licenses for desks**, see [Buy and set up Teams Shared Space licenses for desks](https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/buy-set-up-teams-shared-space-licenses-desks).

## AI features

AI-driven features such as Copilot room booking require a Microsoft Copilot license.

## Summary: Places feature and license requirements

| Feature | Description | Where | Old license requirement \(before April 1st, 2026\) | New license requirement |
| --- | --- | --- | --- | --- |
| Work plans | Set your work location schedule in advance so coworkers know when you plan to be in the office or work remotely. | Calendar in New Outlook<sup>1</sup>; Calendar in Teams; Places app<sup>2</sup> | Core | Core |
| Workplace presence | Update your work location to indicate you’re in the office and see who else is in the office that day. | Calendar in new Outlook; Calendar in Teams; Places app | Core | Core |
| Automatic update of work location | Automatically check in when connecting to corporate WiFi or a supported peripheral. | Teams desktop app | Core | Core |
| In-person events | Request invitees to attend a meeting or event in person and see each person’s attendance mode and response in the event tracking pane. | Calendar in new Outlook; Calendar in Teams | Core | Core |
| Hybrid RSVP | Allow participants to indicate whether they plan to attend an in-person event in person or virtually. | Calendar in new Outlook; Calendar in Teams | Core | Core |
| Places card | View who’s coming into the office and quickly adjust your work plan directly from your calendar. | Calendar in new Outlook; Calendar in Teams; Places app | Core | Core |
| Places explorer | View people, spaces, and experiences across a workplace location in a single experience. | Places app | Teams Premium | Core |
| Places finder | Book rooms and desks with rich metadata such as photos, floor plans, A/V capabilities, accessibility, and more. | Calendar in new Outlook; Calendar in Teams | Teams Premium | Core |
| Places management | Manage Places properties, modes, and policies through a management experience. | Places management portal; PowerShell; Microsoft Graph | Core | Core |
| Individual desk booking | Allow users to select and book individual desks in advance for their day in the office. | Calendar in new Outlook; Calendar in Teams | Teams Premium | Space license |
| Autorelease | Automatically release reserved rooms and desks when they're unoccupied. | Rooms, desks, and desk pools | Teams Premium | Space license |
| Places analytics | Visualize intended and actual occupancy data for buildings, rooms, and workspaces. | Places app | Teams Premium | Occupancy reports require a space license |
| Quick book | Get room recommendations and quickly add rooms to meetings that don’t yet have one. | Calendar in new Outlook; Calendar in Teams; Places app | Teams Premium | Microsoft Copilot license |
| Copilot room booking | Use Copilot to recommend rooms based on multiple factors and rebook rooms when meetings change or conflicts arise. | Calendar in new Outlook; Calendar in Teams | Microsoft Copilot license | Microsoft Copilot license |

<sup>1</sup> [New Outlook](https://support.microsoft.com/office/getting-started-with-the-new-outlook-for-windows-656bb8d9-5a60-49b2-a98b-ba7822bc7627) is currently available on Windows and on the web.

<sup>2</sup> The Microsoft Places app is available [on the web](https://aka.ms/places), and on desktop and mobile as a connected app inside Outlook, Teams, and the Microsoft 365 app.

Note

In Exchange hybrid environments, Places features are only available for users with a mailbox managed in Exchange Online. Users with an on-premises mailbox can't access the Places app, Places finder, or other Places features such as work plans. These users can continue to use Room Finder in Outlook.

Work location settings aren't supported for users whose mailbox is hosted on Exchange on-premise. While the option to update work location is visible in Microsoft Teams, any changes made are only visible to the individual user and aren't shared with colleagues or reflected across the organization. For accurate presence and location sharing, we recommend migrating your mailbox to Exchange Online.

## More resources

You can find more resources here:

- [Microsoft Places product page](https://www.microsoft.com/microsoft-places)
- [Microsoft Teams Premium - Overview for admins](https://learn.microsoft.com/en-us/microsoftteams/enhanced-teams-experience)

Tip

As a companion to this article, we recommend using the [**Microsoft Places Deployment Playbook**](https://aka.ms/PlacesDeployment).
