<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3 -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Set-PlaceV3

Use the Set-PlaceV3 cmdlet to update metadata about your desks, rooms, workspaces, sections, floors, or buildings within your Places directory.

Note

- We recommend updating to Places PowerShell version 2.0.0 and above to ensure access to the latest features and improvements.
- In Exchange hybrid environments, the `Set-PlaceV3` cmdlet can't be used to update the following properties on synchronized room mailboxes: City, CountryOrRegion, GeoCoordinates, Phone, PostalCode, State, and Street. Also, GeoCoordinates can't be set on synchronized room mailboxes. To set other properties, use the `Set-User` or `Set-Mailbox` cmdlets in on-premises Exchange.
- Updates to conference rooms & workspaces can take up to 24 hours to reflect. If you need to onboard multiple rooms and workspaces, we recommend using `Initialize-Places`, which is able to force the changes to reflect immediately.
- The `Set-UserPhoto` cmdlet was [deprecated](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecation-of-exchange-online-powershell-userphoto-cmdlets/ba-p/3955744) in April 2024. We are working to add a parameter to `Set-PlaceV3` to set a photo on rooms and workspaces. For now, go to [Add or update a user's profile information and settings in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-user-profile-info) to set the photo on a room or workspace.

## Syntax

### Building

```powershell
Set-PlaceV3
 [-Identity]
 [-DisplayName]
 [-Label]
 [-IsWheelChairAccessible]
 [-GeoCoordinates]
 [-Phone]
 [-Street]
 [-City]
 [-State]
 [-PostalCode]
 [-CountryOrRegion]
 [-ResourceLinks]
```

### Floor

```powershell
Set-PlaceV3
 [-Identity]
 [-DisplayName]
 [-ParentId]
 [-Label]
 [-SortOrder]
```

### Section

A section is a grouping of spaces within a floor, for example, a neighborhood. Desks and workspaces are required to be parented to a section. Rooms can also optionally be parented to a section or they can be directly parented to a floor.

```powershell
Set-PlaceV3
 [-Identity]
 [-DisplayName]
 [-ParentId]
 [-Label]
```

### Desk

Desks are a newly introduced entity type in Microsoft Places, representing individual desk units. Each desk includes a Mode property that specifies how the desk can be booked. For more information, refer to the mode section below.

For Desk, There are some dependencies between mode and mailbox as follows:

- If the Mode property is not defined, the desk defaults to Unavailable, and no desk mailbox is created automatically.
- For desks set to Reservable or DropIn mode, a desk mailbox is required. One is automatically created when the desk is provisioned. Alternatively, you can link an existing mailbox by specifying the EmailAddress in the Mailbox parameter.
- For desks in Assigned or Unavailable mode, linking a mailbox is optional, and no mailbox is created by default. However, you may manually associate these desks with custom mailboxes if needed.
- If no mode is configured initially, the desk remains in Unavailable mode. Linking a mailbox afterward does not automatically update the desk’s mode.

Unlike Room or Workspace types, desks are not automatically provisioned by simply creating a mailbox. Additionally, metadata such as Capacity or DisplayName is not synchronized with mailbox properties. The mailbox is used primarily by the reservation engine, while metadata is read from the Places Directory.

```powershell
Set-PlaceV3
 [-Identity]
 [-DisplayName]
 [-ParentId]
 [-Label]
 [-IsWheelChairAccessible]
 [-DisplayDeviceName]
 [-Tags]
 [-Mailbox]
 [-Mode]
```

### Room

Set-PlaceV3 supports legacy location parameters that are already available in the Exchange Set-Place cmdlet. However, once a room is linked to a floor or building using the `-ParentId ` parameter, location details \(`Street` and `City`\) should be managed at the building level—not on the individual room or workspace.

Note

The address fields \(Street, City, State, CountryOrRegion, and PostalCode\) set on the room or workspace mailbox object are ignored.

```powershell
Set-PlaceV3
 [-Identity]
 [-DisplayName]
 [-ParentId]
 [-Label]
 [-Capacity]
 [-IsWheelChairAccessible]
 [-AudioDeviceName]
 [-DisplayDeviceName]
 [-VideoDeviceName]
 [-MTREnabled]
 [-GeoCoordinates]
 [-Phone]
 [-Tags]
```

### Workspace

Set-PlaceV3 supports legacy location parameters that are already available in the Exchange Set-Place cmdlet. However, once a workspace is linked to a section using the `-ParentId ` parameter, location details \(`Street` and `City`\) should be managed at the building level—not on the individual room or workspace.

Note

The address fields \(Street, City, State, CountryOrRegion, and PostalCode\) set on the room or workspace mailbox object are ignored.

Workspace supports Mode property. The details for the same are documented in `Mode` parameter section.

```powershell
Set-PlaceV3
 [-Identity]
 [-DisplayName]
 [-ParentId]
 [-Label]
 [-Capacity]
 [-IsWheelChairAccessible]
 [-AudioDeviceName]
 [-DisplayDeviceName]
 [-VideoDeviceName]
 [-MTREnabled]
 [-GeoCoordinates]
 [-Phone]
 [-Tags]
 [-Mode]
```

## Description

Places depends on a fully set up hierarchy among your rooms/workspaces, floors, and buildings. Once buildings and floors are created, you can link them using parentId. A room should have a parent floor or section. A workspace or desk should have a parent section. A section should have a parent floor. A floor should have a parent building.

You need to be assigned permissions before you can run this cmdlet. You must have either the Exchange Admin role or the Places TenantPlacesManagement role.

Caution

You might find extra parameters in the PowerShell cmdlet, but those parameters aren't currently supported. Do not use any parameter that is not documented on this page.

## Examples

### Example 1

This example sets up the directory hierarchy for a room, floor, and building.

In this example, the floor's PlaceId is f12172b6-195d-4e6e-8f4f-eb72e41de99a, and the building's PlaceId is daa2f89b-75c4-4eb7-adcc-ff249233338d.

```powershell
Set-PlaceV3 -Identity 'room@contoso.com' -ParentId f12172b6-195d-4e6e-8f4f-eb72e41de99a
Set-PlaceV3 -Identity f12172b6-195d-4e6e-8f4f-eb72e41de99a -ParentId daa2f89b-75c4-4eb7-adcc-ff249233338d
```

### Example 2

This example updates a building's address.

```powershell
Set-PlaceV3 -Identity f12172b6-195d-4e6e-8f4f-eb72e41de99a -CountryOrRegion US -State WA -City Redmond -Street 'Street 3' -PostalCode 98052
```

### Example 3

This example updates a building's geo coordinates.

```powershell
Set-PlaceV3 -Identity f12172b6-195d-4e6e-8f4f-eb72e41de99a -GeoCoordinates "47.644125;-122.122411"
```

### Example 4

This example updates the resource links for a building with resource links. The entire set is replaced on update. To add or remove a value, be sure to include previous values that should be persisted.

```powershell
Set-PlaceV3 -Identity f12172b6-195d-4e6e-8f4f-eb72e41de99a -ResourceLinks @{name="TestLink";value="https://contoso.com/";type="Url"}
```

### Example 5

This example creates a reservable desk under a section without specifying mailbox details. A desk mailbox is automatically created and linked, and the MailboxOID property is populated. The desk appears in Places Finder and is available for booking by anyone.

```powershell
$section = New-Place -Name 'Section1' -Type Section -ParentId 'someFloorId'
New-Place -Name 'Reservable Desk101' -Type Desk -ParentId $section.PlaceId -Mode @{Name='Reservable'}
```

### Example 6

This example updates the mode value to DropIn mode.

```powershell
Set-PlaceV3 -Identity f12172b6-195d-4e6e-8f4f-eb72e41de99a -Mode @{Name='DropIn'}
```

### Example 7

This example updates the mode value to Assigned mode.

Note that even if the desk is already an assigned mode desk, the change is only the metadata field. A whole new mode object needs to be created and to replace the old one.

```powershell
$modemetadata = New-Object 'System.Collections.Generic.Dictionary[String,object]'
$modemetadata.Add("AssignedPersonEmailAddress","someUserEmailAddress")
Set-PlaceV3 -Identity f12172b6-195d-4e6e-8f4f-eb72e41de99a Mode @{Name='Assigned';Metadata=$modemetadata}
```

## Parameters

### -Identity

The identity parameter specifies the place that you want to update. You can use any value that uniquely identifies a place.

For example, for places based on a mailbox \(conference rooms and workspaces\):

- Name \[deprecated\]
- Alias \[deprecated\]
- Distinguished name \(DN\) \[deprecated\]
- Canonical DN \[deprecated\]
- GUID \[deprecated\]
- Email address

For example, for places that aren't based on a mailbox \(buildings, floors, sections and desks\):

- Name
- GUID

| Attribute | Description |
| --- | --- |
| Type: | RecipientIdParameter |
| Position: | 0 |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | True |
| Accept wildcard characters: | False |

### -AudioDeviceName, and -VideoDeviceName

These parameters specify the name of the audio, and video devices in the room. If the value contains spaces, enclose the value in quotation marks \("\).

The default value is blank \($null\). To indicate that this room has no audio, or video device, use the value $null for the parameter.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Building

Important

Building parameter is deprecated and provided here for backward compatibility only. Building information will be read from the Building entity that's on the parent chain of the room or workspace.

The Building parameter specifies the building name or building number that the room is in. If the value contains spaces, enclose the value in quotation marks \("\).

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Capacity

The Capacity parameter specifies the capacity of the room or workspace. A valid value is an integer.

Note

- The `Set-PlaceV3` cmdlet will update the following properties on synchronized mailboxes for room and workspace: Capacity and Name. To set those properties, you need Place Administrator role or Global Admin role permission.

| Attribute | Description |
| --- | --- |
| Type: | System.Int32 |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -City

The City parameter specifies the building's city. If the value contains spaces, enclose the value in quotation marks \("\). The maximum length is 200 characters.

Tip

There's a hierarchy between room/workspace -> floor -> building, and rooms/workspaces inherit the location attributes of their Building. The city information will be ignored for parented rooms and workspaces.

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

Tip

There's a hierarchy between room/workspace -> floor -> building, and rooms/workspaces inherit the location attributes of their Building. The CountryOrRegion information will be ignored for parented room and workspace.

| Attribute | Description |
| --- | --- |
| Type: | CountryInfo |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

> ### -Label

The Label parameter specifies a descriptive label for the place. If the value contains spaces, enclose the value in quotation marks \("\). The maximum length is 200 characters.

For rooms and workspaces, the command updates the value named -Label in Exchange Set-Place.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | True |
| Accept wildcard characters: | False |

### -DisplayDeviceName

The DisplayDeviceName parameter specifies the name of the display device in the place \(room, desk, or workspace\). If the value contains spaces, enclose the value in quotation marks \("\).

The default value is blank \($null\). To indicate that this place has no display device, use the value $null for this parameter.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -FloorLabel

The FloorLabel parameter specifies a descriptive label for the floor. If the value contains spaces, enclose the value in quotation marks \("\).

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Floor

The Floor parameter specifies the sort order of the floor within a particular building.

| Attribute | Description |
| --- | --- |
| Type: | System.Int32 |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -GeoCoordinates

The GeoCoordinates parameter specifies the building's location in latitude, longitude, and \(optionally\) altitude coordinates. A valid value for this parameter uses one of the following formats:

- Latitude and longitude: For example, "47.644125;-122.122411"
- Latitude, longitude, and altitude: For example, "47.644125;-122.122411;161.432"

If period separators don't work for you, use commas instead.

Tip

We recommend managing the location data on the Building rather than the Room/Workspace. There's a hierarchy between room/workspace -> floor -> building, and rooms/workspaces inherit the location attributes of their Building.

| Attribute | Description |
| --- | --- |
| Type: | GeoCoordinates |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -IsWheelChairAccessible

The IsWheelChairAccessible parameter specifies whether the place is wheelchair accessible. Valid values are:

- $true: The place is wheelchair accessible.
- $false: The place isn't wheelchair accessible. This is the default value.

| Attribute | Description |
| --- | --- |
| Type: | Boolean |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -MTREnabled

The MTREnabled parameter identifies the room as configured with a Microsoft Teams room system. You can add Teams room systems as audio sources in Teams meetings that involve the room. Valid values are:

- $true: The room has a Teams room system. You can add the Teams room system to Microsoft Teams meetings when selecting to join a meeting with room audio.
- $false: The room doesn't have a Teams room system. Users can join Teams meetings using their PC or mobile device audio instead of using room audio. This is the default value.

For more information about Microsoft Teams Rooms, see [Microsoft Teams Rooms](https://learn.microsoft.com/en-us/microsoftteams/rooms/).

| Attribute | Description |
| --- | --- |
| Type: | Boolean |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -DisplayName

The DisplayName parameter specifies the display name of the place. The maximum length is 200 characters. To update the display name of a room or workspace place that has an associated SMTP address, you need Place Administrator, Exchange Administrator or Global Admin role.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -ParentId

The ParentId parameter specifies the ID of a Place in the parent location hierarchy in Microsoft Places. A room should have a parent floor or section. A workspace or desk should have a parent section. A section should have a parent floor. A floor should have a parent building.

Note

If you need backward compatibility with Outlook Roomfinder, please make sure to also update the "Floor"/"FloorLabel" properties, in parallel with parenting the room to the floor entity. Places Finder will use the new hierarchy while Outlook Roomfinder will continue to use the legacy "Floor" and "FloorLabel" objects. You will also need to make sure the room is associated with a Roomlist, as documented here [Configure rooms and workspaces for Room Finder in Outlook](https://learn.microsoft.com/en-us/outlook/troubleshoot/calendaring/configure-room-finder-rooms-workspaces).

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -PostalCode

The PostalCode parameter specifies the building's postal code.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -ResourceLinks

The ResourceLinks parameter specifies external links or [Teams app](https://learn.microsoft.com/en-us/microsoftteams/apps-in-teams) IDs that should be associated to this building, such as a dining menu, a link to services or a Teams app for visitor management. For more information on how to set up services in Places, see [Services in Places](https://learn.microsoft.com/en-us/deployoffice/places/services-in-places).

The value must be provided as an array of links, as shown in [Example 4](https://learn.microsoft.com/en-us/deployoffice/places/powershell/set-placev3#example-4). Each link should contain the following properties: Name, Value, and Type. For example, a link would be written as @{name="TestLink"; value="https://contoso.com/"; type="Url"}.

- **Name**

  - This string is used to show how your link or app name is displayed in the Places app.
  - The maximum length is 200 characters.

- **Value**

  - This value should be either a url link or a Teams app ID. Teams app IDs can be found in the App Details page of the app in the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center.
  - The maximum length is 1,000 characters.

- **Type** must be one of the supported types:

  - Url - indicates that this is a url link.
  - MetaOsApp - indicates that this link is a Teams app.

Note

The entire set will be replaced on update. To add or remove a value, be sure to include previous values that should be persisted.

| Attribute | Description |
| --- | --- |
| Type: | Link\[\] |
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

Tip

There's a hierarchy between room/workspace -> floor -> building, and rooms/workspaces inherit the location attributes of their Building. The State information will be ignored for parented room and workspace.

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

Tip

There's a hierarchy between room/workspace -> floor -> building, and rooms/workspaces inherit the location attributes of their Building. The Street information will be ignored for parented room and workspace.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Mode

The Mode parameter defines how a place is intended to be used or booked. Currently, mode is only available for desks and desk pools\(workspaces\).

Currently, there are four modes in total.

- **Reservable**- Reservable desks are the desks that are configured to be booked in advance or on-the-spot.
- **Drop-in**- The desk is available for on-the-spot use and cannot be reserved in advance. You can use the capability from Microsoft Teams to link the peripheral devices present on these desks to the individual desk object in the directory.
- **Assigned** - An assigned desk is permanently linked to a specific user and cannot be booked by others. Every assigned desk must always have a designated user.
- **Unavailable**- The desk is not available for reservation due to maintenance or for any other reason.

The mode value should contain the following properties: Name and Metadata, as shown in [Example 6](https://learn.microsoft.com/en-us/deployoffice/places/powershell/new-place#example-6). Name is string and metadata is a dictionary object.

- **Name**: The Name field specifies the active mode for a place. It uses an enumeration value, and the available options vary by place type. For desks, supported modes include `Reservable`, `DropIn`, `Assigned` and `Unavailable`. For desk pools, the supported modes are `Reservable`, `DropIn` and `Unavailable`.
- **Metadata**: The Metadata field is a dictionary used to store additional information relevant to the selected mode. This metadata supports business logic tied to specific booking scenarios.

  - Places in Reservable and DropIn modes do not support any metadata fields.
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

### -Tags

The Tags parameter specifies additional features of the room \(for example, details like the type of view or furniture type\). There's no maximum length currently.

You can specify multiple labels separated by commas. If the labels contains spaces, enclose the values in quotation marks: `"Label 1","Label 2",..."Label N"`.

Note

The entire set will be replaced on update. To add or remove a value, be sure to include previous values that should be persisted.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

## Troubleshooting

### I am receiving a permission denied error.

Set-PlaceV3 requires one of the following roles: TenantPlacesManagement, GlobalAdmin, or MailRecepients. Because roles can be assigned in different ways, the following are the supported ways to assign role permissions:

- If the permission is assigned through Exchange Admin Center \(which only supports permanent permissions\), you should have no issues with using the Places cmdlets. It wouldn't be expected for you to see a Permission Denied error.
- If the permission is assigned through Entra directly to the user \(as a permanent or a temporary role\), you should have no issues with using the Places cmdlets. It wouldn't be expected for you to see a Permission Denied error. However, there might be some delay in the sync between Entra and Exchange.
- If the permission is assigned through Entra to a group in Entra, which the user is a part of, this isn't supported by Exchange and the role-through-group won't be respected. Exchange cmdlets and Places cmdlets will both fail with permission denied. This expected behavior is described [here](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo).

### I assigned a ParentId to a resource, but I don't see it yet in Places Finder.

It can take up to 24 hours for the correlation between the resource and its parent Floor to appear in Places experiences. We're working on eliminating this delay.

### How do I set a photo on a resource?

The Set-UserPhoto was [deprecated](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecation-of-exchange-online-powershell-userphoto-cmdlets/ba-p/3955744) in April 2024. We're working on adding a parameter to this cmdlet to set a photo on rooms and workspaces when using Set-PlaceV3. In the meantime, please follow [these instructions](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/change-user-profile-photos) set the photo on a room or workspace.

It is not currently possible to set photos on a building or on a floor.
