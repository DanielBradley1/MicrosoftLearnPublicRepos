<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray.hide object

Configures how to hide another add-in that you've published whenever the add-in is installed, so users don't see both in the Microsoft 365 UI. For example, use this property when you've previously published an add-in that uses the old XML app manifest and you're replacing it with a version that uses the new JSON app manifest.

Properties that reference this object type:

- [root.extensions.alternates.hide](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array?view=m365-app-1.30#hide-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "storeOfficeAddin": {
    "officeAddinId": "{string}",
    "assetId": "{string}"
  },
  "customOfficeAddin": {
    "officeAddinId": "{string}"
  },
  "windowsExtensions": {
    "effect": "userOptionToDisable | disableWithNotification",
    "comAddin": {
      comAddin object
    },
    "automationAddin": {
      automationAddin object
    },
    "xllCustomFunctions": {
      xllCustomFunctions object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "storeOfficeAddin": {
      "type": "object",
      "properties": {
        "officeAddinId": {
          "type": "string",
          "description": "Solution ID of an in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        },
        "assetId": {
          "type": "string",
          "description": "Asset ID of the in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        }
      },
      "additionalProperties": false,
      "required": [
        "officeAddinId",
        "assetId"
      ]
    },
    "customOfficeAddin": {
      "type": "object",
      "properties": {
        "officeAddinId": {
          "type": "string",
          "description": "Solution ID of the in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        }
      },
      "additionalProperties": false,
      "required": [
        "officeAddinId"
      ]
    },
    "windowsExtensions": {
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
  },
  "minProperties": 1
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "storeOfficeAddin": {
    "officeAddinId": "{string}",
    "assetId": "{string}"
  },
  "customOfficeAddin": {
    "officeAddinId": "{string}"
  },
  "windowsExtensions": {
    "effect": "userOptionToDisable | disableWithNotification",
    "comAddin": {
      comAddin object
    },
    "automationAddin": {
      automationAddin object
    },
    "xllCustomFunctions": {
      xllCustomFunctions object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "storeOfficeAddin": {
      "type": "object",
      "properties": {
        "officeAddinId": {
          "type": "string",
          "description": "Solution ID of an in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        },
        "assetId": {
          "type": "string",
          "description": "Asset ID of the in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        }
      },
      "additionalProperties": false,
      "required": [
        "officeAddinId",
        "assetId"
      ]
    },
    "customOfficeAddin": {
      "type": "object",
      "properties": {
        "officeAddinId": {
          "type": "string",
          "description": "Solution ID of the in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        }
      },
      "additionalProperties": false,
      "required": [
        "officeAddinId"
      ]
    },
    "windowsExtensions": {
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
  },
  "minProperties": 1
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "storeOfficeAddin": {
    "officeAddinId": "{string}",
    "assetId": "{string}"
  },
  "customOfficeAddin": {
    "officeAddinId": "{string}"
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "storeOfficeAddin": {
      "type": "object",
      "properties": {
        "officeAddinId": {
          "type": "string",
          "description": "Solution ID of an in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        },
        "assetId": {
          "type": "string",
          "description": "Asset ID of the in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        }
      },
      "additionalProperties": false,
      "required": [
        "officeAddinId",
        "assetId"
      ]
    },
    "customOfficeAddin": {
      "type": "object",
      "properties": {
        "officeAddinId": {
          "type": "string",
          "description": "Solution ID of the in-market add-in to hide. Maximum length is 64 characters.",
          "maxLength": 64
        }
      },
      "additionalProperties": false,
      "required": [
        "officeAddinId"
      ]
    }
  },
  "minProperties": 1
}
```

## Properties

#### storeOfficeAddin

Specifies a Microsoft 365 Add-in available in Microsoft AppSource.

**Type**  
[storeOfficeAddin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-store-office-addin?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### customOfficeAddin

Configures how to hide an in-market add-in that isn't distributed through AppSource.

**Type**  
[customOfficeAddin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-custom-office-addin?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### windowsExtensions

Configures how to hide windows native extensions

**Type**  
[windowsExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
  "hide": {
    "storeOfficeAddin": {
      "officeAddinId": "00000000-0000-0000-0000-000000000000",
      "assetId": "WA000000000"
    }
  }
}
```
