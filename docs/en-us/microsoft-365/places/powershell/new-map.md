<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/new-map -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# New-Map

Use the New-Map cmdlet to import floorplans \(maps\) for a building. To add your floorplans to Microsoft Places, you'll need files in the IMDF format, with spatial information properly correlated to your building data, and georeferenced. For requirements on IMDF files and for instructions on correlation, see [Configure floorplans](https://learn.microsoft.com/en-us/microsoft-365/places/end-user/configure-floorplans-maps).

Tip

The New-Map cmdlet is part of the map onboarding workflow. It is recommended to read [Configure floorplans](https://learn.microsoft.com/en-us/microsoft-365/places/end-user/configure-floorplans-maps) and follow the step-by-step guide there to configure floorplans.

## Syntax

```powershell
New-Map -BuildingId <BuildingPlaceId> -FilePath "[path\to\your\imdf_correlated.zip]" 
```

## Description

Before you upload your floorplans, you need to make sure:

- Buildings and floors are configured in Places Directory
- IMDF files meet Microsoft Places requirements
- Map features in the IMDF files are correlated with Places Directory buildings/floors/rooms

See [Configure buildings, floors, and sections](https://learn.microsoft.com/en-us/microsoft-365/places/configuring-places/buildings-floors-sections) for instructions.

Note

New maps may take up to 1 hour to be reflected in Microsoft Places.

You can only upload data for one building at a time. To upload another building, you should follow the process again for that new building.

## Examples

**Example 1**

Upload floorplans for a building.

```powershell
New-Map -BuildingId 86897e93-bcef-4c05-af9d-45116dda791f -FilePath "C:\Document\correlated_imdf.zip" 
```

### Parameters

#### -BuildingId

PlaceId for the building to upload floorplans.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

#### -FilePath

File path for the IMDF zip file.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |
