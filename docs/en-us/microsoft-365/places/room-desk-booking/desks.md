<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/room-desk-booking/desks -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Desks

## Overview of desk booking

Desk booking in Microsoft Places enables users to reserve either a specific desk or a shared desk pool \(workspace\), providing flexibility for different workplace scenarios. Desk pools allow users to reserve a space within a defined area, such as a neighborhood or team zone, without selecting an exact desk. This approach lets users choose where they want to sit when they arrive while still ensuring that a desk will be available within that area based on its configured capacity.

Desks can be configured individually or as part of a pool, and each individual desk supports modes such as reservable, drop-in, assigned, or unavailable to control how it is used. All desks are organized within a structured hierarchy of building, floor, section, and desk, and can be booked through Outlook, Teams, or the Places app.

### Individual desk vs. desk pool

Microsoft Places brings support for **individual desk booking** to Microsoft 365, which allows end users to select a specific desk instead of reserving from a desk pool.

Key concepts:

- Desks can be configured individually or pooled with other nearby desks. Desk pools are referred to as "workspaces" in Exchange Online.
- Individual desks and desk pools can coexist side-by-side in your organization, but each physical desk can be configured in only one way.
- Each individual desk in your organization can be in one of four modes:

  - **Reservable** – Desks can be booked in advance or on the spot.
  - **Drop-in** – Desks are available for on-the-spot use and can't be reserved in advance.
  - **Assigned** – Desks are permanently linked to a specific user and can't be booked by others.
  - **Unavailable** – Desks aren't available for reservation due to maintenance or any other reason.

- Desks follow a strict hierarchy in the Places directory: **Building > Floor > Section > Desk** and desk pools.

Important

- Individual desk booking is a premium feature that requires desks to be backed by a space license. For a limited time, users with a Teams Premium license can also book desks that aren't backed by a space license. For more information, see [What is Places?](https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/what-is-places).
- Users must be enabled for Places Finder to book individual desks.
- The new desk booking experience, which supports both individually configured and pooled desks, is available in New Outlook and Teams calendar on Windows and on the web. It's also available in the Places app in Classic Outlook, Outlook mobile, and Teams mobile apps.

### Prerequisites

- [Configure buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/configuring-places/buildings-floors-sections).
- [Enable Places Finder](https://learn.microsoft.com/en-us/microsoft-365/places/end-user/enable-placesfinder).

## Create an individual desk

You can use either PowerShell or Places management portal to configure desks. The following steps show how to configure desks for individual booking using PowerShell.

### Step 0: Identify the target location \(building, floor, and section\)

Before creating an individual desk, confirm where it will reside within the Places hierarchy. Desks must be created under a **section**, which is itself part of a floor within a building. This hierarchy must already exist before desks can be added.

Use the `Get-PlaceV3` cmdlet to locate the **PlaceId** of the building and floor where the desk will be created:

```powershell
Connect-MicrosoftPlaces

$building = Get-PlaceV3 -Type Building | Where-Object DisplayName -eq "NYC Times Square"

$floor = Get-PlaceV3 -AncestorId $building.PlaceId | Where-Object DisplayName -eq "1"
```

- Use the building and floor identifiers to determine the correct location for your desks.
- In the next step, create \(or identify\) a section under this floor and assign desks to it.

The `Get-PlaceV3` cmdlet retrieves metadata and identifiers for locations in the Places directory, including buildings, floors, sections, and desks.

### Step 1: Create sections and desks

Use the [Get-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placev3) cmdlet to find the **PlaceId** of the floor where the new section will be located. Then create a section and link desks to it.

```powershell
Connect-MicrosoftPlaces

$building = Get-PlaceV3 -Type Building | Where-Object -Property DisplayName -eq 'NYC Times Square'

$floor = Get-PlaceV3 -AncestorId $building.PlaceId | Where-Object -Property DisplayName -eq "1"

$section = New-Place -Type Section -Name "A" -ParentId $floor.PlaceId

$desk1 = New-Place -Type Desk -Name "Desk 1" -ParentId $section.PlaceId

$desk2 = New-Place -Type Desk -Name "Desk 2" -ParentId $section.PlaceId
```

### Step 2: Make the desks bookable

To make a desk bookable, set the mode to **Reservable** or **Drop-In**. A mailbox is created automatically if one isn't provided.

Example: Create a reservable desk without specifying mailbox details.

```powershell
$section = New-Place -Name 'Section1' -Type Section -ParentId 'floorId'

New-Place -Name 'Desk101' -Type Desk -ParentId $section.PlaceId -Mode @{Name='Reservable'}
```

If a mailbox is provided and the mailbox exists, the desk links to it. Otherwise, a new desk mailbox is created automatically.

Example: Create a reservable desk with mailbox details.

```powershell
$section = New-Place -Name 'Section1' -Type Section -ParentId 'someFloorId'

New-Place -Name 'Reservable Desk101' -Type Desk -ParentId $section.PlaceId -Mode @{Name='Reservable'} -Mailbox <mailboxAddress>
```

### Step 3: Add capabilities to desks \(optional\)

You can add metadata to desks, such as accessibility information or available devices.

Refer to [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3) for supported metadata.

```powershell
Connect-MicrosoftPlaces

Set-PlaceV3 $desk1.PlaceId -Tags "height-adjustable-desk"

Set-PlaceV3 $desk2.PlaceId -IsWheelChairAccessible $true
```

### Step 4: Apply booking policies to desks \(optional\)

You can use the Exchange PowerShell `Set-CalendarProcessing` cmdlet to apply booking policies.

```powershell
Connect-ExchangeOnline

Set-CalendarProcessing <desk_mailbox_alias> -BookInPolicy <BookableGroupDL>
```

### Link peripheral devices and set up automatic work location update \(recommended\)

You can use Microsoft Teams to [link peripheral devices](https://learn.microsoft.com/en-us/microsoftteams/rooms/bookable-desks) associated with desks to the corresponding desk objects in the directory.

This allows users to:

- Reserve desks automatically if they forgot to book in advance.
- Generate utilization insights based on monitor and peripheral connections.
- Improve desk utilization reporting.

You may also want to enable automatic work location updates so users' Microsoft 365 work location is updated automatically when they connect to desk peripherals after providing one-time consent.

## Create a desk pool

### Step 0: Identify the target location \(building, floor, and section\)

Before creating a desk pool, confirm where it will reside within the Places hierarchy. Desk pools must be created under a **section**, which is itself part of a floor within a building.

Use the `Get-PlaceV3` cmdlet to locate the target location:

```powershell
Connect-MicrosoftPlaces

$building = Get-PlaceV3 -Type Building | Where-Object DisplayName -eq "NYC Times Square"

$floor = Get-PlaceV3 -AncestorId $building.PlaceId | Where-Object DisplayName -eq "1"
```

- Use the building and floor identifiers to determine the correct location.
- Create or identify a section under the floor and assign the desk pool to it.

The `Get-PlaceV3` cmdlet retrieves metadata and identifiers for buildings, floors, sections, and desks.

### Step 1: Create the desk pool

Desk pools are referred to as **workspaces** in Exchange Online.

Use Exchange Online PowerShell to create a workspace mailbox:

```powershell
Connect-ExchangeOnline

New-Mailbox -Room -Alias <mailbox_alias> -Name <workspace_name> | Set-Mailbox -Type Workspace

Set-CalendarProcessing -Identity <mailbox_alias> -EnforceCapacity $True
```

### Step 2: Make the desk pool available to book

Use [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3) to link the workspace to a section and configure capacity.

```powershell
Connect-MicrosoftPlaces

$building = Get-PlaceV3 -Type Building | Where-Object -Property DisplayName -eq 'NYC Times Square'

$floor = Get-PlaceV3 -AncestorId $building.PlaceId | Where-Object -Property DisplayName -eq '1'

$section = Get-PlaceV3 -AncestorId $floor.PlaceId | Where-Object -Property DisplayName -eq 'A'

Set-PlaceV3 -Identity <mailbox_alias> -Capacity 10 -ParentId $section.PlaceId
```

Add the workspace to a Room List so it also appears in Outlook Room Finder:

```powershell
Add-DistributionGroupMember <roomlistAlias> -Member <workspaceMailbox>
```

See [Add-DistributionGroupMember](https://learn.microsoft.com/en-us/powershell/module/exchange/add-distributiongroupmember) for more information.

### Step 3: Add capabilities to desk pools \(optional\)

You can add metadata to desk pools, including accessibility settings, available devices, and custom tags.

Refer to [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3) for supported metadata.

```powershell
Connect-MicrosoftPlaces

Set-PlaceV3 -Identity <mailbox_alias> -IsWheelChairAccessible $True -Tags "Docking Station"
```

### Step 4: Apply booking policies to desk pools \(optional\)

Use the [Set-CalendarProcessing](https://learn.microsoft.com/en-us/powershell/module/exchange/set-calendarprocessing) Exchange Online cmdlet to apply additional booking policies.

```powershell
Connect-ExchangeOnline

Set-CalendarProcessing <mailbox_alias> -BookInPolicy <BookableGroupDL>
```

### Link peripheral devices and set up automatic work location update \(recommended\)

You can use Microsoft Teams to [link peripheral devices](https://learn.microsoft.com/en-us/microsoftteams/rooms/bookable-desks) associated with desks to individual desks or desk pool objects in the directory.

This allows users to:

- Automatically reserve a drop-in desk.
- Check in to a reservable desk they booked in advance.
- Improve workplace utilization and check-in experiences.
