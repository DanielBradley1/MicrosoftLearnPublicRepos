<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheetprotection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookWorksheetProtection resource type

Namespace: microsoft.graph

Represents the protection of a sheet object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/worksheetprotection-get?view=graph-rest-1.0) | [workbookWorksheetProtection](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheetprotection?view=graph-rest-1.0) | Read the properties and relationships of a workbookWorksheetProtection object. |
| [Protect worksheet](https://learn.microsoft.com/en-us/graph/api/worksheetprotection-protect?view=graph-rest-1.0) | None | Protect a worksheet. Returns an error if the worksheet is already protected. |
| [Unprotect worksheet](https://learn.microsoft.com/en-us/graph/api/worksheetprotection-unprotect?view=graph-rest-1.0) | None | Unprotect a worksheet. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| options | [workbookWorksheetProtectionOptions](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheetprotectionoptions?view=graph-rest-1.0) | Worksheet protection options. Read-only. |
| protected | Boolean | Indicates whether the worksheet is protected. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "options": { "@odata.type": "microsoft.graph.workbookWorksheetProtectionOptions" },
  "protected": true
}
```
