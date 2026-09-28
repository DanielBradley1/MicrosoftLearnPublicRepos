<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placedevice -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# Set-PlaceDevice

## Syntax - Update

```powershell
Set-PlaceDevice
[-ID]  
[-DeviceId]  
[-DisplayName] 
[-Description] 
[-MACAddress] 
[-Manufacturer]  
[-IPV4Address] 
[-IPV6Address] 
[-PlaceId] 
[-Tags] 
[-Sensors] 
```

## Description

BSet-PlaceDevice cmdlet overwrites the existing place device properties based for the provided ID.

## Examples

**Example 1**

Updates all properties of an existing place device.

```powershell
Set-PlaceDevice -Id b8a9ad1c-a90f-4e1a-bad2-1720b8e58187 -DeviceId "contoso_7D6816" -DisplayName "Contoso 7D6816 Device" -Description "Contoso 9D6816 Device" -MACAddress "00:0A:95:9D:68:16" -Manufacturer "Contoso" -IPV4Address "192.168.1.100" -IPV6Address "2001:db8::ff00:42:8329" -PlaceId "acfa3bc0- 2b83-425b-8910-84a0250e9671" -Tags "BuildingA" -Sensors (New-Object MicrosoftPlaces.PlacesDevices.Sensor -Property @{SensorType="badge"})
```

## Parameters

### -Id

ID of the place device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | True |

### -DeviceId

User defined Id of the device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | True |

### -DisplayName

Name of the device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | False |

### -Description

Description of the device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | False |

### -MACAddress

MAC Address of the device provided by manufacturer.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | False |

### -Manufacturer

Name of the Manufacturer of the device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | True |

### -IPV4Address

IPV4 Address of the device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | False |

### -IPV6Address

IPV6 Address of the device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | False |

### -PlaceId

Id of the Place \(in Microsoft Places\) associated with the device.

| Attribute | Description |
| --- | --- |
| Type: | Guid String |
| Required: | False |

### -Tags

String used to filter out or identify the device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | False |

### -Sensors

Properties of the Sensor associated with the device.

| Attribute | Description |
| --- | --- |
| Type: | [MicrosoftPlaces.PlacesDevices.Sensor](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensor) |
| Required: | True |
