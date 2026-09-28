<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-datasetstatus -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# Get-DatasetStatus

## Syntax

```powershell
Get-DatasetStatus
[-Type]
[-PushDate]
```

## Description

Get-DatasetStatus cmdlet is used to retrieve the processing status of a dataset \(Type\) for a specific date \(PushDate\).

## Examples

**Example 1**

```powershell
Get-DatasetStatus -Type badgeswipe -PushDate "2024-10-02"
```

## Parameters

### -Type

Type parameter specifies the type of dataset for which status needs to be checked. Its value can be one of the following options:

- roomoccupancy
- peoplecount
- badgeswipe

### -PushDate

PushDate parameter specifies the date for which dataset status needs to be checked.
