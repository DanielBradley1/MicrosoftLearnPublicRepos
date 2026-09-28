<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/remove-place -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Remove-Place

Use the Remove-Place cmdlet to delete buildings, floors, sections, rooms, workspaces, or desks from your Places directory. If a place object is associated with a mailbox, the mailbox is automatically soft-deleted upon deletion of the place object. A soft-deleted mailbox remains in Exchange for 30 days before it is permanently deleted.

Note

- We recommend updating to Places PowerShell version 2.0.0 and above to ensure access to the latest features and improvements.

## Syntax

```powershell
Remove-Place
   [-Identity]
```

## Description

You can't remove a place that is a parent of other places. Before removing a place, clear the ParentId value of its existing child places before attempting to remove. As an example, clear the ParentId value on all rooms associated with a given floor before deleting that floor.

Review [License Requirements](https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/license-requirements) if you plan to run this or any other Places commands.

Note

To automatically remove the mailbox, you need Place Administrator role, Exchange administrator role, or Global Admin role permission.

## Examples

### Example 1

Delete a floor based on its PlaceId.

```powershell
Remove-Place -Identity 86897e93-bcef-4c05-af9d-45116dda791f 
```

## Parameters

### -Identity

The identity parameter specifies the place that you want to view. You can use any value that uniquely identifies a place - either PlaceId or Name\_PlaceId.

| Attribute | Description |
| --- | --- |
| Type: | RecipientIdParameter |
| Position: | 0 |
| Default value: | None |
| Required: | False |
| Accept pipeline input: | True |
| Accept wildcard characters: | False |
