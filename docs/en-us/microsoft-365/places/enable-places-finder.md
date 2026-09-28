<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/enable-places-finder -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# Enable Places finder

Places finder can replace the Room finder experience in Outlook and Teams calendar. We are evaluating deprecation of the Room finder experiences, so we highly recommend that you start with Places finder to reduce future migration costs. The improved functionality helps employees choose the right place to meet and work productively.

Room finder and Places finder use different browsing models. Room finder browses rooms and workspaces by Room Lists, while Places finder browses places by building and floor hierarchy. Before enabling Places finder, make sure you've properly configured your building and floor hierarchy as described in [Configure buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors).

## Overview of Places finder

Places finder and Room finder rely on the same meeting rooms and workspaces data configured in Exchange Online, but Places finder also uses building and floor hierarchical data. Rooms and workspaces will automatically show up in Places finder **as long as you've properly configured your building and floor hierarchy** as described in [Configure buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors).

Starting August 1, 2026, Places finder is enabled by default for newly onboarded tenants.

For newly onboarded tenants, building experiences are also enabled by default through `-EnableBuildings`.

In addition, Places finder will show a much richer experience for conference rooms and workplaces once you've added metadata. Check out [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3) for the full list.

![OWA Card](https://learn.microsoft.com/en-us/microsoft-365/places/media/enabling-places-finder/owa-card.png)

## Enable Places finder

For tenants onboarded before August 1, 2026 that already have Room Lists configured, Places finder remains opt-in. You might want to start by turning it on for a subset of users to validate the experience, before enabling it for everyone. You'll use the [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings) PowerShell cmdlet to enable Places finder. For example, here's how to enable it for users in a specific mail-enabled security group:

For tenants onboarded on or after August 1, 2026, Places finder is opt-out and enabled by default. To turn it off, use the [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings) PowerShell cmdlet to disable Places finder.

```powershell
Set-PlacesSettings -PlacesFinderEnabled 'Default:false'
```

Important

If you plan to use a standard security group, your configuration might not work as expected. To ensure proper functionality, the security group must be set as a mail-enabled security group.

```powershell
Set-PlacesSettings -PlacesFinderEnabled 'Default:false,OID:53212aff-b481-31b1-970b-2ca512e6ae53@ef2a97124-022c7-4bcb7-8a8c-bc2a4256201c:true'
```

And here's how to enable it for everyone in your tenant:

```powershell
Set-PlacesSettings -PlacesFinderEnabled 'Default:true'
```

See [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings) for more details.

You can also use [Get-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placessettings) to verify which users Places finder is enabled for.

For existing tenants that already have Room Lists configured, there are no behavior changes.

Note

To try the experience yourself, make sure you're a member of the mail-enabled security group you're enabling it for, and not just the owner of that security group.

## Understanding the differences between Room finder and Places finder

## Capabilities

|  | Room finder | Places finder |
| --- | --- | --- |
| Browse for rooms | Browse by buildings \(Room Lists\) | Browse by location hierarchy \(Country, State/Region, City, Building, Floor\) |
| Building suggestions | Recent buildings \(Room Lists\) from user's booking history | Buildings from user's booking history and work plan |
| Default building | Last building \(Room List\) selected | Last building set in work plan |
| Spaces | Conference room, workspaces | Conference room, workspaces |
| Filters | Filter by capacity, standard properties, and custom tags.  <br>  <br>Standard properties for meeting rooms: Video, Display, Audio, Microsoft Teams Room, and Wheelchair accessible.  <br>  <br>Standard properties for workspaces: Wheelchair accessible. | Filter by capacity, standard properties, and custom tags.  <br>  <br>Standard properties for meeting rooms: Video, Display, Audio, Microsoft Teams Room, and Wheelchair accessible.  <br>  <br>Standard properties for workspaces: Wheelchair accessible. |
| Room details | Name  <br>Availability  <br>Capacity  <br>City  <br>Features: Standard properties with icons  <br>Features: Custom properties \(no icons\) | Name  <br>Availability  <br>Capacity  <br>Building - Floor - City  <br>Picture  <br>Features - Standard properties with icons  <br>Features - Custom properties with icons  <br>Nearby collaborators for workspaces |
| Hide hidden rooms | Yes | Yes |
| Access policies | Yes | Yes |
| Address Book policies | Yes | Yes |
| Pre-fetching results | Yes | Yes |

### Properties used by Room finder and Places finder

| Property | Property used by Room finder | Property used by Places finder |
| --- | --- | --- |
| Room name, Capacity, MTREnabled, AudioDeviceName, DisplayDeviceName, VideoDeviceName, IsWheelChairAccessible, Tags | Properties of the room in Exchange Online | Properties of the room in Exchange Online |
| City, State, CountryorRegion | Properties of the room in Exchange Online | Properties of the Building |
| GeoCoordinates, PostalCode, Street | Not used | Not used currently |

## Frequently Asked Questions

### Can Room finder and Places finder coexist in my tenant? Will they show the same information?

You can use Room finder and Places finder in parallel. Both show consistent information, but Places finder offers a simpler navigation and provides much richer details to help users pick the right room.

Specifically, Places finder shows a hierarchical view of rooms based on buildings and floors, while Room finder uses RoomList. Furthermore, Places finder sources the City, State, and CountryorRegion properties from the building instead of the room. Other room properties are read from the room object in Exchange Online. For more details, refer to the table included in this article.

#### When I enable Places finder for a certain set of users, will they lose access to Room finder?

Yes. Each user can either see Room finder or Places finder. Room finder remains the default experience and is replaced by Places Finder for users who are enabled.

Important

Make sure that the buildings and floors hierarchy is correctly set up for all rooms and workspaces in the locations where Places finder will be enabled.

#### Who should be enabled for Places finder?

For tenants onboarded before August 1, 2026 that already have Room Lists configured, you might want to start by enabling the new experience for a small set of users before turning it on for everyone.

For tenants onboarded on or after August 1, 2026, Places finder is enabled by default. We recommend adopting Places finder broadly to reduce future migration costs as Room finder deprecation is being evaluated.

#### How do I keep Room finder and Places finder data consistent?

If you plan to use Room finder, we strongly recommend using one RoomList per building and naming each RoomList with the exact building name. If you update the City, State, or CountryorRegion property, make sure to update the information on both the rooms and the building.

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

We strongly recommend creating one RoomList per building only if you plan to use the Room finder experience, to help ensure consistency between Room finder and Places finder.

#### How do I rename a building?

First, rename the building using [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3). Then rename the RoomList to ensure a consistent experience between Room finder and Places finder.

#### One of our rooms shows up in the wrong building/RoomList. How do I fix it?

Follow these steps:

- Step 1: Associate the room to the correct floor and building using [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3). The room will be dissociated from the previous building.
- Step 2: Associate the room to the correct RoomList, and make sure it's not associated to any other RoomList \(see [Create and manage room mailbox](https://learn.microsoft.com/en-us/exchange/recipients/room-mailboxes#create-a-room-list) for details\).
