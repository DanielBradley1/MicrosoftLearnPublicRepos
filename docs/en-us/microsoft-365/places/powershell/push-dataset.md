<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/push-dataset -->
<!-- Sitemap-Last-Modified: 2025-08-11 -->

# Push-DataSet

The Push-Dataset cmdlet is used to send datasets \(specified by Type\) to Microsoft Places for analytics and reporting purposes.

## Syntax

```powershell
Push-dataset 
[-Type]
[-Path]
[-DeviceType]
```

## Description

This cmdlet uploads data for the same date it's used. If the cmdlet is run again on the same date, the previously uploaded data are overwritten.

## Examples

**Example 1**

Uploading the "badgeswipe" data:

1. This example shows two sample entries in CSV.

   ```CSV
   BadgeEntry1_BANGALORE-FERNS_MIRPL,BadgeIn,a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1,AlexW,AlexW@SkelligeIsland.OnMicrosoft.com,BANGALORE-FERNS_MIRPL,2024-06-28T09:36:05.144Z

   BadgeEntry1_BANGALORE-FERNS_MIRPL,BadgeIn,a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1,AllanD,AllanD@SkelligeIsland.OnMicrosoft.com,BANGALORE-FERNS_MIRPL,2024-06-28T10:36:05.144Z
   ```

2. Save this example in csv format in a folder, for example, C:\\sensordata.

   ```powershell
   Push-Dataset -Type BadgeSwipe -Path C:\sensordata\
   ```


   OR


   ```powershell
   Push-Dataset -Type BadgeSwipe -Path C:\sensordata\ -DeviceType Standard
   ```

**Example 2**

Uploading the "peoplecount" data:

1. This example shows two sample entries in CSV.

   ```CSV
   d3d3d3d3-eeee-ffff-aaaa-b4b4b4b4b4b4,a6a6a6a6-bbbb-cccc-dddd-e7e7e7e7e7e7,5, 2023-06-27T18:24:20.808Z,building1  
   d3d3d3d3-eeee-ffff-aaaa-b4b4b4b4b4b4,a6a6a6a6-bbbb-cccc-dddd-e7e7e7e7e7e7,5, 2023-06-27T18:24:20.808Z,building1
   ```

2. Save this example in csv format in a folder, for example, C:\\peoplecount\\

   ```powershell
     Push-Dataset -Type PeopleCount  -Path C:\peoplecount\
   ```


   OR


   ```powershell
      Push-Dataset -Type PeopleCount  -Path C:\peoplecount\ -DeviceType Standard
   ```

**Example 3**

Uploading the "roomoccupancy" data:

1. This example shows two sample entries in CSV.

   ```CSV
   d3d3d3d3-eeee-ffff-aaaa-b4b4b4b4b4b4,a6a6a6a6-bbbb-cccc-dddd-e7e7e7e7e7e7,true, 2023-06-27T18:24:20.808Z,building1  
   d3d3d3d3-eeee-ffff-aaaa-b4b4b4b4b4b4,a6a6a6a6-bbbb-cccc-dddd-e7e7e7e7e7e7,true, 2023-06-27T18:30:20.808Z,building1
   ```

2. Save this example in csv format in a folder, for example, C:\\roomoccupancy\\

   ```powershell
      Push-Dataset -Type roomoccupancy  -Path C:\roomoccupancy\
   ```


   OR


   ```powershell
      Push-Dataset -Type roomoccupancy  -Path C:\roomoccupancy\ -DeviceType Standard
   ```

## Parameters

**Mandatory Parameters**

### -Type

Type parameter specifies the type of dataset needs to be uploaded. Its value can be one of the following options:

- roomoccupancy
- peoplecount
- badgeswipe

### -Path

Path parameter specifies the location of dataset files on your device. It takes the folder path where file is kept in ".csv" format.

## Optional Parameters

### -DeviceType

DeviceType parameter can only have one value: Standard
