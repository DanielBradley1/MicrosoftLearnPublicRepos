<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/configuring-places/buildings-floors-sections -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Configuring Places

## Buildings, floors, and sections

Microsoft Places depends on a fully established hierarchy of rooms/workspaces/desks, sections, floors, and buildings. This page guides you through the steps.

## Plan the workplace hierarchy

Most Places features depend on a structured hierarchy:

- Buildings
- Floors
- Sections
- Rooms
- Workspaces
- Desks

This hierarchy enables workplace presence, building-based location, desk booking, room discovery, space analytics, workplace services, and wayfinding. Because of this dependency, hierarchy configuration is the foundation of any deployment.

The **Initialize-Places** cmdlet parses existing rooms, and workspaces in your organization, and generates the hierarchy on your behalf. Specifically, the cmdlet uses the **RoomList** information to infer the building and floor name of each room, or workspace. The cmdlet builds a hierarchy of places, allows you to review and revise the results, and upload the final file.

Alternatively, to manually configure all of your buildings, floors, sections, workspaces, and rooms, see the [Alternative - Manual setup](https://learn.microsoft.com/en-us/microsoft-365/places/configuring-places/buildings-floors-sections) section of this article.

Important

By default, buildings are not visible across Microsoft Places experiences \(Work plans, Workplace presence, Places cards, and so on\).

You can enable building visibility in PowerShell:

```powershell
Set-PlacesSettings -EnableBuildings 'Default:true'
```

For more information, see [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings).

## Step 1 - Create buildings, floors, and sections hierarchy

1. Launch PowerShell 7 as an Administrator.
2. Run the following command if the Microsoft Places PowerShell module is not installed. This step needs to be done once per PC from which you plan to configure Microsoft Places.

   ```powershell
   Install-Module -Name MicrosoftPlaces -Force
   ```

3. Run the following command:

   ```powershell
   Connect-MicrosoftPlaces
   ```

4. Run the following command:

   ```powershell
   Initialize-Places
   ```

You should see the following options:

1. Export suggested mapping CSV of rooms and workspaces to buildings/floors/sections.
2. Import mapping CSV to automatically create buildings/floors/sections and mapping of rooms and workspaces.
3. Export PowerShell script with commands to manually create buildings/floors/sections and mapping of rooms and workspaces based on an imported CSV.

Note

Use Option 1 to create a CSV file.

## Step 2 - Review and revise the CSV

1. Add or correct building and floor names **in the first two columns**: `InferredBuildingName` and `InferredFloorName`. The other columns include more metadata which can help you update your building and floor names.
2. Remove all columns except `InferredBuildingName`, `InferredFloorName`, `InferredSectionName`, and `PrimarySmtpAddress`.
3. **Save and close this CSV file** before moving on to the next step.

## Step 3 - Upload the finalized CSV

1. Run the **Initialize-Places** cmdlet again and use Option 2 to import your CSV file.
2. The script generates a file summarizing the results and then exports the file to the same folder as the imported file.

## Step 4 - Verify

Open the account manager in Microsoft Teams, or the calendar in New Outlook, and check whether you can set your workplace presence to a specific building. For example:

| Teams account control |  |
| --- | --- |
| ![Screenshot of Teamscontrol1.](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/media/quick-setup-buildings-floors/teamscontrol1.png) | ![Screenshot of Teamscontrol2](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/media/quick-setup-buildings-floors/teamscontrol2.png) |

Note

New buildings, floors, and sections should be visible in Microsoft Places right away. However, any changes made to rooms, and workspaces may take up to 24 hours to update.

## Step 5 - Add metadata

Use **Set-PlaceV3** to add additional metadata on buildings, floors, and rooms/workspaces. We recommend adding capacity, A/V equipment, room pictures, etc. This step is optional and can be taken up later. Check out [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3) for the full list.

## Example

Here's what the CSV file generated at step 1 would look like for an organization with meeting rooms in two buildings, "Austin 550" and "NYC Times Square" and a desk pool in "NYC Times Square":

| InferredBuildingName | InferredFloorName | InferredSectionName | PrimarySmtpAddress |
| --- | --- | --- | --- |
| Austin 550 | Mezzanine |  | [baker@contoso.com](mailto:baker@contoso.com) |
| Austin 550 | 1 |  | [adams@contoso.com](mailto:adams@contoso.com) |
| Austin 550 | 2 |  | [rainier@contoso.com](mailto:rainier@contoso.com) |
| NYC Times Square | Unknown |  | [olympus@contoso.com](mailto:olympus@contoso.com) |
| NYC Times Square | Unknown | Unknown | [desks4.1.5@contoso.com](mailto:desks4.1.5@contoso.com) |

You should review all building, floor, and section names in the CSV file before uploading it as part of Step 3. In this example, you should fix the floor, and section names in the NYC building \(last two rows\).

## Alternative - Manual setup

Manual setup for the floor can be done in two ways:

- Using Places management portal
- Using PowerShell

## Manual setup using Places Management portal

The Places Management Portal allows you to manually create and manage buildings, floors, sections, rooms, workspaces, and desks through a user-friendly interface. You can access the portal via the [Places space management portal](https://places.cloud.microsoft/places/admin/space-management) or through the Places Meta OS application within Microsoft Teams or Outlook. To use the portal, you must be assigned a built-in or custom role with the necessary permissions.

Once inside the portal, you can:

- Create new buildings.
- Add floors associated with specific buildings.
- Define sections within each floor.
- Add rooms to a section or directly to a floor.
- Add desk pools \(workspaces\) or individual desks to a section.
- You can also use the management portal to add or update metadata for both new and existing Places objects, including buildings, floors, sections, rooms, workspaces, and desks.

Note

Not all built-in roles have permissions to create every type of Places object. For a detailed breakdown of role-specific permissions and capabilities, refer to the Configure administrator roles section.

## Manual setup using Places PowerShell

To set up places manually using PowerShell, you need to run individual PowerShell cmdlets to create each building and floor:

1. Create the building.
2. Create the floors with `ParentId` set to a building.
3. Create sections on all such floors. `ParentId` of sections should be set to a floor.
4. Set the room's `ParentId` to the floor or section, if desired, as shown in the example. Workspace's `ParentId` must be set to a section.
5. Use [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3) to add any extra metadata on buildings, floors, or rooms/workspaces.

```powershell
New-Place -Type Building -Name "Austin 550"
New-Place -Type Floor -Name "1" -ParentId {PlaceId of Austin550}
Set-PlaceV3 -Identity {smtpAddressOfRoom} -ParentId {PlaceId of Floor1}
```

For more information, see [New-Place](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/new-place) and [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3).

Note

Use Exchange PS cmdlets to create new rooms.

## Frequently Asked Questions

For more information, see [Configure buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/frequently-asked-questions#configure-buildings-and-floors).
