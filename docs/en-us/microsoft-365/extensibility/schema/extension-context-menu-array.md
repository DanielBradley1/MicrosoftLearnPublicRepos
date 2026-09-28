<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-context-menu-array?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionContextMenuArray object

Specifies the context menus for your extension. A context menu is a shortcut menu that appears when a user right-clicks \(selects and holds\) in the Office UI. To learn more see [how to design your Office Add-in UI](https://learn.microsoft.com/en-us/office/dev/add-ins/design/add-in-design).

Properties that reference this object type:

- [root.extensions.contextMenus](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#contextMenus-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "menus": [
    {
      "entryPoint": "text | cell",
      "controls": [
        {
          extensionCommonCustomGroupControlsItem object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "type": "object",
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "menus": {
      "$ref": "#/definitions/extensionMenuItem",
      "description": "Configures the context menus. Minimum size is 1."
    }
  },
  "additionalProperties": false,
  "required": [
    "menus"
  ]
}
```

## Properties

#### requirements

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### menus

Configures the context menus. Minimum size is 1.

**Type**  
Array of [extensionMenuItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-menu-item?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1.

**Supported values**
