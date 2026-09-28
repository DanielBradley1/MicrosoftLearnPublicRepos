<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/remove-placedevice -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# Remove-PlaceDevice

## Syntax

```powershell
Remove-PlaceDevice
[-Id]
```

## Description

Remove-PlaceDevice cmdlet deletes a place device specified by its Id.

## Examples

**Example 1**

Deletes device from Microsoft places.

```powershell
Remove-PlaceDevice -Id 0f1894d4-668f-41e8-acdb-e5b7fbe71be5
```

## Parameters

### -ID \(required\)

ID of the place device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | True |
