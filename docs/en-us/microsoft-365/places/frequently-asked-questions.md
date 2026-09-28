<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/frequently-asked-questions -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Frequently Asked Questions

## Licensing

#### Does the license change affect existing Teams Premium customers?

Yes, but only after renewal. Customers who purchased Teams Premium before April 1, 2026 can continue using Places premium capabilities until renewal. After renewal, Places premium features will no longer be included in Teams Premium and will transition to a per-space license.

#### Is a space license required to book rooms or workspaces?

No. Users can continue to book rooms and workspaces \(also known as desk pools\) without any additional license. Furthermore, all users can now enjoy Places finder and Places explorer without any additional license. However, a space license is required to enable autorelease and specific analytics features.

#### Do floors, areas, or buildings need a space license? What about assigned desks?

No. Licenses are only required for individual desks, and for autorelease and analytics on rooms and desks.

#### Which space licenses are supported?

Individual desk booking requires a Microsoft Teams Shared Space License \(formerly named Teams Shared Device license\). See [Teams Shared Device license](https://learn.microsoft.com/en-us/microsoftteams/teams-add-on-licensing/teams-shared-device-license) for details. Autorelease and occupancy data in Places analytics require a Microsoft Teams Shared Space License or a Microsoft Teams Room license. See [Microsoft Teams Room license](https://learn.microsoft.com/en-us/microsoftteams/rooms/rooms-licensing) for details.

#### Can organizations enable Places finder only for specific user groups?

Yes. Admins can selectively enable Places finder using PowerShell. Once you've configured all buildings, we recommend enabling Places finder for all users in your organization.

#### Is Room finder going away?

No. Room finder remains available and continues to be the default experience in the Outlook and Teams calendar. However, Microsoft recommends configuring buildings and maps and enabling Places finder for everyone in your organization.

#### Do I need a space license for check-in?

No. Checking in to a building, a room, or a desk doesn't require any additional license. However, checking in to a room or desk prevents it from being autoreleased if the room or desk has a space license. Otherwise, the autorelease policy may be ignored.

## Configure buildings and floors

#### Can I export all rooms, regardless of whether they're part of a room list?

Yes. Use `Get-PlaceV3` to export all rooms.

**PowerShell**

```powershell
Get-PlaceV3 -Type Room | Export-Csv -NoTypeInformation "C:\temp\rooms.csv"
```

#### Do I have to set up all of my buildings and floors at the same time?

No. You can run `Initialize-Places` as many times as you want and focus on one building at a time. To do that, trim the rows in the CSV file generated in step 1 to only keep the buildings and floors you're working on, and upload that CSV in step 3. Changes for a set of buildings, floors, and sections may not reflect if you generate a new CSV file immediately after uploading a CSV file.

Make sure buildings, floors, and sections are spelled exactly the same way throughout the list. Any difference results in a new building, floor, or section being created.

#### My security department wants to know what PowerShell commands are executed during import

You can use **Initialize-Places Option 3 \(Export a PowerShell script\)** to preview the commands that are executed. In this option, you must provide a CSV file with the same four columns shown in the example. Instead of setting up the buildings, floors, sections, workspaces, and rooms, Initialize-Places Option 3 exports a PowerShell script containing the commands that would be executed during import. The PowerShell script is exported to the same folder as your import file.

Note

The import file is needed only to generate the PowerShell script. Nothing is imported on your behalf. You can use the exported PowerShell script to run the commands yourself rather than using Initialize-Places Option 2.

#### Can I run import with only building names?

No. Microsoft Places depends on a fully established hierarchy with Buildings > Floors > Sections > Rooms/workspaces. If you leave the section empty, the room is parented to the floor. However, workspaces aren't processed as workspaces because workspaces must always be parented to a section.

#### How do I update room data, such as capacity or display name?

You can do this using `Set-PlaceV3`.

## Troubleshooting

#### I don't see the options described here when I run Initialize-Places

Make sure you're using the latest version of the Microsoft Places PowerShell module. PowerShell might attempt to cache the installed module, so it's a good idea to use the `-Force` parameter.

**PowerShell**

```powershell
Install-Module -Name MicrosoftPlaces -AllowPrerelease -Force
```

#### I created buildings, but they are not visible

Enable building visibility in PowerShell:

**PowerShell**

```powershell
Set-PlacesSettings -EnableBuildings 'Default:true'
```

For more information, see `Set-PlacesSettings`.

#### I receive an import error

Make sure that the CSV file is closed before importing it.

#### I don't see all rooms/workspaces after importing

It can take up to 24 hours for room and workspace associations to appear in Microsoft Places.

## Configure automatic update of work location \(Wi-Fi building check-in\)

#### What is Automatic Update of work location, and what does it do?

This is a Microsoft Teams feature that helps employees keep their work location up to date so coworkers can coordinate in-person work. It's not a monitoring or surveillance tool and does not track movement, attendance, or store historical location data.

#### Can Automatic Update be used to monitor employees?

No. Users can manually set or clear their work location at any time, whether they're inside or outside their corporate network. For example, they can mark themselves as in-office or even in a specific building while working from home, or mark themselves as remote while working on-site. This is by design because Automatic Update is meant to improve in-person collaboration and coordination rather than monitor employees.

#### Is Automatic Update turned on automatically for employees?

No. Automatic Update is off by default in every tenant and must be enabled and configured by admins. For Wi‑Fi-based Automatic Update, admins can choose between **Inform mode** \(users can opt out\) and **Ask mode** \(users can opt in\). In both cases, users are always informed and can choose whether to participate. Users must also grant operating-system-level location permission to Microsoft Teams for Automatic Update to work.

#### Can employees control or override their work location?

Yes. Employees remain in control by design. Users can manually set, override, or clear their work location at any time, whether they're inside or outside corpnet.

#### What information is visible to coworkers?

Users choose whether to share their work location with coworkers in Teams and Outlook calendar settings. When sharing is enabled, coworkers can see work-location signals \(in the office, in a specific building, or remote\), whether the location was set manually or automatically.

#### How does Wi‑Fi Automatic Update work?

Automatic Update uses network change events, such as connecting to a Wi‑Fi network, switching between Wi‑Fi networks, or waking a device from sleep. Automatic Update doesn't continuously poll location.

If a user switches to Ethernet after connecting to Wi‑Fi, Teams may clear or retain location depending on the scenario. Work location isn't automatically updated on desktop computers connected via Ethernet. Users must grant OS-level location permission to Teams for the feature to function.

#### Does the work location signal expire?

Users can manually clear their work location at any time. Work location is automatically cleared at the end of working hours, which can be configured in Teams and Outlook calendar settings.

#### Does Automatic Update work outside users' working hours?

No. If users connect to a peripheral or wireless network outside of working hours, their work location won't be automatically updated. At the end of a user's working hours, their work location is cleared and workplace check-in via Wi‑Fi won't be triggered for the remainder of the day.

Users can go to **Set your work hours and location in Outlook** for more information about setting work hours.

#### Does Automatic Update work outside corporate networks?

No. Automatic Update only works when users connect to a peripheral or wireless network configured in their tenant. Connecting to the networks or peripherals of another organization is ignored.

#### Does workplace check-in support mobile devices?

No. Workplace check-in is currently available only in the Teams desktop app on Windows and macOS.

## Enable Places Finder

#### Can Room finder and Places finder coexist in my tenant? Will they show the same information?

You can use Room finder and Places finder in parallel. Both show consistent information, but Places finder offers a simpler navigation and provides much richer details to help users pick the right room.

Specifically, Places finder shows a hierarchical view of rooms based on buildings and floors, while Room finder uses RoomList. Furthermore, Places finder sources the City, State, and CountryorRegion properties from the building instead of the room. Other room properties are read from the room object in Exchange Online. For more details, refer to the table included in this article.

#### When I enable Places finder for a certain set of users, will they lose access to Room finder?

Yes. Each user can either see Room finder or Places finder. Room finder remains the default experience and is replaced by Places Finder for users who are enabled.

Important

Make sure that the buildings and floors hierarchy is correctly set up for all rooms and workspaces in the locations where Places finder will be enabled.

#### Who should be enabled for Places finder?

You might want to start by enabling the new experience for a small set of users in your organization before turning it on for everyone.

#### How do I keep Room finder and Places finder data consistent?

We strongly recommend using one RoomList per building and naming each RoomList with the exact building name. If you update the City, State, or CountryorRegion property make sure to update the information on the rooms and on the building.

#### I’ve enabled Places finder for everyone in my tenant, but some users are still seeing the Room finder experience

Places finder is available:

- in Classic Outlook and New Outlook, on Windows
- in Outlook web app \(OWA\)
- in Teams, on Windows, macOS and on the web

#### Some meeting rooms are missing in Places finder

Make sure you've curated your building and floor hierarchy as described in [Configured buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors).

#### Can I hide a room or workspace from showing in Places finder?

Yes. A room or workspace can be hidden in both Places finder and Room finder. Learn more about how you can hide mailboxes by using the [Set-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/set-mailbox) cmdlet.

#### Our facilities team has configured a new meeting room. How do I make it visible in both Room finder and Places finder?

Follow these steps:

- Step 1: Create the room in Exchange Online \(see [New-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/new-mailbox)\).
- Step 2: Add the room to the RoomList that represents the correct building. For more information on room mailboxes, see [Create and manage room mailbox](https://learn.microsoft.com/en-us/exchange/recipients/room-mailboxes#create-a-room-list). This step will make the room visible in Room finder.
- Step 3: Associate the room to the right floor and building \(see [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3)\). This step will make the room visible in Places finder.

Note

If you rename a room, the new name will automatically show up in both Room finder and Places finder.

#### Our facilities team has converted a meeting room to desk space. How do I delete the room?

Use [Remove-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/remove-mailbox) to permanently delete a room.

#### We leased a new building. What should I do?

Follow these steps:

- Step 1: Create the rooms in Exchange Online \(see [New-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchange/new-mailbox)\).
- Step 2: create a new RoomList that represents the building, then add the rooms to this RoomList \(see [Create and manage room mailbox](https://learn.microsoft.com/en-us/exchange/recipients/room-mailboxes#create-a-room-list) for details\). This step will make the rooms visible in Room finder.
- Step 3: associate the rooms to their respective floors and to the building \(see [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3)\). This step will make the rooms visible in Places finder.

Note

We strongly recommend creating one RoomList per building to ensure a consistent experience between Room finder and Places finder.

#### How do I rename a building?

First, rename the building using [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3). Then rename the RoomList to ensure a consistent experience between Room finder and Places finder.

#### One of our rooms shows up in the wrong building/RoomList. How do I fix it?

Follow these steps:

- Step 1: Associate the room to the correct floor and building using [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3). The room will be dissociated from the previous building.
- Step 2: Associate the room to the correct RoomList, and make sure it's not associated to any other RoomList \(see [Create and manage room mailbox](https://learn.microsoft.com/en-us/exchange/recipients/room-mailboxes#create-a-room-list) for details\).

## Enable check in and autorelease for rooms, desks, and desk pools \(optional\)

#### Does this feature support on-premises mailboxes?

No. This feature is only available for rooms, desks, and desk pools backed by a mailbox in Exchange Online. To learn more about how to manage mailboxes, see Manage resource mailboxes in Exchange Online.

#### My users aren't able to check in via Teams chat

The check-in experience in Teams meeting chat is hosted in Outlook on the web \(OWA\). Make sure that Outlook on the web is enabled for users who need to check in via Teams chat. See Outlook on the web in Exchange Online for details. 【1-05fe65】

#### How does this feature work with Microsoft Teams' check-in and room release?

Microsoft Places enhances check-in and room release features for Teams Panels to reflect room usage and prevent automatic release. Places analytics show insights on booked rooms that are released due to no check-in.

#### When are rooms released?

If no attendee checks in to the room within the configured duration of meeting start time, the system cancels the room reservation so that others can reserve the room.

#### Is the meeting organizer required to check in?

No. Anyone physically present in the meeting room, or who has access to the Teams meeting chat, can check in. Only one person needs to check in.

#### Is this feature supported in any of the special cloud environments?

Autorelease is currently supported in the Government Community Cloud \(GCC\).

#### Does this feature work for both desks and desk pools?

Yes. If the user reserves an individual desk or a desk in a desk pool and doesn't check in within the allotted time, the system cancels their reservation so others can reserve that desk.

#### When does a desk get released?

When a user reserves a desk or a desk in a desk pool, they have a set time to check in. This time is configurable by the admin. If the user doesn't check in, they receive an email notification that the desk is released and available for others to book.

#### Which desk modes support this feature?

This feature is supported for reservable desks. Drop-in, assigned, and unavailable desks don't support this feature.

#### Are there times when the user is automatically checked into a desk?

Yes. A desk is checked in automatically as part of automatic reservation upon plug-in to a linked peripheral.
