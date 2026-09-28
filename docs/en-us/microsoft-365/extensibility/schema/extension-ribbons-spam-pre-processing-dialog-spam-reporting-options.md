<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsSpamPreProcessingDialog.spamReportingOptions object

Specifies up to five options that a user can select from the preprocessing dialog to provide a reason for reporting a message.

Properties that reference this object type:

- [root.extensions.ribbons.spamPreProcessingDialog.spamReportingOptions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamReportingOptions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "title": "{string}",
  "options": [
    "{string}"
  ],
  "type": "radio | checkbox"
}
```

```json
{
  "type": "object",
  "description": "Specifies up to five options that a user can select from the preprocessing dialog to provide a reason for reporting a message.",
  "properties": {
    "title": {
      "type": "string",
      "description": "Specifies the title listed before the reporting options list.",
      "maxLength": 128
    },
    "options": {
      "type": "array",
      "description": "Specifies the custom options that a user can select from the preprocessing dialog to provide a reason for reporting a message.",
      "items": {
        "type": "string",
        "minItems": 1,
        "maxItems": 5
      }
    },
    "type": {
      "type": "string",
      "enum": [
        "radio",
        "checkbox"
      ],
      "description": "Can be set to \u0022radio\u0022 or \u0022checkbox\u0022. This determines if Radio Buttons or checkboxes are used for the options. \u0022checkbox\u0022 is the default if this value is not specified.",
      "default": "checkbox"
    }
  },
  "required": [
    "title",
    "options"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "title": "{string}",
  "options": [
    "{string}"
  ],
  "type": "radio | checkbox"
}
```

```json
{
  "type": "object",
  "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive.",
  "properties": {
    "title": {
      "type": "string",
      "description": "Specifies the title listed before the reporting options list.",
      "maxLength": 128
    },
    "options": {
      "type": "array",
      "description": "Specifies the custom options that a user can select from the preprocessing dialog to provide a reason for reporting a message.",
      "items": {
        "type": "string",
        "minItems": 1,
        "maxItems": 5
      }
    },
    "type": {
      "type": "string",
      "enum": [
        "radio",
        "checkbox"
      ],
      "description": "Can be set to \u0022radio\u0022 or \u0022checkbox\u0022. This determines if Radio Buttons or checkboxes are used for the options. \u0022checkbox\u0022 is the default if this value is not specified.",
      "default": "checkbox"
    }
  },
  "required": [
    "title",
    "options"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "title": "{string}",
  "options": [
    "{string}"
  ]
}
```

```json
{
  "type": "object",
  "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive.",
  "properties": {
    "title": {
      "type": "string",
      "description": "Specifies the title listed before the reporting options list.",
      "maxLength": 128
    },
    "options": {
      "type": "array",
      "description": "Specifies the custom options that a user can select from the preprocessing dialog to provide a reason for reporting a message.",
      "items": {
        "type": "string",
        "minItems": 1,
        "maxItems": 5
      }
    }
  },
  "required": [
    "title",
    "options"
  ]
}
```

## Properties

#### title

Specifies the custom text or title to describe the reporting options provided in the preprocessing dialog.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### title

Specifies the custom text or title to describe the reporting options provided in the preprocessing dialog.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### options

Specifies a custom option with a checkbox that a user can select from the preprocessing dialog to provide a reason for reporting a message. At least one option must be specified. A maximum of five options can be included.

**Type**  
Array of string

**Required**  
✅

**Constraints**  


**Supported values**  


#### options

Specifies a custom option with a checkbox that a user can select from the preprocessing dialog to provide a reason for reporting a message. At least one option must be specified. A maximum of five options can be included.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
Array of string

**Required**  
✅

**Constraints**  


**Supported values**  


#### type

The type of preprocessing dialog that appears when a user selects the spam reporting option. Can be set to "radio" or "checkbox". Default value: "checkbox". To learn more about spam preprocessing dialog options, see [Configure the manifest](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#configure-the-manifest).

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `radio`, `checkbox`.
