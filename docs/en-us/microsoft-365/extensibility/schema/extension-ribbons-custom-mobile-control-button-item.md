<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-mobile-control-button-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsCustomMobileControlButtonItem object

Defines the controls in the group. Only mobile buttons are supported.

Properties that reference this object type:

- [root.extensions.ribbons.tabs.customMobileRibbonGroups.controls](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-mobile-group-item?view=m365-app-1.30#controls-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "type": "mobileButton",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}",
      "scale": {number}
    }
  ],
  "actionId": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Specify the Id of the button like msgReadFunctionButton.",
      "maxLength": 250
    },
    "type": {
      "type": "string",
      "enum": [
        "mobileButton"
      ]
    },
    "label": {
      "type": "string",
      "description": "Short label of the control. Maximum length is 32 characters.",
      "maxLength": 32
    },
    "icons": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCustomMobileIcon"
      },
      "minItems": 9,
      "maxItems": 9
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an action defined in runtimes. Maximum length is 64 characters.",
      "maxLength": 64
    }
  },
  "required": [
    "id",
    "type",
    "label",
    "icons",
    "actionId"
  ]
}
```

## Properties

#### id

Specifies the ID of the control such as `msgReadFunctionButton`.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### type

Specifies the type of control.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `mobileButton`.

#### label

Specifies the label on the control.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### label

Specifies the label on the control.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### icons

Specifies the icons that will appear on the control depending on the dimensions and DPI of the mobile device screen. There must be exactly 9 icons.

**Type**  
Array of [extensionCustomMobileIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-mobile-icon?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 9. Maximum array items: 9.

**Supported values**  


#### actionId

Specifies the ID of the action that is taken when a user selects the control. The `actionId` must match the `runtime.actions.id` property of an action in the `runtimes` object.

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
 "extensions": [
    {
      "ribbons": [
        {
          "tabs": [
            {
              "customMobileRibbonGroups" [
                {
                  "controls": [
                    {
                      "id": "msgReadFunctionButton",
                      "type": "mobileButton",
                      "label": "Action 1",
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
                      ],
                      "supertip": {
                        "title": "Action 1 Title",
                        "description": "Action 1 Description"
                      },
                      "actionId": "action1"
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```
