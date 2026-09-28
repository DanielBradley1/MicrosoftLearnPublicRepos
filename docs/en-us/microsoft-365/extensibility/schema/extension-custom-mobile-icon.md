<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-mobile-icon?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionCustomMobileIcon object

Specifies the icons that will appear on the control depending on the dimensions and DPI of the mobile device screen. There must be exactly 9 icons.

Properties that reference this object type:

- [root.extensions.ribbons.tabs.customMobileRibbonGroups.controls.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-mobile-control-button-item?view=m365-app-1.30#icons-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "size": {number},
  "url": "{string}",
  "scale": {number}
}
```

```json
{
  "type": "object",
  "properties": {
    "size": {
      "type": "number",
      "description": "Size in pixels of the icon. Three image sizes are required (25, 32, and 48 pixels).",
      "enum": [
        25,
        32,
        48
      ]
    },
    "url": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "Url to the icon."
    },
    "scale": {
      "type": "number",
      "description": "How to scale - 1,2,3 for each image. This attribute specifies the UIScreen.scale property for iOS devices.",
      "enum": [
        1,
        2,
        3
      ]
    }
  },
  "additionalProperties": false,
  "required": [
    "size",
    "url",
    "scale"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "size": {number},
  "url": "{string}",
  "scale": {number}
}
```

```json
{
  "type": "object",
  "properties": {
    "size": {
      "type": "number",
      "description": "Size in pixels of the icon. Three image sizes are required (25, 32, and 48 pixels).",
      "enum": [
        25,
        32,
        48
      ]
    },
    "url": {
      "$ref": "#/definitions/httpsUrl",
      "description": "Url to the icon."
    },
    "scale": {
      "type": "number",
      "description": "How to scale - 1,2,3 for each image. This attribute specifies the UIScreen.scale property for iOS devices.",
      "enum": [
        1,
        2,
        3
      ]
    }
  },
  "additionalProperties": false,
  "required": [
    "size",
    "url",
    "scale"
  ]
}
```

## Properties

#### size

Size in pixels of the icon. The required sizes are 25, 32, and 48. There must be exactly one of each size for each possible value of the icons' `scale` property.

**Type**  
number

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: 25, 32, 48.

#### url

The full, absolute URL of the icon's image file.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### scale

Specifies the UIScreen.scale property for iOS devices. The possible values are 1, 2, and 3. There must be exactly one of each value for each possible value of the icons's `size` property.

**Type**  
number

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: 1, 2, 3.

## Examples

```json
{
    "customMobileRibbonGroups": [
      {
        "controls": [
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
        ]
      }
    ]
}
```
