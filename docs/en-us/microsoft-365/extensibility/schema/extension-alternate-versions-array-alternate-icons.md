<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray.alternateIcons object

For future use. We are working on a system that will make Office Add-ins that use the unified manifest for Microsoft 365 installable on older or non-subscription Office versions or platforms that do not directly support the unified manifest. That system will use this object to specify the icons that represent the add-in Office Add-in in the add-in insertion UX and the vertical task pane tab bar. For more information, see [Office Add-ins with the unified app manifest for Microsoft 365 - Client and platform support](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/unified-manifest-overview#client-and-platform-support).

Properties that reference this object type:

- [root.extensions.alternates.alternateIcons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array?view=m365-app-1.30#alternateIcons-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "icon": {
    "size": {number},
    "url": "{string}"
  },
  "highResolutionIcon": {
    "size": {number},
    "url": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "icon": {
      "$ref": "#/definitions/extensionCommonIcon"
    },
    "highResolutionIcon": {
      "$ref": "#/definitions/extensionCommonIcon"
    }
  },
  "required": [
    "icon",
    "highResolutionIcon"
  ]
}
```

## Properties

#### icon

Specifies properties of the image file used to represent the add-in in the add-in acquisition UI in an Office application, and in the vertical task pane tab bar, for certain old or non-subscription versions of Office.

The file should be a version of the same image used for the [icons.color](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color) property. But it must be 64 x 64 pixels if `mail` is in the `extensions.requirements.scopes` array \(or there is no `extensions.requirements.scopes` property in the manifest\), otherwise it must be 32 x 32 pixels. The file must have one of the following file formats: GIF, JPG, PNG, EXIF, BMP, TIFF.

Important

The descendant `icon.size` property is ignored, but it must be present and have a valid size value. When the manifest is validated, the file specified at `icon.url` is opened and measured.

For more information, see [Create a consistent visual identity](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/create-effective-office-store-listings#create-a-consistent-visual-identity).

**Type**  
[extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### highResolutionIcon

Specifies properties of the image file used to represent the add-in on high DPI screens in the add-in acquisition UI in an Office application, and in the vertical task pane tab bar, for certain old or non-subscription versions of Office.

The file should be a version of the same image used for the [icons.color](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30#color) property. But it must be 128 x 128 pixels if `mail` is in the `extensions.requirements.scopes` array \(or there is no `extensions.requirements.scopes` property in the manifest\), otherwise it must be 64 x 64 pixels. The file must have one of the following file formats: GIF, JPG, PNG, EXIF, BMP, TIFF.

Important

The descendant `highResolutionIcon.size` property is ignored, but it must be present and have a valid size value. When the manifest is validated, the file specified at `highResolutionIcon.url` is opened and measured.

For more information, see [Create a consistent visual identity](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/create-effective-office-store-listings#create-a-consistent-visual-identity).

**Type**  
[extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


## Examples

Note

The `size` properties are ignored, but they must be present and have valid values. When the manifest is validated, the files are opened and measured.

```json
{
    "alternateIcons": {
      "icon": {
        "size": 64,
        "url": "https://contoso.com/assets/icon64x64.jpg"
      },
      "highResolutionIcon": {
        "size": 64,
        "url": "https://contoso.com/assets/icon128x128.jpg"
      }
    }
}
```
