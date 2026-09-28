<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item-position?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsArrayTabsItem.position object

Configures the position of a custom tab relative to other tabs on the ribbon.

Properties that reference this object type:

- [root.extensions.ribbons.tabs.position](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#position-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "builtInTabId": "{string}",
  "align": "after | before"
}
```

```json
{
  "type": "object",
  "properties": {
    "builtInTabId": {
      "type": "string",
      "description": "The id of the built-in tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "align": {
      "type": "string",
      "description": "Define alignment of this custom tab relative to the specified built-in tab.",
      "enum": [
        "after",
        "before"
      ]
    }
  },
  "additionalProperties": false,
  "required": [
    "builtInTabId",
    "align"
  ]
}
```

## Properties

#### builtInTabId

Specifies the ID of the built-in tab that the custom tab should be positioned next to. For more information, see [Find the IDs of controls and control groups](https://learn.microsoft.com/en-us/office/dev/add-ins/design/built-in-button-integration#find-the-ids-of-controls-and-control-groups).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### align

Defines the alignment of custom tab relative to the specified built-in tab.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `after`, `before`.

## Remarks

Tab positioning is supported only in PowerPoint add-ins.
