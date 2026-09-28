<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionCommonIcon object

Specifies properties of the image file used to represent the add-in.

Properties that reference this object type:

- [root.extensions.alternates.alternateIcons.highResolutionIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30#highResolutionIcon-property)
- [root.extensions.alternates.alternateIcons.icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30#icon-property)
- [root.extensions.contextMenus.menus.controls.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#icons-property)
- [root.extensions.contextMenus.menus.controls.items.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.fixedControls.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.tabs.groups.controls.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.tabs.groups.controls.items.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.tabs.groups.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#icons-property)

Properties that reference this object type:

- [root.extensions.alternates.alternateIcons.highResolutionIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30#highResolutionIcon-property)
- [root.extensions.alternates.alternateIcons.icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30#icon-property)
- [root.extensions.ribbons.fixedControls.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.tabs.groups.controls.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.tabs.groups.controls.items.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.tabs.groups.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#icons-property)

Properties that reference this object type:

- [root.extensions.alternates.alternateIcons.highResolutionIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30#highResolutionIcon-property)
- [root.extensions.alternates.alternateIcons.icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-alternate-icons?view=m365-app-1.30#icon-property)
- [root.extensions.ribbons.tabs.groups.controls.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.tabs.groups.controls.items.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#icons-property)
- [root.extensions.ribbons.tabs.groups.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30#icons-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "size": {number},
  "url": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "size": {
      "type": "number",
      "description": "Size in pixels of the icon. Three image sizes are required (16, 32, and 80 pixels)",
      "enum": [
        16,
        20,
        24,
        32,
        40,
        48,
        64,
        80
      ]
    },
    "url": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "Absolute Url to the icon."
    }
  },
  "additionalProperties": false,
  "required": [
    "size",
    "url"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "size": {number},
  "url": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "size": {
      "type": "number",
      "description": "Size in pixels of the icon. Three image sizes are required (16, 32, and 80 pixels)",
      "enum": [
        16,
        20,
        24,
        32,
        40,
        48,
        64,
        80
      ]
    },
    "url": {
      "$ref": "#/definitions/httpsUrl",
      "description": "Absolute Url to the icon."
    }
  },
  "additionalProperties": false,
  "required": [
    "size",
    "url"
  ]
}
```

## Properties

#### size

Specifies the size of the icon in pixels, enumerated as `16`,`20`,`24`,`32`,`40`,`48`,`64`,`80`.

**Type**  
number

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: 16, 20, 24, 32, 40, 48, 64, 80.

#### url

Specifies the full, absolute URL of the image file that is used to represent the add-in.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

## Remarks

The ICO file format isn't supported. Using it in your manifest will fail manifest validation and prevent your Office Add-in from appearing in the ribbon or action bar.

When specifying the `extensions.alternates.alternateIcons.highResolutionIcon` or `extensions.alternates.alternateIcons.icon` properties, the `extensionCommonIcon` type works differently from how it works in other contexts, as noted in the following points:

- The icon file must be one of the following file formats: GIF, JPG, PNG, EXIF, BMP, TIFF.
- The `size` property is ignored, but it must be present and have a valid size value. When the manifest is validated, the size of the file in the `url` property is measured.
- For the `alternateIcons.icon` property, the file that `icon.url` points to must be 64 x 64 pixels if `mail` is in the `extensions.requirements.scopes` array \(or there is no `extensions.requirements.scopes` property in the manifest\). Otherwise, it must be 32 x 32 pixels.
- For the `alternateIcons.highResolutionIcon` property, the file that `highResolutionIcon.url` points to must be 128 x 128 pixels if `mail` is in the `extensions.requirements.scopes` array \(or there is no `extensions.requirements.scopes` property in the manifest\). Otherwise, it must be 64 x 64 pixels.

## Examples

```json
{
  "icons": [
    {
      "size": 16,
      "url": "test_16.png"
    },
    {
      "size": 32,
      "url": "test_32.png"
    },
    {
      "size": 80,
      "url": "test_80.png"
    }
  ]
}
```

In the following example, the `size` properties are ignored, but they must be present and have valid values. When the manifest is validated, the files are opened and measured.

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
