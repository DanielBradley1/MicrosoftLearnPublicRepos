<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# requirementsExtensionElement object

The `extensions.requirements` object specifies the scopes, form factors, and Office JavaScript library requirement sets that must be supported on the Office client in order for the add-in to be installed. Requirements are also supported on child properties of `extensions` objects to selectively filter out some features of the add-in.

Important

Configuring requirements can be error prone. We strongly recommend that you familiarize yourself with [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest) and [Understand the logic of API requirement configuration](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/understand-requirement-configuration).

Properties that reference this object type:

- [root.extensions.alternates.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array?view=m365-app-1.30#requirements-property)
- [root.extensions.appDeeplinks.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-app-deeplinks-array?view=m365-app-1.30#requirements-property)
- [root.extensions.autoRunEvents.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array?view=m365-app-1.30#requirements-property)
- [root.extensions.contentRuntimes.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-content-runtime-array?view=m365-app-1.30#requirements-property)
- [root.extensions.contextMenus.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-context-menu-array?view=m365-app-1.30#requirements-property)
- [root.extensions.getStartedMessages.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-get-started-message-array?view=m365-app-1.30#requirements-property)
- [root.extensions.keyboardShortcuts.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30#requirements-property)
- [root.extensions.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#requirements-property)
- [root.extensions.ribbons.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array?view=m365-app-1.30#requirements-property)
- [root.extensions.runtimes.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30#requirements-property)

Properties that reference this object type:

- [root.extensions.alternates.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array?view=m365-app-1.30#requirements-property)
- [root.extensions.autoRunEvents.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array?view=m365-app-1.30#requirements-property)
- [root.extensions.contentRuntimes.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-content-runtime-array?view=m365-app-1.30#requirements-property)
- [root.extensions.contextMenus.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-context-menu-array?view=m365-app-1.30#requirements-property)
- [root.extensions.getStartedMessages.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-get-started-message-array?view=m365-app-1.30#requirements-property)
- [root.extensions.keyboardShortcuts.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30#requirements-property)
- [root.extensions.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#requirements-property)
- [root.extensions.ribbons.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array?view=m365-app-1.30#requirements-property)
- [root.extensions.runtimes.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30#requirements-property)

Properties that reference this object type:

- [root.extensions.alternates.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array?view=m365-app-1.30#requirements-property)
- [root.extensions.autoRunEvents.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array?view=m365-app-1.30#requirements-property)
- [root.extensions.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#requirements-property)
- [root.extensions.ribbons.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array?view=m365-app-1.30#requirements-property)
- [root.extensions.runtimes.requirements](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30#requirements-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "capabilities": [
    {
      "name": "{string}",
      "minVersion": "{string}",
      "maxVersion": "{string}"
    }
  ],
  "scopes": [
    "mail | workbook | document | presentation"
  ],
  "formFactors": [
    "desktop | mobile"
  ]
}
```

```json
{
  "type": "object",
  "description": "Specifies limitations on which clients the add-in can be installed on, including limitations on the Office host application, the form factors, and the requirement sets that the client must support.",
  "minProperties": 1,
  "properties": {
    "capabilities": {
      "type": "array",
      "minItems": 1,
      "maxItems": 100,
      "items": {
        "type": "object",
        "properties": {
          "name": {
            "type": "string",
            "description": "Identifies the name of the requirement sets that the add-in needs to run.",
            "maxLength": 128
          },
          "minVersion": {
            "type": "string",
            "description": "Identifies the minimum version for the requirement sets that the add-in needs to run."
          },
          "maxVersion": {
            "type": "string",
            "description": "Identifies the maximum version for the requirement sets that the add-in needs to run."
          }
        },
        "additionalProperties": false,
        "required": [
          "name"
        ]
      }
    },
    "scopes": {
      "type": "array",
      "description": "Identifies the scopes in which the add-in can run. For example, mail means Outlook.",
      "maxItems": 4,
      "items": {
        "type": "string",
        "enum": [
          "mail",
          "workbook",
          "document",
          "presentation"
        ]
      }
    },
    "formFactors": {
      "type": "array",
      "description": "Identifies the form factors that support the add-in. Supported values: mobile, desktop.",
      "minItems": 1,
      "maxItems": 2,
      "items": {
        "type": "string",
        "enum": [
          "desktop",
          "mobile"
        ]
      }
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "capabilities": [
    {
      "name": "{string}",
      "minVersion": "{string}",
      "maxVersion": "{string}"
    }
  ],
  "scopes": [
    "mail | workbook | document | presentation"
  ],
  "formFactors": [
    "desktop | mobile"
  ]
}
```

```json
{
  "description": "Specifies limitations on which clients the add-in can be installed on, including limitations on the Office host application, the form factors, and the requirement sets that the client must support.",
  "type": "object",
  "minProperties": 1,
  "properties": {
    "capabilities": {
      "type": "array",
      "minItems": 1,
      "maxItems": 100,
      "items": {
        "type": "object",
        "properties": {
          "name": {
            "type": "string",
            "description": "Identifies the name of the requirement sets that the add-in needs to run.",
            "maxLength": 128
          },
          "minVersion": {
            "type": "string",
            "description": "Identifies the minimum version for the requirement sets that the add-in needs to run."
          },
          "maxVersion": {
            "type": "string",
            "description": "Identifies the maximum version for the requirement sets that the add-in needs to run."
          }
        },
        "additionalProperties": false,
        "required": [
          "name"
        ]
      }
    },
    "scopes": {
      "type": "array",
      "description": "Identifies the scopes in which the add-in can run. Supported values: \u0027mail\u0027, \u0027workbook\u0027, \u0027document\u0027, \u0027presentation\u0027.",
      "minItems": 1,
      "maxItems": 4,
      "items": {
        "type": "string",
        "enum": [
          "mail",
          "workbook",
          "document",
          "presentation"
        ]
      }
    },
    "formFactors": {
      "type": "array",
      "description": "Identifies the form factors that support the add-in. Supported values: mobile, desktop.",
      "minItems": 1,
      "maxItems": 2,
      "items": {
        "type": "string",
        "enum": [
          "desktop",
          "mobile"
        ]
      }
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "capabilities": [
    {
      "name": "{string}",
      "minVersion": "{string}",
      "maxVersion": "{string}"
    }
  ],
  "scopes": [
    "mail | workbook | document | presentation"
  ],
  "formFactors": [
    "desktop | mobile"
  ]
}
```

```json
{
  "type": "object",
  "description": "Specifies limitations on which clients the add-in can be installed on, including limitations on the Office host application, the form factors, and the requirement sets that the client must support.",
  "minProperties": 1,
  "properties": {
    "capabilities": {
      "type": "array",
      "minItems": 1,
      "maxItems": 100,
      "items": {
        "type": "object",
        "properties": {
          "name": {
            "type": "string",
            "description": "Identifies the name of the requirement sets that the add-in needs to run.",
            "maxLength": 128
          },
          "minVersion": {
            "type": "string",
            "description": "Identifies the minimum version for the requirement sets that the add-in needs to run."
          },
          "maxVersion": {
            "type": "string",
            "description": "Identifies the maximum version for the requirement sets that the add-in needs to run."
          }
        },
        "additionalProperties": false,
        "required": [
          "name"
        ]
      }
    },
    "scopes": {
      "type": "array",
      "description": "Identifies the scopes in which the add-in can run. Supported values: \u0027mail\u0027, \u0027workbook\u0027, \u0027document\u0027, \u0027presentation\u0027.",
      "minItems": 1,
      "maxItems": 4,
      "items": {
        "type": "string",
        "enum": [
          "mail",
          "workbook",
          "document",
          "presentation"
        ]
      }
    },
    "formFactors": {
      "type": "array",
      "description": "Identifies the form factors that support the add-in. Supported values: mobile, desktop.",
      "minItems": 1,
      "maxItems": 2,
      "items": {
        "type": "string",
        "enum": [
          "desktop",
          "mobile"
        ]
      }
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "capabilities": [
    {
      "name": "{string}",
      "minVersion": "{string}",
      "maxVersion": "{string}"
    }
  ],
  "scopes": [
    "mail | workbook | document | presentation"
  ],
  "formFactors": [
    "desktop | mobile"
  ]
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "capabilities": {
      "type": "array",
      "minItems": 1,
      "maxItems": 100,
      "items": {
        "type": "object",
        "properties": {
          "name": {
            "type": "string",
            "description": "Identifies the name of the requirement sets that the add-in needs to run.",
            "maxLength": 128
          },
          "minVersion": {
            "type": "string",
            "description": "Identifies the minimum version for the requirement sets that the add-in needs to run."
          },
          "maxVersion": {
            "type": "string",
            "description": "Identifies the maximum version for the requirement sets that the add-in needs to run."
          }
        },
        "additionalProperties": false,
        "required": [
          "name"
        ]
      }
    },
    "scopes": {
      "type": "array",
      "description": "Identifies the scopes in which the add-in can run.",
      "minItems": 1,
      "maxItems": 4,
      "items": {
        "type": "string",
        "enum": [
          "mail",
          "workbook",
          "document",
          "presentation"
        ]
      }
    },
    "formFactors": {
      "type": "array",
      "description": "Identifies the form factors that support the add-in. Supported values: mobile, desktop.",
      "minItems": 1,
      "maxItems": 2,
      "items": {
        "type": "string",
        "enum": [
          "desktop",
          "mobile"
        ]
      }
    }
  },
  "additionalProperties": false
}
```

## Properties

#### capabilities

Identifies the [requirement sets](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/office-versions-and-requirement-sets).

Important

Configuring requirements can be error prone. We strongly recommend that you familiarize yourself with [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest) and [Understand the logic of API requirement configuration](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/understand-requirement-configuration).

**Type**  
Array of [capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element-capabilities?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 100.

**Supported values**  


#### scopes

Identifies the Microsoft 365 applications in which the extension can run, or in which the feature is accessible. This property should be used only to restrict the add-in or feature to a *proper subset* of the possible applications; `document` \(Word\), `mail` \(Outlook\), `presentation` \(PowerPoint\), and `workbook`\(Excel\). Including all the possible values in the array has the same effect as having no `scopes` property at all: the add-in will be installable \(or the feature will be accessible\) on *all* Office applications.

Important

Configuring requirements can be error prone. We strongly recommend that you familiarize yourself with [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest) and [Understand the logic of API requirement configuration](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/understand-requirement-configuration).

**Type**  
Array of string

**Required**  
—

**Constraints**  
Maximum array items: 4.

**Supported values**  
Allowed values: `mail`, `workbook`, `document`, `presentation`.

#### scopes

Identifies the Microsoft 365 applications in which the extension can run, or in which the feature is accessible. This property should be used only to restrict the add-in or feature to a *proper subset* of the possible applications; `document` \(Word\), `mail` \(Outlook\), `presentation` \(PowerPoint\), and `workbook`\(Excel\). Including all the possible values in the array has the same effect as having no `scopes` property at all: the add-in will be installable \(or the feature will be accessible\) on *all* Office applications.

Important

Configuring requirements can be error prone. We strongly recommend that you familiarize yourself with [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest) and [Understand the logic of API requirement configuration](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/understand-requirement-configuration).

**Type**  
Array of string

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 4.

**Supported values**  
Allowed values: `mail`, `workbook`, `document`, `presentation`.

#### formFactors

Identifies the form factors that support the add-in.

Important

Configuring requirements can be error prone. We strongly recommend that you familiarize yourself with [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest) and [Understand the logic of API requirement configuration](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/understand-requirement-configuration).

**Type**  
Array of string

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 2.

**Supported values**  
Allowed values: `desktop`, `mobile`.
