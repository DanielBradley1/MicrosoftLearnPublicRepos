<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/import-mapcorrelations -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Import-MapCorrelations

Use the Import-MapCorrelations cmdlet to prepare correlated IMDF zip file. The cmdlet should be run twice in sequence:

1. First run: Parse your IMDF zip file and extract map features into a CSV file named mapfeatures.csv, which you use to manually correlate map features with Places buildings, floors, and rooms.
2. Second run: Populate correlations \(in mapfeatures.csv\) into the original IMDF zip file to generate correlated IMDF zip file, which you upload with New-Map cmdlet.

Tip

The Import-MapCorrelations cmdlet is part of the map onboarding workflow. It is recommended to read [Configure floorplans](https://learn.microsoft.com/en-us/microsoft-365/places/end-user/configure-floorplans-maps) first and follow the step-by-step guide there to configure floorplans.

## Syntax

First run

```powershell
Import-MapCorrelations -MapFilePath "[path\to\your\imdffile.zip]"
```

Second run

```powershell
Import-MapCorrelations -MapFilePath "[path\to\your\imdffile.zip]" -CorrelationsFilePath "[path\to\mapfeatures.csv]"
```

## Description

Prior to using this cmdlet, you should make sure you have a valid IMDF zip package ready. For requirements on IMDF zip package, see [Configure floorplans](https://learn.microsoft.com/en-us/microsoft-365/places/end-user/configure-floorplans-maps).

Between the first and second run of Import-MapCorrelations cmdlet, you need to manually correlate Places buildings, floors, and rooms into mapfeatures.csv. The correlation data will subsequently be populated into IMDF zip package. For instructions on how to do manual correlations, see [Configure floorplans](https://learn.microsoft.com/en-us/microsoft-365/places/end-user/configure-floorplans-maps).

## Examples

**Example 1**

Run Import-MapCorrelations to extract map features into mapfeatures.csv \(first run\).

```powershell
Import-MapCorrelations -MapFilePath "C:\Document\IMDF.zip"
```

### Parameters

#### -MapFilePath

File path to the IMDF zip file.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

**Example 2**

Run Import-MapCorrelations with mapfeatures.csv and IMDF zip file to generate correlated IMDF zip file \(second run\).

```powershell
Import-MapCorrelations -MapFilePath "C:\Document\IMDF.zip" -CorrelationsFilePath "C:\Document\mapfeatures.csv"
```

### Parameters

#### -CorrelationsFilePath

File path to the mapfeatures.csv \(should contain correlations info\).

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -MapFilePath

File path for the IMDF zip file.

| Attribute | Description |
| --- | --- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | True |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |
