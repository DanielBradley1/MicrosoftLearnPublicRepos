<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/new-placedevice -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# New-PlaceDevice

## Syntax

```powershell
New-PlaceDevice
[-DeviceId]
[-DisplayName]
[-MACAddress]
[-Manufacturer]
[-IPV4Address]
[-IPV6Address]
[-PlaceId]
[-Tags]
[-Sensors] 
```

## Description

New-PlaceDevice cmdlet uploads new device properties to Microsoft Places.

## Examples

**Example 1**

Creates a new device in places with badge as sensor type.

```powershell
New-PlaceDevice -DeviceId "contoso_9D6816" -DisplayName "Contoso 9D6816 Device" -Description "Contoso 9D6816 Device" -MACAddress "00:0A:95:9D:68:16" -Manufacturer "Contoso" -IPV4Address "192.168.1.100" -IPV6Address "2001:db8::ff00:42:8329" -PlaceId "acfa3bc0- 2b83-425b-8910-84a0250e9671" -Tags "BuildingA" -Sensors (New-Object MicrosoftPlaces.PlacesDevices.Sensor -Property @{SensorType="badge"})
```

## Parameters

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

### -SensorId

User defined id of the sensor on the device.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Required: | False |

### -SensorType

Type of the Sensor.

| Attribute | Description |
| --- | --- |
| Type: | Enum \(badge/occupancy\) |
| Required: | True |
