<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placedevice -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# Get-PlaceDevice

## Syntax

```powershell
Get-PlaceDevice
[-Id]
[-Top]
[-Filter] 
```

## Description

Get-PlaceDevice cmdlet retrieves properties of existing place devices. Default number of devices to return is 1,000.

## Examples

**Example 1**

Fetch the info of a specific place device ID.

```powershell
Get-PlaceDevice -Id 0f1894d4-668f-41e8-acdb-e5b7fbe71be5
```

**Example 2**

Fetch the info of top 100 place devices.

```powershell
Get-PlaceDevice -Top 100
```

**Example 3**

Fetch info that matches the filter query string.

```powershell
Get-PlaceDevice -Filter "Tags/Any(x: cast(x, 'String') eq 'BuildingA')"
```

## Parameters

### -Id

ID of the Place device.

| Attribute | Description |
| --- | --- |
| Type: | Guid String |
| Required: | False |

### -Top

Specifies how many devices to return \(default is 10\).

| Attribute | Description |
| --- | --- |
| Type: | Integer |
| Required: | False |

### -Filter

Query string used to filter devices.

| Attribute | Description |
| --- | --- |
| Type: | Query String |
| Required: | False |
