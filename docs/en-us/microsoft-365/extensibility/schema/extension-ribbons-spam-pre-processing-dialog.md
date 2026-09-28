<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsSpamPreProcessingDialog object

Configures the preprocessing dialog of an [integrated spam-reporting](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting) add-in in Outlook.

Properties that reference this object type:

- [root.extensions.ribbons.spamPreProcessingDialog](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array?view=m365-app-1.30#spamPreProcessingDialog-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "title": "{string}",
  "description": "{string}",
  "spamNeverShowAgainOption": {boolean},
  "spamReportingOptions": {
    "title": "{string}",
    "options": [
      "{string}"
    ],
    "type": "radio | checkbox"
  },
  "spamFreeTextSectionTitle": "{string}",
  "spamMoreInfo": {
    "text": "{string}",
    "url": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "title": {
      "type": "string",
      "description": "Specifies the custom title of the preprocessing dialog.",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "Specifies the custom text that appears in the preprocessing dialog.",
      "maxLength": 250
    },
    "spamNeverShowAgainOption": {
      "type": "boolean",
      "description": "Indicating if the developer will allow the user to permanently bypass the PreProcessing Dialog for this add-in. \u0022false\u0022 is the default value if not specified.",
      "default": "false"
    },
    "spamReportingOptions": {
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
    },
    "spamFreeTextSectionTitle": {
      "type": "string",
      "description": "A text box to the preprocessing dialog to allow users to provide additional information on the message they\u0027re reporting. This value is the title of that text box.",
      "maxLength": 128
    },
    "spamMoreInfo": {
      "type": "object",
      "description": "Specifies the custom text and URL to provide informational resources to the users.",
      "properties": {
        "text": {
          "type": "string",
          "description": "Specifies display content of the hyperlink pointing to the site containing informational resources in the preprocessing dialog of a spam-reporting add-in.",
          "maxLength": 128
        },
        "url": {
          "type": "string",
          "description": "Specifies the URL of the hyperlink pointing to the site containing informational resources in the preprocessing dialog of a spam-reporting add-in.",
          "maxLength": 2048
        }
      },
      "required": [
        "text",
        "url"
      ]
    }
  },
  "required": [
    "title",
    "description"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "title": "{string}",
  "description": "{string}",
  "spamNeverShowAgainOption": {boolean},
  "spamReportingOptions": {
    "title": "{string}",
    "options": [
      "{string}"
    ],
    "type": "radio | checkbox"
  },
  "spamFreeTextSectionTitle": "{string}",
  "spamMoreInfo": {
    "text": "{string}",
    "url": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "title": {
      "type": "string",
      "description": "Specifies the custom title of the preprocessing dialog.",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "Specifies the custom text that appears in the preprocessing dialog.",
      "maxLength": 250
    },
    "spamNeverShowAgainOption": {
      "type": "boolean",
      "description": "Indicating if the developer will allow the user to permanently bypass the PreProcessing Dialog for this add-in. \u0022false\u0022 is the default value if not specified.",
      "default": "false"
    },
    "spamReportingOptions": {
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
    },
    "spamFreeTextSectionTitle": {
      "type": "string",
      "description": "A text box to the preprocessing dialog to allow users to provide additional information on the message they\u0027re reporting. This value is the title of that text box.",
      "maxLength": 128
    },
    "spamMoreInfo": {
      "type": "object",
      "description": "Specifies the custom text and URL to provide informational resources to the users.",
      "properties": {
        "text": {
          "type": "string",
          "description": "Specifies display content of the hyperlink pointing to the site containing informational resources in the preprocessing dialog of a spam-reporting add-in.",
          "maxLength": 128
        },
        "url": {
          "type": "string",
          "description": "Specifies the URL of the hyperlink pointing to the site containing informational resources in the preprocessing dialog of a spam-reporting add-in.",
          "maxLength": 2048
        }
      },
      "required": [
        "text",
        "url"
      ]
    }
  },
  "required": [
    "title",
    "description"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "title": "{string}",
  "description": "{string}",
  "spamReportingOptions": {
    "title": "{string}",
    "options": [
      "{string}"
    ]
  },
  "spamFreeTextSectionTitle": "{string}",
  "spamMoreInfo": {
    "text": "{string}",
    "url": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "title": {
      "type": "string",
      "description": "Specifies the custom title of the preprocessing dialog.",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "Specifies the custom text that appears in the preprocessing dialog.",
      "maxLength": 250
    },
    "spamReportingOptions": {
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
    },
    "spamFreeTextSectionTitle": {
      "type": "string",
      "description": "A text box to the preprocessing dialog to allow users to provide additional information on the message they\u0027re reporting. This value is the title of that text box.",
      "maxLength": 128
    },
    "spamMoreInfo": {
      "type": "object",
      "description": "Specifies the custom text and URL to provide informational resources to the users.",
      "properties": {
        "text": {
          "type": "string",
          "description": "Specifies display content of the hyperlink pointing to the site containing informational resources in the preprocessing dialog of a spam-reporting add-in.",
          "maxLength": 128
        },
        "url": {
          "type": "string",
          "description": "Specifies the URL of the hyperlink pointing to the site containing informational resources in the preprocessing dialog of a spam-reporting add-in.",
          "maxLength": 2048
        }
      },
      "required": [
        "text",
        "url"
      ]
    }
  },
  "required": [
    "title",
    "description"
  ]
}
```

## Properties

#### title

Specifies the custom title of the preprocessing dialog of a spam-reporting add-in.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### title

Specifies the custom title of the preprocessing dialog of a spam-reporting add-in.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### description

Specifies the custom text that appears in the preprocessing dialog of a spam-reporting add-in.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### description

Specifies the custom text that appears in the preprocessing dialog of a spam-reporting add-in.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### spamNeverShowAgainOption

Indicating if the developer will allow the user to permanently bypass the PreProcessing Dialog for this add-in. Default value: "false". To learn more, see [Suppress the preprocessing dialog](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting#suppress-the-preprocessing-dialog).

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `false`.

#### spamReportingOptions

Specifies up to five options that a user can select from the preprocessing dialog to provide a reason for reporting a message.

**Type**  
[spamReportingOptions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-reporting-options?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### spamFreeTextSectionTitle

Adds a text box to the preprocessing dialog for users to provide additional information on the message they're reporting. The string provided in this property appears above the text box.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### spamFreeTextSectionTitle

Adds a text box to the preprocessing dialog for users to provide additional information on the message they're reporting. The string provided in this property appears above the text box.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### spamMoreInfo

Configures a link to provide informational resources to a user. In the preprocessing dialog, the link appears below the text provided in `spamPreProcessingDialog.description`.

**Type**  
[spamMoreInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-more-info?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
