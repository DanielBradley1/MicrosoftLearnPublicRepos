<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# extensionCommonCustomControlMenuItem object

Configures the items for a menu control.

Properties that reference this object type:

- [root.extensions.contextMenus.menus.controls.items](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#items-property)
- [root.extensions.ribbons.tabs.groups.controls.items](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#items-property)

Properties that reference this object type:

- [root.extensions.ribbons.tabs.groups.controls.items](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#items-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "type": "menuItem",
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
  "enabled": {boolean},
  "overriddenByRibbonApi": {boolean},
  "keytip": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Supported values: menuItem.",
      "enum": [
        "menuItem"
      ]
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the control. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
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
      "description": "The ID of an action defined in runtimes. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "default": "false"
    },
    "keytip": {
      "type": "string",
      "description": "KeyTip shortcut for keyboard navigation (1-3 uppercase alphanumeric characters)",
      "minLength": 1,
      "maxLength": 3,
      "pattern": "^[A-Z0-9]\u002B$"
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "type",
    "label",
    "supertip",
    "actionId"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "type": "menuItem",
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
  "enabled": {boolean},
  "overriddenByRibbonApi": {boolean},
  "keytip": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Supported values: menuItem.",
      "enum": [
        "menuItem"
      ]
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
      "description": "The ID of an action defined in runtimes. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "default": "false"
    },
    "keytip": {
      "type": "string",
      "description": "KeyTip shortcut for keyboard navigation (1-3 uppercase alphanumeric characters)",
      "minLength": 1,
      "maxLength": 3,
      "pattern": "^[A-Z0-9]\u002B$"
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "type",
    "label",
    "supertip",
    "actionId"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "type": "menuItem",
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
  "enabled": {boolean},
  "overriddenByRibbonApi": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this control within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "description": "Supported values: menuItem.",
      "enum": [
        "menuItem"
      ]
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
      "description": "The ID of an action defined in runtimes. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "default": "false"
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "type",
    "label",
    "supertip",
    "actionId"
  ]
}
```

## Properties

#### id

Specifies the ID for a menu item.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### type

Defines the menu item's control type.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `menuItem`.

#### label

Specifies the text displayed for the menu item.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### icons

Configures the icons for the menu item.

**Type**  
Array of [extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 3. Maximum array items: 8.

**Supported values**  


#### icons

Configures the icons for the menu item.

**Type**  
Array of [extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 3.

**Supported values**  


#### supertip

Configures a supertip for the menu item. A supertip is a UI feature that displays a brief box of help information about a control when the cursor hovers over it. The box may contain multiple lines of text.

**Type**  
[extensionCommonSuperToolTip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### actionId

Specifies the ID of the action that is taken when a user selects the control or menu item. The `actionId` must match with some `runtimes.actions.id` property value.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### enabled

Indicates whether the menu item is initially enabled.

Note

- This property isn't supported in Outlook add-ins.
- This property is supported only in menus on the ribbon, not in a context menu.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `True`.

#### overriddenByRibbonApi

Specifies whether the menu item is hidden on application and platform combinations which support the API \([Office.ribbon.requestCreateControls](https://learn.microsoft.com/en-us/javascript/api/office/office.ribbon#office-office-ribbon-requestcreatecontrols-member\(1\))\). This API installs custom contextual tabs on the ribbon.

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
  "items": [
    {
      "id": "menuItem1",
      "type": "menuItem",
      "label": "Action 2",
      "supertip": {
        "title": "Action 2 Title",
        "description": "Action 2 Description"
      },
      "actionId": "action2"
    },
  ]
}
```
