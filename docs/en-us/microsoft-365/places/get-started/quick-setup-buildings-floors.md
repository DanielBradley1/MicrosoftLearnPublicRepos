<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# Configure buildings and floors

Microsoft Places depends on a fully established hierarchy of rooms/workspaces/desks, sections, floors, and buildings. This page guides you through the steps.

The **Initialize-Places** cmdlet parses existing rooms, and workspaces in your organization, and generates the hierarchy on your behalf. Specifically, the cmdlet uses the **RoomList** information to infer the building and floor name of each room, or workspace. The cmdlet builds a hierarchy of places, allows you to review and revise the results, and upload the final file.

Note

Starting July 28, 2026, for tenants that haven't built any places hierarchy, Microsoft Places will automatically generate the hierarchy based on the building and floor metadata configured on room mailboxes through [Set-Place](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-place). After the building visibility is enabled by setting the [EnableBuildings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings#-enablebuildings) parameter, users can see these buildings from the generated hierarchy in Places experience without running Initialize-Places or [manual setup](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors#alternative---manual-setup). Newly added building and floor metadata on room mailboxes through Set-Place will be reflected in the places hierarchy automatically through daily updates.

For tenants that have already created places hierarchies before this capability is introduced, the hierarchy generation will continue to be manual. The automatic hierarchy generation feature will not be applied.

Alternatively, to manually configure all of your buildings, floors, sections, workspaces, and rooms, see the [Alternative - Manual setup](#alternative---manual-setup) section of this article.

Important

By default, buildings are not visible across Microsoft Places experiences \(Work plans, Workplace presence, Places cards, and so on\).

You can enable building visibility in PowerShell:

```PowerShell
Set-PlacesSettings -EnableBuildings 'Default:true'
```

For more information, see [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings#-enablebuildings).

## Step 1 - Create buildings, floors, and sections hierarchy

1. Launch PowerShell7 as an Administrator.
2. Run `Install-Module -Name MicrosoftPlaces -Force` if Microsoft Places PowerShell module is not installed. \(this step needs to be done once per PC from which you plan to configure Microsoft Places\).
3. Run `Connect-MicrosoftPlaces`.
4. Finally, run `Initialize-Places`. You should see the following options:

   ```PowerShell
   Initialize-Places
   Please choose the desired option before continuing:
   1. Export suggested mapping CSV of rooms and workspaces to buildings/floors/sections.
   2. Import mapping CSV to automatically create buildings/floors/sections and mapping of rooms and workspaces.
   3. Export PowerShell script with commands to manually create buildings/floors/sections and mapping of rooms and workspaces based on an imported CSV.
   ```

5. Use Option `1` to create a CSV file.

## Step 2 - Review and revise the CSV

1. Add or correct building and floor names **in the first two columns** \(InferredBuildingName, InferredFloorName\). The other columns include more metadata which can help you update your building and floor names.
2. Remove all columns except InferredBuildingName, InferredFloorName, InferredSectionName, and PrimarySmtpAddress.
3. **Save and close this CSV file** before moving on to the next step.

## Step 3 - Upload the finalized CSV

1. Run the **Initialize-Places** cmdlet again and use Option `2` to import your CSV file.
2. The script generates a file summarizing the results and then exports the file to the same folder as the imported file.

## Step 4 - Verify

Open the account manager in Microsoft Teams, or the calendar in New Outlook, and check whether you can set your workplace presence to a specific building. For example:

| Teams account control |  |
| --- | --- |
| ![Screenshot of Teamscontrol1.](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/media/quick-setup-buildings-floors/teamscontrol1.png) | ![Screenshot of Teamscontrol2.](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/media/quick-setup-buildings-floors/teamscontrol2.png) |

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

1. Using Places management portal
2. Using PowerShell

### Manual setup using Places Management portal

The Places Management Portal allows you to manually create and manage buildings, floors, sections, rooms, workspaces, and desks through a user-friendly interface. You can access the portal via the [https://places.cloud.microsoft/places/admin/space-management](https://places.cloud.microsoft/places/admin/space-management) or through the Places Meta OS application within Microsoft Teams or Outlook. To use the portal, you must be assigned a built-in or custom role with the necessary permissions. Once inside the portal, you can:

1. Create new buildings.
2. Add floors associated with specific buildings.
3. Define sections within each floor.
4. Add rooms to a section or directly to a floor.
5. Add desk pools \(workspaces\) or individual desks to a section.
6. You can also use the management portal to add or update metadata for both new and existing Places objects, including buildings, floors, sections, rooms, workspaces, and desks.

Note

Not all built-in roles have permissions to create every type of Places object. For a detailed breakdown of role-specific permissions and capabilities, refer to the Configure administrator roles section.

### Manual setup using Places PowerShell

To set up places manually using PowerShell, you need to run individual PowerShell cmdlets to create each building and floor:

1. Create the building.
2. Create the floors with ParentId set to a building.
3. Create sections on all such floors. ParentId of sections should be set to a floor.
4. Set the room's ParentId to the floor \(or section, if desired\), as shown in the example. Workspace's ParentId must be set to a section.
5. Use [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3) to add any extra metadata on buildings, floors, or rooms/workspaces.

   ```PowerShell
   New-Place -Type Building -Name "Austin 550"
   New-Place -Type Floor -Name "1" -ParentId {PlaceId of Austin550}
   Set-PlaceV3 -Identity {smtpAddressOfRoom} -ParentId {PlaceId of Floor1}
   ```

For more information, see [New-Place](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/new-place) and [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3).

Note

Use Exchange PS cmdlets to create new rooms.

## Frequently Asked Questions

### Can I export all rooms, regardless of whether they're part of a roomlist?

Yes. Use [Get-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placev3) to export all rooms.

```PowerShell
Get-PlaceV3 -Type Room | Export-Csv -NoTypeInformation "C:\temp\rooms.csv"
```

### Do I have to set up all of my buildings, and floors at the same time?

No. You can run [Initialize-Places](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/initialize-places) as many times as you want, and, for example, focus on one building at a time. To do that, trim the rows in the CSV file generated at step 1 to only keep the builds/floors you're working on, and upload that CSV at step 3. Changes for a set of buildings, floors, and sections may not reflect if you generate a new CSV file immediately after uploading a CSV file.

Make sure buildings, floors, and sections are spelled the exact same way throughout the list. Any difference results in a new building, floor, or section being created.

### My security department wants to know what PowerShell commands are executed during import

You can use **Initialize-Places** Option `3` \(Export a PowerShell script\) to preview the commands that are executed. In this option, you must provide a CSV file with the same four-columns as shown in the [example](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors#example). Instead of setting up the buildings, floors, sections, workspaces, and rooms, Initialize-Places Option 3 exports a PowerShell script of the commands that would be executed during import. The PowerShell script is exported to the same folder as your import file.

Note

The import file is needed only to generate the PowerShell script. Nothing is imported on your behalf.

You can use the exported PowerShell script to run the commands yourself rather than using Initialize-Places Option 2.

### Can I run import with only building names?

No. Microsoft Places depends on a fully established hierarchy with Buildings > Floors > Sections > Rooms/workspaces. If you leave the section empty, the room is parented to the floor however workspaces aren't processed as workspaces always need to be parented to a section.

### How do I update room data, such as capacity, or display name?

You can do this using [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3).

## Troubleshooting

### I don't see the options described here when I run Initialize-Places

Make sure you're using the latest version of Microsoft Places PowerShell module. PowerShell might attempt to cache the installed module, so it's a good idea to use the -Force parameter.

```PowerShell
Install-Module –Name MicrosoftPlaces –AllowPrerelease -Force
```

### I created buildings, but they are not visible

Enable building visibility in PowerShell:

```PowerShell
Set-PlacesSettings -EnableBuildings 'Default:true'
```

For more information, see [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings#-enablebuildings).

### I receive an import error

Make sure that the CSV file is closed before importing it.

### I don't see all rooms/workspaces after importing

It can take up to 24 hours for room and workspaces associations to appear in Microsoft Places.
