<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-menu-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionMenuItem object

The title used for the top of the callout.

Properties that reference this object type:

- [root.extensions.contextMenus.menus](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-context-menu-array?view=m365-app-1.30#menus-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "entryPoint": "text | cell",
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "visible": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ],
      "keytip": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "entryPoint": {
      "type": "string",
      "description": "Use \u0027text\u0027 or \u0027cell\u0027 here for Office context menu. Use text if the context menu should open when a user right-clicks (selects and holds) on the selected text. Use cell if the context menu should open when the user right-clicks (selects and holds) on a cell in an Excel spreadsheet.",
      "enum": [
        "text",
        "cell"
      ]
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem"
      },
      "minItems": 1
    }
  },
  "additionalProperties": false,
  "required": [
    "entryPoint",
    "controls"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "entryPoint": "text | cell",
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ],
      "visible": {boolean},
      "keytip": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "entryPoint": {
      "type": "string",
      "description": "Use \u0027text\u0027 or \u0027cell\u0027 here for Office context menu. Use \u0027text\u0027 if the context menu should open when a user right-clicks (selects and holds) on the selected text. Use \u0027cell\u0027 if the context menu should open when the user right-clicks (selects and holds) on a cell in an Excel spreadsheet.",
      "enum": [
        "text",
        "cell"
      ]
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem",
        "description": "The control type should be \u0027menu\u0027. Minimum size is 1."
      },
      "minItems": 1
    }
  },
  "additionalProperties": false,
  "required": [
    "entryPoint",
    "controls"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "entryPoint": "text | cell",
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ],
      "keytip": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "entryPoint": {
      "type": "string",
      "description": "Use \u0027text\u0027 or \u0027cell\u0027 here for Office context menu. Use \u0027text\u0027 if the context menu should open when a user right-clicks (selects and holds) on the selected text. Use \u0027cell\u0027 if the context menu should open when the user right-clicks (selects and holds) on a cell in an Excel spreadsheet.",
      "enum": [
        "text",
        "cell"
      ]
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem",
        "description": "The control type should be \u0027menu\u0027. Minimum size is 1."
      },
      "minItems": 1
    }
  },
  "additionalProperties": false,
  "required": [
    "entryPoint",
    "controls"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "entryPoint": "text | cell",
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
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
    "entryPoint": {
      "type": "string",
      "description": "Use \u0027text\u0027 or \u0027cell\u0027 here for Office context menu. Use \u0027text\u0027 if the context menu should open when a user right-clicks (selects and holds) on the selected text. Use \u0027cell\u0027 if the context menu should open when the user right-clicks (selects and holds) on a cell in an Excel spreadsheet.",
      "enum": [
        "text",
        "cell"
      ]
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem",
        "description": "The control type should be \u0027menu\u0027. Minimum size is 1."
      },
      "minItems": 1
    }
  },
  "additionalProperties": false,
  "required": [
    "entryPoint",
    "controls"
  ]
}
```

## Properties

#### entryPoint

Use text or cell here for Office context menu. Use text if the context menu should open when a user right-clicks on the selected text. Use cell if the context menu should open when the user right-clicks on a cell on an Excel spreadsheet.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `text`, `cell`.

#### controls

**Type**  
Array of [extensionCommonCustomGroupControlsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1.

**Supported values**
