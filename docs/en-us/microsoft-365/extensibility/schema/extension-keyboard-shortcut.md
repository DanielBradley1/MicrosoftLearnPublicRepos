<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionKeyboardShortcut object

[Keyboard shortcuts](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts), also known as key combinations, help users work more efficiently with your add-in. They also improve accessibility for users with disabilities by providing an alternative to mouse interactions.

Properties that reference this object type:

- [root.extensions.keyboardShortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#keyboardShortcuts-property)

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
  "shortcuts": [
    {
      "key": {
        extensionKeyCombination object
      },
      "actionId": "{string}"
    }
  ],
  "keyMappingFiles": {
    "shortcutsUrl": "{string}",
    "localizationResourceUrl": "{string}"
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "description": "Specifies the Office requirement sets.",
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "shortcuts": {
      "type": "array",
      "description": "Array of mappings from actions to the key combinations that invoke the actions.",
      "items": {
        "$ref": "#/definitions/extensionShortcut"
      },
      "minItems": 1,
      "maxItems": 20000
    },
    "keyMappingFiles": {
      "description": "Specifies the full URLs for shortcuts mapping and localization resource files that don\u0027t directly support the unified manifest.",
      "$ref": "#/definitions/keyboardShortcutsMappingFiles"
    }
  },
  "required": [
    "shortcuts"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

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
  "shortcuts": [
    {
      "key": {
        extensionKeyCombination object
      },
      "actionId": "{string}"
    }
  ],
  "keyMappingFiles": {
    "shortcutsUrl": "{string}",
    "localizationResourceUrl": "{string}"
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "description": "Specifies the Office requirement sets.",
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "shortcuts": {
      "type": "array",
      "description": "Array of mappings from actions to the key combinations that invoke the actions.",
      "items": {
        "$ref": "#/definitions/extensionShortcut"
      },
      "minItems": 1,
      "maxItems": 20000
    },
    "keyMappingFiles": {
      "description": "Specifies the full URLs for shortcuts mapping and localization resource files that don\u0027t directly support the unified manifest.",
      "$ref": "#/definitions/keyboardShortcutsMappingFiles"
    }
  }
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

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
  "shortcuts": [
    {
      "key": {
        extensionKeyCombination object
      },
      "actionId": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "description": "Specifies the Office requirement sets.",
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "shortcuts": {
      "type": "array",
      "description": "Array of mappings from actions to the key combinations that invoke the actions.",
      "items": {
        "$ref": "#/definitions/extensionShortcut"
      },
      "minItems": 1,
      "maxItems": 20000
    }
  },
  "required": [
    "shortcuts"
  ]
}
```

## Properties

#### requirements

Specifies the Office requirement sets.

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### shortcuts

Array of mappings from actions to the key combinations that invoke the actions.

**Type**  
Array of [extensionShortcut](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-shortcut?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 20000.

**Supported values**  


#### shortcuts

Array of mappings from actions to the key combinations that invoke the actions.

**Type**  
Array of [extensionShortcut](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-shortcut?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1. Maximum array items: 20000.

**Supported values**  


#### keyMappingFiles

Specifies the full URLs for shortcuts mapping and localization resource files that don't directly support the unified manifest.

**Type**  
[keyboardShortcutsMappingFiles](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/keyboard-shortcuts-mapping-files?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
