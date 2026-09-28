<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placev3 -->
<!-- Sitemap-Last-Modified: 2025-08-26 -->

# Get-PlaceV3

Use the Get-PlaceV3 cmdlet to view metadata configured on conference rooms, workspaces, buildings, floors, sections, or desks within the Places directory.

Note

- We recommend updating to Places PowerShell version 2.0.0 and above to ensure access to the latest features and improvements.

## Syntax

```powershell
Get-PlaceV3
   [-Identity]
   [-AncestorId]
   [-Type]
```

## Description

You must have the necessary permissions to run this cmdlet. You can use Places Administrator role, Exchange Administrator role, or a custom role with TenantPlacesManagement permissions.

## Examples

### Example 1

This example returns a room or workspace using its smtp address identifier.

```powershell
Get-PlaceV3 -Identity smtp@domain.com
```

### Example 2

This example returns all places of a certain type.

```powershell
Get-PlaceV3 -Type Building
```

### Example 3

This example returns the PlaceId based on a place's name and type.

```powershell
Get-PlaceV3 -Type Building | Where-Object -Property DisplayName -eq 'Pine Valley' | fl PlaceId
```

### Example 4

This example returns all places whose ancestor is a specific place.

```powershell
Get-PlaceV3 -AncestorId 86897e93-bcef-4c05-af9d-45116dda791f 
```

## Parameters

### -Identity

The identity parameter specifies the place that you want to view. You can use any value that uniquely identifies a place.

For example, for places based on a mailbox \(conference rooms and workspaces\):

- Name \[deprecated\]
- Alias \[deprecated\]
- Distinguished name \(DN\) \[deprecated\]
- Canonical DN \[deprecated\]
- GUID \[deprecated\]
- Email address

For example, for places that aren't based on a mailbox \(buildings, floors, sections or desks\):

- Name\_PlaceId
- PlaceId

This parameter can't be used together with the Type parameter.

| Attribute | Description |
| :--- | :--- |
| Type: | String |
| Position: | 0 |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | True |
| Accept wildcard characters: | False |

### -AncestorId

The AncestorId parameter specifies the guid of place. If the specified place found, it returns all places below this place in the directory hierarchy. For example, if a building's PlaceId is provided as the AncestorId, the command would return all floors, sections, rooms, desk pools \(workspaces\) and desks that are under that building in the directory hierarchy.

| Attribute | Description |
| :--- | :--- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |

### -Type

The Type parameter specifies the type of the place that you want to view. Valid values are:

- Room
- RoomList
- Space
- Building
- Floor
- Section
- Desk

This parameter can't be used together with the Identity parameter.

| Attribute | Description |
| :--- | :--- |
| Type: | String |
| Position: | Named |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | False |
| Accept wildcard characters: | False |
