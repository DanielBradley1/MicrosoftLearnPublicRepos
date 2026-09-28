<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-prefer-com-addin?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray.prefer.comAddin object

Specifies a COM or VSTO add-in that must be used in place of the Microsoft 365 Web Add-in for Windows.

Properties that reference this object type:

- [root.extensions.alternates.prefer.comAddin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-prefer?view=m365-app-1.30#comAddin-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "progId": "{string}"
}
```

```json
{
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
```

## Properties

#### progId

Specifies the name of either a COM or VSTO add-in which is to be used in place of the web add-in when both are installed on a Windows computer.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


## Remarks

The term "progId" is usually associated with only COM add-ins, but in the manifest its value can be the name of a VSTO add-in.

## Examples

```json
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
```

## See also

- [Make your Office Add-in compatible with an existing COM or VSTO add-in](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/make-office-add-in-compatible-with-existing-com-add-in)
