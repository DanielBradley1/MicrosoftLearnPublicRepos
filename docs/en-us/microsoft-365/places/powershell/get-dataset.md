<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-dataset -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# Get-Dataset

## Syntax UPDATE

```powershell
Get-dataset
[-Type]
[-PushDate]
[-OutputDirectory]
[-Filename]
```

## Description

Get-Dataset cmdlet is used to download data. It can download a specific CSV file \(Filename\) on the tenant’s path based on the given dataset ID \(Type\) and date \(PushDate\) to location provided\(Output\).

## Examples

**Example 1**

```powershell
Get-Dataset -Type badgeswipe -PushDate "2024-11-05" -Output "C:\sensordata" -Filename "2024110507_7.csv"
```

## Parameters

### -Type

Type parameter specifies the type of dataset needs to be downloaded. Its value can be one of the following options:

- roomoccupancy
- peoplecount
- badgeswipe

### -PushDate

PushDate parameter specifies the date for which data needs to be downloaded.

### -OutputDirectory

OutputDirectory parameter specifies the folder in which data needs to be downloaded.

### -Filename

Filename parameter specifies the name of file needs to be downloaded.
