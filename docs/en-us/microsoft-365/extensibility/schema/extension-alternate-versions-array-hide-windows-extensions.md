<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray.hide.windowsExtensions object

Configures how to hide Windows-only types of extensions in favor of Office Web Add-in versions that run cross-platform \(for example in Office on the web or Mac\). For more information, see [Option to disable Windows-only add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in#option-to-disable-the-windows-only-add-in-instead-preview) in the Office Add-ins documentation.

Properties that reference this object type:

- [root.extensions.alternates.hide.windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide?view=m365-app-1.30#windowsExtensions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "effect": "userOptionToDisable | disableWithNotification",
  "comAddin": {
    "progIds": [
      "{string}"
    ]
  },
  "automationAddin": {
    "progIds": [
      "{string}"
    ]
  },
  "xllCustomFunctions": {
    "fileNames": [
      "{string}"
    ]
  }
}
```

```json
{
  "type": "object",
  "description": "Configures how to hide windows native extensions",
  "properties": {
    "effect": {
      "type": "string",
      "description": "Specifies the effect to take while installing the web add-in if the equivalent add-in is installed.",
      "enum": [
        "userOptionToDisable",
        "disableWithNotification"
      ]
    },
    "comAddin": {
      "type": "object",
      "description": "Specifies the equivalent COM or VSTO add-ins",
      "properties": {
        "progIds": {
          "type": "array",
          "description": "Specifies the program Ids of the equivalent COM add-ins and the names of equivalent VSTO add-ins",
          "minItems": 1,
          "maxItems": 5,
          "items": {
            "type": "string",
            "minLength": 1,
            "maxLength": 64
          }
        }
      },
      "additionalProperties": false,
      "required": [
        "progIds"
      ]
    },
    "automationAddin": {
      "type": "object",
      "description": "Specifies the equivalent automation add-ins",
      "properties": {
        "progIds": {
          "type": "array",
          "description": "Specifies the program Ids of the equivalent automation add-ins",
          "minItems": 1,
          "maxItems": 5,
          "items": {
            "type": "string",
            "minLength": 1,
            "maxLength": 64
          }
        }
      },
      "additionalProperties": false,
      "required": [
        "progIds"
      ]
    },
    "xllCustomFunctions": {
      "type": "object",
      "description": "Specifies the XLL-based add-ins custom function",
      "properties": {
        "fileNames": {
          "type": "array",
          "description": "Specifies the file names of the XLL-based add-ins custom function",
          "minItems": 1,
          "maxItems": 5,
          "items": {
            "type": "string",
            "minLength": 1,
            "maxLength": 64
          }
        }
      },
      "additionalProperties": false,
      "required": [
        "fileNames"
      ]
    }
  },
  "additionalProperties": false,
  "anyOf": [
    {
      "required": [
        "effect",
        "comAddin"
      ]
    },
    {
      "required": [
        "effect",
        "automationAddin"
      ]
    },
    {
      "required": [
        "effect",
        "xllCustomFunctions"
      ]
    }
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "effect": "userOptionToDisable | disableWithNotification",
  "comAddin": {
    "progIds": [
      "{string}"
    ]
  },
  "automationAddin": {
    "progIds": [
      "{string}"
    ]
  },
  "xllCustomFunctions": {
    "fileNames": [
      "{string}"
    ]
  }
}
```

```json
{
  "type": "object",
  "description": "Configures how to hide windows native extensions",
  "properties": {
    "effect": {
      "type": "string",
      "description": "Specifies the effect to take while installing the web add-in if the equivalent add-in is installed.",
      "enum": [
        "userOptionToDisable",
        "disableWithNotification"
      ]
    },
    "comAddin": {
      "type": "object",
      "description": "Specifies the equivalent COM add-ins",
      "properties": {
        "progIds": {
          "type": "array",
          "description": "Specifies the program Ids of the equivalent COM add-ins",
          "minItems": 1,
          "maxItems": 5,
          "items": {
            "type": "string",
            "minLength": 1,
            "maxLength": 64
          }
        }
      },
      "additionalProperties": false,
      "required": [
        "progIds"
      ]
    },
    "automationAddin": {
      "type": "object",
      "description": "Specifies the equivalent automation add-ins",
      "properties": {
        "progIds": {
          "type": "array",
          "description": "Specifies the program Ids of the equivalent automation add-ins",
          "minItems": 1,
          "maxItems": 5,
          "items": {
            "type": "string",
            "minLength": 1,
            "maxLength": 64
          }
        }
      },
      "additionalProperties": false,
      "required": [
        "progIds"
      ]
    },
    "xllCustomFunctions": {
      "type": "object",
      "description": "Specifies the XLL-based add-ins custom function",
      "properties": {
        "fileNames": {
          "type": "array",
          "description": "Specifies the file names of the XLL-based add-ins custom function",
          "minItems": 1,
          "maxItems": 5,
          "items": {
            "type": "string",
            "minLength": 1,
            "maxLength": 64
          }
        }
      },
      "additionalProperties": false,
      "required": [
        "fileNames"
      ]
    }
  },
  "additionalProperties": false,
  "anyOf": [
    {
      "required": [
        "effect",
        "comAddin"
      ]
    },
    {
      "required": [
        "effect",
        "automationAddin"
      ]
    },
    {
      "required": [
        "effect",
        "xllCustomFunctions"
      ]
    }
  ]
}
```

## Properties

#### effect

Specifies the effect to take while installing the web add-in if the equivalent add-in is installed.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `userOptionToDisable`, `disableWithNotification`.

#### comAddin

Specifies the equivalent COM or VSTO add-ins

**Type**  
[comAddin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions-com-addin?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### automationAddin

Specifies the equivalent automation add-ins

**Type**  
[automationAddin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions-automation-addin?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### xllCustomFunctions

Specifies the XLL-based add-ins custom function

**Type**  
[xllCustomFunctions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions-xll-custom-functions?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
