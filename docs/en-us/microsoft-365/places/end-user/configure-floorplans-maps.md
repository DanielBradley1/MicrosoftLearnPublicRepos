<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/end-user/configure-floorplans-maps -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Configure floorplans \(maps\)

While not strictly required, setting up floorplans makes the Microsoft Places experience better for end users. Floorplans allow users to see building layouts, find points of interest, and find nearby rooms and desks.

![Screenshot of how maps appear in Microsoft Places.](https://learn.microsoft.com/en-us/microsoft-365/places/media/setting-up-maps-in-places/maps-experience.png)

To add your floorplans to Microsoft Places, you need files in the IMDF format, with spatial information properly correlated to your building data, and georeferenced. Creating and correlating IMDF files can be complex. Microsoft recommends working with a specialized partner to streamline the process.

These partners have experience preparing IMDF files compatible with Microsoft Places:

- [Archilogic](https://www.archilogic.com/imdf-conversion-service)
- [Pointr](https://converter.pointr.cloud/)
- [Mappedin](https://mappedin.ca/imdf/microsoft-places/)
- [JLL Technologies \| OSIS](https://www.jllt.com/osis-ms-places/)

If you decide to work with one of these partners, check their own documentation. Otherwise, your ability to import the IMDF files into Microsoft Places might not work.

Note

Microsoft does not endorse these partners or guarantee their services. This list is not exhaustive. Other providers may also support IMDF conversion. All third-party services are subject to their own terms.

You can also manually prepare and correlate your IMDF files. See the **Alternative - Manual Setup** section, below.

## Tips

- The IMDF file should only contain elements for one building.

Before uploading the correlated IMDF files, make sure your buildings and floors are already configured in Microsoft Places. See [Configure buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/configuring-places/buildings-floors-sections).

Once you have the correlated IMDF files, you can upload them to Microsoft Places, one building at a time.

### Step 1 - Prepare your IMDF package

Ensure the following `.geojson` files are zipped directly, not in subfolders:

- `building.geojson` required
- `footprint.geojson` required
- `level.geojson` required
- `unit.geojson` required
- `section.geojson` optional
- `fixture.geojson` optional

Important

In order for furniture, such as desks and chairs, and sections to show in Microsoft Places, you need to include `section.geojson` and `fixture.geojson` in your IMDF files.

### Step 2 - Find the building PlaceId

Use [Get-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placev3) to find the identity of the building, also known as the `PlaceId`, for which you want to add maps.

Example of how to find the `PlaceId` for a building named `Austin 550`:

```powershell
Get-PlaceV3 -Type Building | ? {$_.DisplayName -eq 'Austin 550'} | ft DisplayName,PlaceId
```

### Step 3 - Import the map

Run the following cmdlet to import your correlated map files for your specified building:

```powershell
New-Map -BuildingId <BuildingPlaceId> -FilePath "[path\to\your\imdf_correlated.zip]"
```

Note

New maps may take up to 1 hour to appear in Microsoft Places.

## Alternative - Manual Setup

The following steps guide you in manually creating correlated IMDF files.

### Step 1 - Export spatial information for the building

Use [Get-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placev3) to find the identity, or `PlaceId`, of the building you want to add maps for.

Example of how to find the `PlaceId` for a building named `Austin 550`:

```powershell
Get-PlaceV3 -Type Building | ? {$_.DisplayName -eq 'Austin 550'} | ft DisplayName,PlaceId
```

Next, use the same cmdlet to export a CSV file that contains the relevant information for that building. You need to specify a location for the file.

Example:

```powershell
Get-PlaceV3 -AncestorId <BuildingPlaceId> | export-csv "[path\to\yourBuildingName.csv]" -NoTypeInformation
```

### Step 2 - Prepare your IMDF files

Create one ZIP file per building in IMDF format, with files zipped together directly, not in subfolders.

The ZIP file should contain the following `.geojson` files:

- `building.geojson` required
- `footprint.geojson` required
- `level.geojson` required
- `unit.geojson` required
- `section.geojson` optional
- `fixture.geojson` optional

In addition to adhering to the IMDF standards, there are specific requirements for Microsoft Places listed [here](https://learn.microsoft.com/en-us/microsoft-365/places/configure-maps-in-places).

Important

In order for furniture, such as desks and chairs, and sections to show in Microsoft Places, you need to include `section.geojson` and `fixture.geojson` in your IMDF files.

### Step 3 - Generate a correlation file

Use [Import-MapCorrelations](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/import-mapcorrelations) to parse your zipped IMDF files. This cmdlet generates a CSV file named `mapfeatures.csv`, which you use in step 4 to correlate your IMDF files with your building, floors, and rooms.

```powershell
Import-MapCorrelations -MapFilePath "[path\to\your\imdffile.zip]"
```

Note

This command fails if the IMDF package does not meet Microsoft Places requirements listed [here](https://learn.microsoft.com/en-us/microsoft-365/places/configure-maps-in-places).

### Step 4 - Correlate the spaces between the two CSV files

Open both files:

- The building CSV file created in Step 1
- The `mapfeatures.csv` file created in Step 3

For each building, floor, room, desk, and desk pool:

1. Copy the `PlaceId`, `Name`, and `Type` from the building CSV file.
2. Paste them into the corresponding row in the `mapfeatures.csv` file.
3. Save and close the file after completing the correlations.

Note

Building and all floor levels must be correlated in the `mapfeatures.csv` file. Importing the IMDF file fails if these features aren't correlated.

Leave items that you want uncorrelated with empty values for `PlaceId`, `Name`, and `Type`.

#### Example

If the building CSV includes a unit named "Room 1555", find the matching row in mapfeatures CSV. Copy the PlaceId, Name, and Type values from the building CSV and paste them into the corresponding row in mapfeatures CSV.

[![Screenshot of the two CSV files with arrows indicating which fields to correlate.](https://learn.microsoft.com/en-us/microsoft-365/places/media/setting-up-maps-in-places/mapping.jpg)](https://learn.microsoft.com/en-us/microsoft-365/places/media/setting-up-maps-in-places/mapping.jpg#lightbox)

This example shows the resulting mapfeatures CSV:

[![Screenshot of the mapfeatures.csv after correlation finishes.](https://learn.microsoft.com/en-us/microsoft-365/places/media/setting-up-maps-in-places/result.jpg)](https://learn.microsoft.com/en-us/microsoft-365/places/media/setting-up-maps-in-places/result.jpg#lightbox)

### Step 5 - Update the IMDF package

Run [Import-MapCorrelations](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/import-mapcorrelations) with your zipped IMDF file location and your correlated CSV file location, `mapfeatures.csv`.

```powershell
Import-MapCorrelations -MapFilePath "[path\to\your\imdffile.zip]" -CorrelationsFilePath "[path\to\mapfeatures.csv]"
```

This step creates and exports a new correlated ZIP file named `imdf_correlated.zip`.

### Step 6 - Importing your maps

Follow the steps in the [Importing your maps section](https://learn.microsoft.com/en-us/microsoft-365/places/end-user/configure-floorplans-maps) of this page to upload your correlated IMDF package.

## IMDF file requirements

[IMDF, indoor mapping data format](https://register.apple.com/resources/imdf/), is an open standard based on GeoJSON, originally developed by Apple, for representing indoor spatial data. Microsoft Places uses IMDF as the input format for floorplans, with extra extensions to support interactive map features.

Each file in the IMDF package must meet the following requirements:

- Must be georeferenced.
- Each IMDF package must contain data for only a *single* building.
- Floor ordinal value in the IMDF must match the `SortOrder` value of the corresponding floor in Microsoft Places Directory.

## Supported IMDF files

The supported set of IMDF feature types is provided in the following table. Other IMDF feature types aren't currently being rendered in Microsoft Places. However, these IMDF feature types may be supported in the future, so we recommend saving them if they're available.

| File type | IMDF feature type | Contents | Allowed geometry types | Example of objects |
| --- | --- | --- | --- | --- |
| `building.geojson` | [Building](https://register.apple.com/resources/imdf/types/building) | Metadata about the building | None, geometry shall be null | Building |
| `footprint.geojson` | [Footprint](https://register.apple.com/resources/imdf/types/footprint) | Outline of the building | Polygon, multipolygon | Building |
| `level.geojson` | [Level](https://register.apple.com/resources/imdf/types/level) | Features representing building floors | Polygon, multipolygon | Floors |
| `unit.geojson` | [Unit](https://register.apple.com/resources/imdf/types/unit) | Features representing spaces, walkways, and walls | Polygon, multipolygon | Rooms, workspaces, kitchenettes, restrooms, stairwells, elevators, walkways, and walls. Any space that is represented with a polygon on the map. Walls are also represented with closed polygon shapes. |
| `section.geojson` | [Section](https://register.apple.com/resources/imdf/types/section) | Section outline, optional | Polygon, multipolygon | Section |
| `fixture.geojson` | [Fixture](https://register.apple.com/resources/imdf/types/fixture) | Furniture or décor such as desks and chairs, optional | Polygon, multipolygon | Furniture, desks, equipment, and any items that are movable or semi-permanent |

## Optional Microsoft-specific extensions

To improve map accuracy and customization, Microsoft Places supports the following optional properties:

| Property | File | Purpose |
| --- | --- | --- |
| `bearing` | `level.geojson` | Sets the default rotation angle of the floorplan. This allows the map to display in a more natural orientation. |
| `rotation` | `fixture.geojson` | Allows individual desks to be rotated independently. This is helpful for spaces with uniquely angled desks or furniture layouts. |

These properties are optional and intended for advanced scenarios. Existing IMDF files do not need to be updated unless you want to take advantage of these enhancements.

## Known Limitations

### Uploading data for multiple buildings

- You can upload data for one building at a time. The IMDF package should include data across the whole building.
- To upload another building, repeat the process for each building.

### Making changes to the floorplan and associated data

In order to make any updates, first delete the map data for that building using the [Remove-Map](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/remove-map) cmdlet, and then reupload with the updated IMDF package using [New-Map](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/new-map).

```powershell
Remove-Map -BuildingId <BuildingPlaceId>

New-Map -BuildingId <BuildingPlaceId>
```

### Delegating map configuration and updates to other admins

Setting up floor plans in Places is only available via PowerShell and requires the Exchange Administrator role or Places Administrator role.
