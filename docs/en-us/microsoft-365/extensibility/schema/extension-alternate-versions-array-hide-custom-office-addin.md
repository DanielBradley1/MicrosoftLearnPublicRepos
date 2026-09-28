<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-custom-office-addin?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray.hide.customOfficeAddin object

Configures how to hide an in-market add-in that isn't distributed through AppSource.

Properties that reference this object type:

- [root.extensions.alternates.hide.customOfficeAddin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide?view=m365-app-1.30#customOfficeAddin-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "officeAddinId": "{string}"
}
```

```json
{
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
```

## Properties

#### officeAddinId

Specifies the ID of the in-market add-in to hide. The GUID is taken from the app manifest `id` property if the in-market add-in uses the JSON app manifest. The GUID is taken from the `<Id>` element if the in-market add-in uses the XML app manifest.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


## Examples

```json
{
  "storeOfficeAddin": {
    "officeAddinId": "00000000-0000-0000-0000-000000000000"
  }
}
```
