<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/new-place -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# New-Place

Use the **New-Place** cmdlet to create buildings, floors, sections, rooms, workspaces, or desks within your Places directory.

Note

- Update to Places PowerShell version 2.0.0 and above to access the latest features and improvements.

## Syntax

### Building

```powershell
New-Place
 [-DisplayName]
 [-Type]
 [-Label]
 [-PostalCode]
 [-CountryOrRegion]
 [-State]
 [-City]
 [-Street]
 [-GeoCoordinates]
 [-ResourceLinks]
 [-Tags]
```

#### Floor

```powershell
New-Place
 [-DisplayName]
 [-Type]
 [-Label]
 [-ParentId]
 [-SortOrder]
 [-Tags]
```

#### Section

A section is a logical grouping of spaces within a floor, such as a neighborhood.

- Desks and workspaces must belong to a section.
- Rooms can either be assigned to a section or directly associated with a floor.

```powershell
New-Place
 [-DisplayName]
 [-Type]
 [-Label]
 [-ParentId]
```

#### Room

Creating a room automatically provisions an associated mailbox. If you provide a EmailAddress in the Mailbox parameter, a new mailbox will be created with that name and linked to the room.

Note

- To create a room mailbox automatically, you need one of these roles: **Places Administrator**, **Exchange Administrator**, or **Global Administrator**.
- Provisioning may take up to 24 hours. Allow a brief delay to ensure all resources are fully set up and operational.
- To create rooms, although not recommended, you may continue to use the New-Mailbox cmdlet as documented [here](https://learn.microsoft.com/en-us/powershell/module/exchange/new-mailbox). Places syncs with mailbox metadata, and the associated room within 24 hours.
- Do **not** change the mailbox resource type after linking it to a room. Updates to the room will fail due to resource type mismatch.

```powershell
New-Place
 [-DisplayName]
 [-Type]
 [-Label]
 [-ParentId]
 [-Capacity]
```

#### Workspace

Creating a workspace \(desk pool\) automatically provisions an associated mailbox. If you provide a EmailAddress in the Mailbox parameter, a new mailbox will be created with that name and linked to the workspace.

Note

- To create a workspace mailbox automatically, you need one of these roles: **Places Administrator**, **Exchange Administrator**, or **Global Administrator**.
- Provisioning may take up to 24 hours. Allow a brief delay to ensure all resources are fully set up and operational.
- To create workspaces, although not recommended, you may continue to use the New-Mailbox cmdlet as documented [here](https://learn.microsoft.com/en-us/powershell/module/exchange/new-mailbox).
- Set type to Workspace immediately after creation. Places syncs with mailbox metadata, and the associated workspace within 24 hours. -Do **not** change the mailbox resource type after linking it to a workspace/desk pool. Updates to the room will fail due to resource type mismatch.

```powershell
New-Place
 [-DisplayName]
 [-Type]
 [-Label]
 [-ParentId]
 [-Capacity]
```

#### Desk

A desk represents an individual desk unit. Each desk has a Mode property that defines how it can be used:

- **Reservable** – Can be reserved in advance.
- **Drop-In** – Available for on-the-spot use only.
- **Assigned** – Assigned to a specific user.
- **Unavailable** – Not available for reservation.

Desk Mode and Mailbox works as follows:

- **Default behavior:** If the Mode is not defined, the desk defaults to Unavailable. No mailbox is created.
- **Reservable or DropIn mode:** A desk mailbox is required. One is automatically created when the desk is provisioned or you can link to an existing one.

  - If you provide an existing EmailAddress in the Mailbox parameter, the desk links to that mailbox.
  - If you provide an EmailAddress that doesn’t exist, a new mailbox is created with that name and linked to the desk.
  - If no EmailAddress is provided, a mailbox is auto-created with a system generated name and linked to the desk.

- **Assigned or Unavailable mode:** Linking a mailbox is optional, and no mailbox is created. However, you can manually associate these desks with custom mailboxes if needed.
- **Changing mode later:** If the desk starts in Unavailable mode and no mailbox is linked, switching the desk to Reservable using the Set-PlaceV3 cmdlet will automatically create and link a mailbox. However, linking a mailbox to a desk does not update the desk's mode automatically.

Unlike rooms or workspaces, desks do not sync metadata such as Capacity or DisplayName with mailbox properties. The mailbox is used primarily by the reservation engine, while metadata is read from the Places Directory.

Note

- To create a desk mailbox automatically, you need one of these roles: **Places Administrator**, **Exchange Administrator**, or **Global Administrator**.
- To link to an existing mailbox, its resource type must be **Desk**.
- If you creatw a new mailbox, set the resource type to Desk immediately after creation.
- Do not set mailbox type as room or workspace.
- Do *not* change the mailbox resource type after linking it to a desk. Updates to the desk will fail due to resource type mismatch.

```powershell
New-Place
 [-DisplayName]
 [-Type]
 [-Label]
 [-ParentId]
 [-GeoCoordinates]
 [-Mailbox]
 [-Mode]
```

## Description

Microsoft Places requires a complete hierarchy for buildings, floors, sections, rooms, workspaces, and desks.

- A **floor** must belong to a building.
- A **section** must belong to a floor.
- A **room** must belong to a floor or section.
- A **workspace** or **desk** must belong to a section.

Use the ParentId property to link entities.

To run this cmdlet, you need one of these roles: **Places Administrator**, **Exchange Administrator**, or a custom roles with **TenantPlacesManagement** permissions.

Caution

You might find additional parameters in the PowerShell cmdlet, but those parameters aren't currently supported. Please do not use any parameter that isn't documented on this page.

## Examples

### Example 1

This example creates a new building and a floor within that building.

```powershell
New-Place -Type Building -Name 'Building 3'
```

After Building 3 is created successfully, read its PlaceId to use when setting the ParentId on the floors.

```powershell
New-Place -Type Floor -Name 'Lobby' -ParentId f12172b6-195d-4e6e-8f4f-eb72e41de99a
New-Place -Type Floor -Name '1' -ParentId f12172b6-195d-4e6e-8f4f-eb72e41de99a
```

### Example 2

This example creates a new building with address information.

```powershell
New-Place -Name 'Building 3' -Type Building -Description 'Building 3 in North of Redmond Campus' -CountryOrRegion US -State WA -City Redmond -Street 'Street 3' -PostalCode 98052
```

### Example 3

This example creates a new building with resource links.

```powershell
New-Place -Name 'Building 3' -Type Building -ResourceLinks @{name="TestLink";value="https://contoso.com/";type="Url"}'
```

### Example 4

This example creates a new room parented to a section and with a capacity 10, without specifying mailbox details. A room mailbox is automatically created and linked.

```powershell
New-Place -Name 'Room a' -Type Room -ParentId -ParentId $SectionId -Capacity 10
```

### Example 5

This example creates a new room parented to a section, and provide a mailbox details

```powershell
New-Place -Name 'Room a' -Type Room -ParentId -ParentId $SectionId -Mailbox <mailboxAddress>
```

### Example 6

This example creates a new workspace\(desk pool\) parented to a section, and provide a mailbox details

```powershell
New-Place -Name 'Deskpool A' -Type Workspace -ParentId -ParentId $SectionId -Mailbox <mailboxAddress>
```

### Example 7

This example creates a reservable desk parented a section without specifying mailbox details. A desk mailbox is automatically created and linked, and the MailboxOID property is populated. The desk appears in Places Finder and is available for booking by anyone.

```powershell
$section = New-Place -Name 'Section1' -Type Section -ParentId 'someFloorId'
New-Place -Name 'Reservable Desk101' -Type Desk -ParentId $section.PlaceId -Mode @{Name='Reservable'}
```

### Example 8

This example creates a reservable desk parented to a section, and provide a mailbox. If the mailbox exist, the desk will link to it, else a new desk mailbox is created automatically with the provided name.

```powershell
$section = New-Place -Name 'Section1' -Type Section -ParentId 'someFloorId'
New-Place -Name 'Reservable Desk101' -Type Desk -ParentId $section.PlaceId -Mode @{Name='Reservable'} -Mailbox <mailboxAddress>
```

### Example 9

This example creates an assigned mode desk parented to a section and assigns it to a person. Only the assigned person can use this desk. Others can no longer reserve it.

```powershell
$section = New-Place -Name 'Section1' -Type Section -ParentId 'someFloorId'
$modemetadata = New-Object 'System.Collections.Generic.Dictionary[String,object]'
$modemetadata.Add("AssignedPersonEmailAddress","someUserEmailAddress")
New-Place -Name 'Bookable Desk101' -Type Desk -ParentId $section.PlaceId -Mode @{Name='Assigned';Metadata=$modemetadata}
```

## Parameters

### -City

The City parameter specifies the building's city. If the value contains spaces, enclose the value in quotation marks \("\). The maximum length is 200 characters.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -CountryOrRegion

The CountryOrRegion parameter specifies the building's country or region. A valid value is a valid ISO 3166-1 two-letter country code \(for example, AU for Australia\) or the corresponding friendly name for the country \(which might be different from the official ISO 3166 Maintenance Agency short name\).

A reference for two-letter country codes is available at [Country Codes List](https://www.nationsonline.org/oneworld/country_code_list.htm).

Address information is used by the Places Explore page to show nearby buildings.

| Attribute | Description |
| --- | --- |
| Type: | CountryInfo |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Label

The Label parameter specifies a descriptive label for the place. If the value contains spaces, enclose the value in quotation marks \("\). The maximum length is 200 characters.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | True |
| Accept wildcard characters: | False |

### -GeoCoordinates

The GeoCoordinates parameter specifies the building's location in latitude, longitude, and \(optionally\) altitude coordinates. A valid value for this parameter uses one of the following formats:

- Latitude and longitude: For example, "47.644125;-122.122411"
- Latitude, longitude, and altitude: For example, "47.644125;-122.122411;161.432"

Note

If period separators don't work for you, use commas instead.

| Attribute | Description |
| --- | --- |
| Type: | GeoCoordinates |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -DisplayName

The DisplayName parameter specifies the display name of the place. The maximum length is 200 characters.

A building's display name is visible:

- In Outlook, when users are setting up their work hours and location, they're able to select a building.
- In Places Explore page that shows who else is in the same building, nearby buildings, and more.
- In Places Finder, as a filter when searching for a conference room or workspace.

A floor's display name is visible in Places Finder as a filter when searching for a conference room or workspace.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -ParentId

The ParentId parameter specifies the ID of a Place in the parent location hierarchy in Microsoft Places.

- A room should have a parent floor or section.
- A workspace or desk should have a parent section.
- A section should have a parent floor.
- A floor should have a parent building.

Note

If you need backward compatibility with Outlook Roomfinder, make sure to also update the "Floor"/"FloorLabel" properties, in parallel with parenting the room to the floor entity. Places Finder uses the new hierarchy while Outlook Roomfinder continues to use the legacy "Floor" and "FloorLabel" objects. You also need to make sure the room is associated with a Roomlist, as documented here [Configure rooms and workspaces for Room Finder in Outlook](https://learn.microsoft.com/en-us/outlook/troubleshoot/calendaring/configure-room-finder-rooms-workspaces).

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -PostalCode

The PostalCode parameter specifies the building's postal code. The maximum length is 200 characters.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -ResourceLinks

The ResourceLinks parameter specifies external links or [Teams app](https://learn.microsoft.com/en-us/microsoftteams/apps-in-teams) IDs that should be associated with this building, such as a dining menu, a link to services or a Teams app for visitor management. For more information on how to set up services in Places, see [Services in Places](https://learn.microsoft.com/en-us/deployoffice/places/services-in-places).

The value must be provided as an array of links, as shown in [Example 4](https://learn.microsoft.com/en-us/deployoffice/places/powershell/set-placev3#example-4). Each link should contain the following properties: Name, Value, and Type. For example, a link would be written as @{name="TestLink"; value="https://contoso.com/"; type="Url"}.

- **Name**

  - This string is used to show how your link or app name is displayed in the Places app.
  - The maximum length is 200 characters.

- **Value**

  - This value should be either a url link or a Teams app ID. Teams app IDs can be found in the App Details page of the app in the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center.
  - The maximum length is 1000 characters.

- **Type** must be one of the supported types:

  - Url - indicates that this is a url link.
  - MetaOsApp - indicates that this link is a Teams app.

Note

The entire set is replaced. To add or remove a value, be sure to include previous values that should be persisted.

| Attribute | Description |
| --- | --- |
| Type: | ResourceLink\[\] |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -SortOrder

The SortOrder parameter specifies the sort order of the floor. For example, a floor might be named "Lobby" with a sort order of 0 to show this floor first in ordered lists.

| Attribute | Description |
| --- | --- |
| Type: | System.Int32 |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -State

The State parameter specifies the building's state or province. The maximum length is 200 characters.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Street

The Street parameter specifies the building's physical address. The maximum length is 200 characters.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Tags

The Tags parameter specifies other features of the room \(for example, details like the type of view or furniture type\). There's no maximum length currently.

You can specify multiple labels separated by commas. If the labels contains spaces, enclose the values in quotation marks: `"Label 1","Label 2",..."Label N"`.

Note

The entire set is replaced on update. To add or remove a value, be sure to include previous values that should be persisted.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Mode

The Mode parameter defines how a place is intended to be used or booked. Currently, mode is only available for desks and desk pools \(workspaces\).

Currently, there are four modes in total.

- **Reservable**- Reservable desks are the desks that are configured to be booked in advance or on-the-spot.
- **Drop-in**- The desk is available for on-the-spot use and can't be reserved in advance. You can use the capability from Microsoft Teams to link the peripheral devices present on these desks to the individual desk object in the directory.
- **Assigned** - An assigned desk is permanently linked to a specific user and can't be booked by others. Every assigned desk must always have a designated user.
- **Unavailable**- The desk isn't available for reservation due to maintenance or for any other reason.

The mode value should contain the following properties: Name and Metadata, as shown in [Example 5](https://learn.microsoft.com/en-us/deployoffice/places/powershell/new-place#example-5). Name is string and metadata is a dictionary object.

- **Name**: The Name field specifies the active mode for a place. It uses an enumeration value, and the available options vary by place type. For desks, supported modes include `Reservable`, `Drop-In`, `Assigned` and `Unavailable`. For desk pools, the supported modes are `Reservable`, `Drop-In` and `Unavailable`.
- **Metadata**: The Metadata field is a dictionary used to store additional information relevant to the selected mode. This metadata supports business logic tied to specific booking scenarios.

  - Places in Reservable and Drop-In modes don't support any metadata fields.
  - Places in Unavailable mode support a `Reason` field \(string\) that explains why the desk is unavailable. Values include `New` for newly created desks and `Maintenance` for Places undergoing service.
  - Assigned mode supports two metadata fields: `AssignedPersonEmailAddress` and `AssignedPersonId`. These identify the user assigned to the desk. Providing either field is sufficient to enable the assigned mode.

| Attribute | Description |
| --- | --- |
| Type: | Mode |
| Position: | Named |
| Default value: | @{Name='Unavailable', Metadata={'Reason':'New'}} |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Type

The Type parameter specifies the type of the place that is being created. Valid values are:

- Building
- Floor
- Section
- Room
- Workspace
- Desk

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | True |
| Accept wildcard characters: | False |
