<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-prefer?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray.prefer object

Specifies an equivalent COM add-in or VSTO add-in that must be used in place of the Microsoft 365 Web Add-in for Windows.

Properties that reference this object type:

- [root.extensions.alternates.prefer](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array?view=m365-app-1.30#prefer-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "comAddin": {
    "progId": "{string}"
  },
  "xllCustomFunctions": {
    "fileName": "{string}"
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "comAddin": {
      "type": "object",
      "properties": {
        "progId": {
          "type": "string",
          "description": "Program ID of the alternate com extension. Maximum length is 64 characters.",
          "maxLength": 64
        }
      },
      "additionalProperties": false,
      "required": [
        "progId"
      ]
    },
    "xllCustomFunctions": {
      "$ref": "#/definitions/extensionXllCustomFunctions"
    }
  },
  "minProperties": 1
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "comAddin": {
    "progId": "{string}"
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "comAddin": {
      "type": "object",
      "properties": {
        "progId": {
          "type": "string",
          "description": "Program ID of the alternate com extension. Maximum length is 64 characters.",
          "maxLength": 64
        }
      },
      "additionalProperties": false,
      "required": [
        "progId"
      ]
    }
  },
  "minProperties": 1
}
```

## Properties

#### comAddin

Specifies a COM or VSTO add-in that must be used in place of the Microsoft 365 Web Add-in for Windows.

**Type**  
[comAddin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-prefer-com-addin?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### xllCustomFunctions

**Type**  
[extensionXllCustomFunctions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-xll-custom-functions?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Remarks

The `comAddin` property has the string "com" for historical reasons. It refers to both COM and VSTO add-ins. Similarly, the term "progId" is usually associated with only COM add-ins, but its value can be the name of a VSTO add-in.

## Examples

```json
{
 "extensions": [
    {
      "alternates": [
        {
          "prefer": {
            "comAddin": {
              "progId": "ContosoExtension"
            }
          }
        }
      ]
    }
  ]
}
```

## See also

- [Make your Office Add-in compatible with an existing COM or VSTO add-in](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in)
