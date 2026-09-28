<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/remove-map -->
<!-- Sitemap-Last-Modified: 2024-11-01 -->

# Remove-Map

Use the Remove-Map cmdlet to remove floorplans for a building.

## Syntax

```powershell
Remove-Map -BuildingId <BuildingPlaceId>
```

## Description

Only removing floorplans for a building is supported. When removing floorplans for a building, all the floorplans associated with the building will be removed, including all the floors that are parented to this building.

## Examples

**Example 1**

Remove floorplans for a building based on its Building PlaceId.

```powershell
Remove-Map -BuildingId 86897e93-bcef-4c05-af9d-45116dda791f
```

### Parameters

#### -BuildingId

PlaceId for the building to remove floorplans.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |
