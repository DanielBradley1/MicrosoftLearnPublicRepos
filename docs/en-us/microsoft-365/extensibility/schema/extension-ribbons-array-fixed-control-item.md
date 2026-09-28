<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsArrayFixedControlItem object

Configures the button of an [integrated spam-reporting](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting) add-in in Outlook. Must configure if `spamReportingOverride` is specified in the `extensions.ribbons.contexts` array.

Properties that reference this object type:

- [root.extensions.ribbons.fixedControls](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array?view=m365-app-1.30#fixedControls-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "type": "button",
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
  "enabled": {boolean}
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
      "description": "Defines the type of control.",
      "enum": [
        "button"
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
      "description": "The ID of an execution-type action that handles this key combination. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "enabled": {
      "type": "boolean",
      "description": "Whether the control is initially enabled.",
      "default": true
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "supertip",
    "actionId",
    "enabled"
  ]
}
```

## Properties

#### id

Specifies the unique ID of the button of a spam-reporting add-in.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### type

Defines the control type of a spam-reporting add-in.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `button`.

#### label

Specifies the text that appears on button of a spam-reporting add-in.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### label

Specifies the text that appears on button of a spam-reporting add-in.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### icons

Defines the icons for the button of a spam-reporting add-in. There must be at least three child objects, each with icon sizes of `16`, `32`, and `80` pixels respectively.

**Type**  
Array of [extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1. Maximum array items: 3.

**Supported values**  


#### supertip

Configures a supertip for the button of a spam-reporting add-in.

**Type**  
[extensionCommonSuperToolTip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### actionId

Specifies the ID of the action taken when a user selects the button of a spam-reporting add-in. The `actionId` must match the `runtime.actions.id` property of an action in the `runtimes` object.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### enabled

This property must be specified in the `fixedControls` object. However, it doesn't affect the functionality of a spam-reporting add-in.

**Type**  
boolean

**Required**  
✅

**Constraints**  


**Supported values**  
Default value: `True`.
