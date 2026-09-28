<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionCommonCustomGroupControlsItem object

Configures the buttons and menus in the group.

Properties that reference this object type:

- [root.extensions.contextMenus.menus.controls](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-menu-item?view=m365-app-1.30#controls-property)
- [root.extensions.ribbons.tabs.groups.controls](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#controls-property)

Properties that reference this object type:

- [root.extensions.ribbons.tabs.groups.controls](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#controls-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "type": "button | menu",
  "builtInControlId": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "supertip": {
    "title": "{string}",
    "description": "{string}"
  },
  "actionId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "enabled": {boolean},
  "visible": {boolean},
  "items": [
    {
      "id": "{string}",
      "type": "menuItem",
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
      "enabled": {boolean},
      "overriddenByRibbonApi": {boolean},
      "keytip": "{string}"
    }
  ],
  "keytip": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Defines the type of control whether button or menu.",
      "enum": [
        "button",
        "menu"
      ]
    },
    "builtInControlId": {
      "type": "string",
      "description": "Id of an existing office control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "description": "Configures the icons for the custom control.",
      "type": "array",
      "minItems": 3,
      "maxItems": 8,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "supertip": {
      "$ref": "#/definitions/extensionCommonSuperToolTip"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group, button, menu, or menu item will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "visible": {
      "type": "boolean",
      "description": "Controls whether the control is visible.",
      "default": true
    },
    "items": {
      "type": "array",
      "description": "Configures the items for a menu control.",
      "minItems": 1,
      "maxItems": 30,
      "items": {
        "$ref": "#/definitions/extensionCommonCustomControlMenuItem"
      }
    },
    "keytip": {
      "type": "string",
      "description": "KeyTip shortcut for keyboard navigation (1-3 uppercase alphanumeric characters)",
      "minLength": 1,
      "maxLength": 3,
      "pattern": "^[A-Z0-9]\u002B$"
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "type": "button | menu",
  "builtInControlId": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "supertip": {
    "title": "{string}",
    "description": "{string}"
  },
  "actionId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "enabled": {boolean},
  "items": [
    {
      "id": "{string}",
      "type": "menuItem",
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
      "enabled": {boolean},
      "overriddenByRibbonApi": {boolean},
      "keytip": "{string}"
    }
  ],
  "visible": {boolean},
  "keytip": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Defines the type of control whether button or menu.",
      "enum": [
        "button",
        "menu"
      ]
    },
    "builtInControlId": {
      "type": "string",
      "description": "Id of an existing office control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "description": "Configures the icons for the custom control.",
      "minItems": 3,
      "maxItems": 8,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "supertip": {
      "$ref": "#/definitions/extensionCommonSuperToolTip"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group, button, menu, or menu item will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "items": {
      "type": "array",
      "description": "Configures the items for a menu control.",
      "minItems": 1,
      "maxItems": 30,
      "items": {
        "$ref": "#/definitions/extensionCommonCustomControlMenuItem"
      }
    },
    "visible": {
      "type": "boolean",
      "description": "Controls whether the control is visible.",
      "default": true
    },
    "keytip": {
      "type": "string",
      "description": "KeyTip shortcut for keyboard navigation (1-3 uppercase alphanumeric characters)",
      "minLength": 1,
      "maxLength": 3,
      "pattern": "^[A-Z0-9]\u002B$"
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "type": "button | menu",
  "builtInControlId": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "supertip": {
    "title": "{string}",
    "description": "{string}"
  },
  "actionId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "enabled": {boolean},
  "items": [
    {
      "id": "{string}",
      "type": "menuItem",
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
      "enabled": {boolean},
      "overriddenByRibbonApi": {boolean},
      "keytip": "{string}"
    }
  ],
  "keytip": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Defines the type of control whether button or menu.",
      "enum": [
        "button",
        "menu"
      ]
    },
    "builtInControlId": {
      "type": "string",
      "description": "Id of an existing office control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "description": "Configures the icons for the custom control.",
      "minItems": 3,
      "maxItems": 8,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "supertip": {
      "$ref": "#/definitions/extensionCommonSuperToolTip"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group, button, menu, or menu item will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "items": {
      "type": "array",
      "description": "Configures the items for a menu control.",
      "minItems": 1,
      "maxItems": 30,
      "items": {
        "$ref": "#/definitions/extensionCommonCustomControlMenuItem"
      }
    },
    "keytip": {
      "type": "string",
      "description": "KeyTip shortcut for keyboard navigation (1-3 uppercase alphanumeric characters)",
      "minLength": 1,
      "maxLength": 3,
      "pattern": "^[A-Z0-9]\u002B$"
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "id": "{string}",
  "type": "button | menu",
  "builtInControlId": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "supertip": {
    "title": "{string}",
    "description": "{string}"
  },
  "actionId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "enabled": {boolean},
  "items": [
    {
      "id": "{string}",
      "type": "menuItem",
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
      "enabled": {boolean},
      "overriddenByRibbonApi": {boolean},
      "keytip": "{string}"
    }
  ],
  "keytip": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Defines the type of control whether button or menu.",
      "enum": [
        "button",
        "menu"
      ]
    },
    "builtInControlId": {
      "type": "string",
      "description": "Id of an existing office control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "description": "Configures the icons for the custom control.",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "supertip": {
      "$ref": "#/definitions/extensionCommonSuperToolTip"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group, button, menu, or menu item will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "items": {
      "type": "array",
      "description": "Configures the items for a menu control.",
      "minItems": 1,
      "maxItems": 30,
      "items": {
        "$ref": "#/definitions/extensionCommonCustomControlMenuItem"
      }
    },
    "keytip": {
      "type": "string",
      "description": "KeyTip shortcut for keyboard navigation (1-3 uppercase alphanumeric characters)",
      "minLength": 1,
      "maxLength": 3,
      "pattern": "^[A-Z0-9]\u002B$"
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip"
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "id": "{string}",
  "type": "button | menu",
  "builtInControlId": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "supertip": {
    "title": "{string}",
    "description": "{string}"
  },
  "actionId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "enabled": {boolean},
  "items": [
    {
      "id": "{string}",
      "type": "menuItem",
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
      "enabled": {boolean},
      "overriddenByRibbonApi": {boolean}
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Defines the type of control whether button or menu.",
      "enum": [
        "button",
        "menu"
      ]
    },
    "builtInControlId": {
      "type": "string",
      "description": "Id of an existing office control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "description": "Configures the icons for the custom control.",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "supertip": {
      "$ref": "#/definitions/extensionCommonSuperToolTip"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group, button, menu, or menu item will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "items": {
      "type": "array",
      "description": "Configures the items for a menu control.",
      "minItems": 1,
      "maxItems": 30,
      "items": {
        "$ref": "#/definitions/extensionCommonCustomControlMenuItem"
      }
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip"
  ]
}
```

- [Syntax](#tabpanel_6_syntax)
- [Schema](#tabpanel_6_schema)

```json
{
  "id": "{string}",
  "type": "button | menu",
  "builtInControlId": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "supertip": {
    "title": "{string}",
    "description": "{string}"
  },
  "actionId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "enabled": {boolean},
  "items": [
    {
      "id": "{string}",
      "type": "menuItem",
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
      "enabled": {boolean},
      "overriddenByRibbonApi": {boolean}
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Defines the type of control whether button or menu.",
      "enum": [
        "button",
        "menu"
      ]
    },
    "builtInControlId": {
      "type": "string",
      "description": "Id of an existing office control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "description": "Configures the icons for the custom control.",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "supertip": {
      "$ref": "#/definitions/extensionCommonSuperToolTip"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group, button, menu, or menu item will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "items": {
      "type": "array",
      "description": "Configures the items for a menu control.",
      "minItems": 1,
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionCommonCustomControlMenuItem"
      }
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip"
  ]
}
```

- [Syntax](#tabpanel_7_syntax)
- [Schema](#tabpanel_7_schema)

```json
{
  "id": "{string}",
  "type": "button | menu",
  "builtInControlId": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "supertip": {
    "title": "{string}",
    "description": "{string}"
  },
  "actionId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "enabled": {boolean},
  "items": [
    {
      "id": "{string}",
      "type": "menuItem",
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
      "enabled": {boolean},
      "overriddenByRibbonApi": {boolean}
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Defines the type of control whether button or menu.",
      "enum": [
        "button",
        "menu"
      ]
    },
    "builtInControlId": {
      "type": "string",
      "description": "Id of the existing office control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "supertip": {
      "$ref": "#/definitions/extensionCommonSuperToolTip"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group, button, menu, or menu item will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "items": {
      "type": "array",
      "description": "Configures the items for a menu control.",
      "minItems": 1,
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionCommonCustomControlMenuItem"
      }
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip"
  ]
}
```

- [Syntax](#tabpanel_8_syntax)
- [Schema](#tabpanel_8_schema)

```json
{
  "id": "{string}",
  "type": "button | menu",
  "builtInControlId": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "supertip": {
    "title": "{string}",
    "description": "{string}"
  },
  "actionId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "enabled": {boolean},
  "items": [
    {
      "id": "{string}",
      "type": "menuItem",
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
      "enabled": {boolean},
      "overriddenByRibbonApi": {boolean}
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Defines the type of control whether button or menu.",
      "enum": [
        "button",
        "menu"
      ]
    },
    "builtInControlId": {
      "type": "string",
      "description": "Id of the existing office control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "supertip": {
      "$ref": "#/definitions/extensionCommonSuperToolTip"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group, button, menu, or menu item will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "items": {
      "type": "array",
      "description": "Configures the items for a menu control.",
      "minItems": 1,
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionCommonCustomControlMenuItem"
      }
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip",
    "actionId"
  ]
}
```

## Properties

#### id

Specifies the ID for the control within the app. It must be different from any other custom control and any built-in control ID in the Microsoft 365 application.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### type

Defines the control type.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `button`, `menu`.

#### builtInControlId

Specifies the ID of an existing Microsoft 365 control. For more information, see [Find the IDs of controls and control groups](https://learn.microsoft.com/en-us/office/dev/add-ins/design/built-in-button-integration#find-the-ids-of-controls-and-control-groups).

Important

This property can't be combined with any other child properties of the control object because built-in controls aren't customizable by an add-in.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### label

Specifies the text displayed for the control. Despite the maximum length of 64 characters, to correctly align the tab in the ribbon, we recommend you limit the label to 16 characters.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### icons

Defines the icons for the control. There must be at least three child objects; one each with `size` properties of `16`, `32`, and `80` pixels.

**Type**  
Array of [extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 3. Maximum array items: 8.

**Supported values**  


#### icons

Defines the icons for the control. There must be at least three child objects; one each with `size` properties of `16`, `32`, and `80` pixels.

**Type**  
Array of [extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1. Maximum array items: 3.

**Supported values**  


#### supertip

Configures a supertip for the control. A supertip is a UI feature that displays a brief box of help information about a control when the cursor hovers over it. The box may contain multiple lines of text.

**Type**  
[extensionCommonSuperToolTip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### actionId

Required if the control type is `button`. Don't use if the control type is `menu`. Specifies the ID of the action that is taken when a user selects the control. The `actionId` must match the `runtime.actions.id` property of an action in the `runtimes` object.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### actionId

Required if the control type is `button`. Don't use if the control type is `menu`. Specifies the ID of the action that is taken when a user selects the control. The `actionId` must match the `runtime.actions.id` property of an action in the `runtimes` object.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### overriddenByRibbonApi

Specifies whether the control is hidden on application and platform combinations which support the API \([Office.ribbon.requestCreateControls](https://learn.microsoft.com/en-us/javascript/api/office/office.ribbon#office-office-ribbon-requestcreatecontrols-member\(1\))\). This API installs custom contextual tabs on the ribbon.

The purpose of this property is to create a fallback experience in an add-in that implements custom contextual tabs when the add-in is running on an application or platform that doesn't support custom contextual tabs. The essential strategy is that you duplicate some or all of the groups and controls from your custom contextual tab onto a custom core tab \(that is, noncontextual custom tab\). Then, to ensure that these groups and controls appear when custom contextual tabs aren't supported, but don't appear when custom contextual tabs are supported, you set `overriddenByRibbonApi` to `true` for a parent `groups`, `controls`, or menu `items` properties. The effect of doing so is the following:

- If the add-in runs on an application and platform that support custom contextual tabs, then the duplicated groups and controls won't appear on the ribbon. Instead, the custom contextual tab will be installed when the add-in calls the `requestCreateControls` method.
- If the add-in runs on an application or platform that doesn't support custom contextual tabs, then the duplicated groups and controls will appear on the ribbon.

Note

For a full understanding of this property, see [Implement an alternate UI experience when custom contextual tabs aren't supported](https://learn.microsoft.com/en-us/office/dev/add-ins/design/contextual-tabs#implement-an-alternate-ui-experience-when-custom-contextual-tabs-are-not-supported).

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `false`.

#### enabled

Indicates whether the control is initially enabled. For more information, see [Change the availability of add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/design/disable-add-in-commands).

Note

This property isn't supported in Outlook add-ins.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `True`.

#### visible

Controls whether the control is visible.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `True`.

#### items

Configures the items for a menu control.

**Type**  
Array of [extensionCommonCustomControlMenuItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 30.

**Supported values**  


#### items

Configures the items for a menu control.

**Type**  
Array of [extensionCommonCustomControlMenuItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 20.

**Supported values**  


#### keytip

KeyTip shortcut for keyboard navigation \(1-3 uppercase alphanumeric characters\). To learn how to create custom KeyTips for your Office Add-in, see [Add custom KeyTips to your Office Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/add-custom-key-tips).

Note

This property isn't supported in Outlook add-ins.

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 3.

**Supported values**  
The string must match the following regular expression: `^[A-Z0-9]+$`.

## Examples

```json
{
    "controls": [
      {
        "id": "control1",
        "type": "button",
        "label": "Action 1",
        "icons": [
          {
            "size": 16,
            "url": "test_16.png"
          },
          {
            "size": 32,
            "url": "test_32.png"
          },
          {
            "size": 80,
            "url": "test_80.png"
          }
        ],
        "supertip": {
          "title": "Action 1 Title",
          "description": "Action 1 Description"
        },
        "actionId": "action1"
      }
    ]
}
```
