<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-mobile-group-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsCustomMobileGroupItem object

Defines groups of controls on the default tab of the ribbon on a mobile device. This array property can only be present on tab objects that have a `tabs.builtInTabId` property that is set to `DefaultTab`. For non-mobile devices, see `tabs.groups`.

Properties that reference this object type:

- [root.extensions.ribbons.tabs.customMobileRibbonGroups](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#customMobileRibbonGroups-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "label": "{string}",
  "controls": [
    {
      "id": "{string}",
      "type": "mobileButton",
      "label": "{string}",
      "icons": [
        {
          extensionCustomMobileIcon object
        }
      ],
      "actionId": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "Specify the Id of the group. Used for mobileMessageRead ext point.",
      "maxLength": 250
    },
    "label": {
      "type": "string",
      "description": "Short label of the control. Maximum length is 32 characters.",
      "maxLength": 32
    },
    "controls": {
      "type": "array",
      "minItems": 1,
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomMobileControlButtonItem"
      }
    }
  },
  "required": [
    "id",
    "label",
    "controls"
  ]
}
```

## Properties

#### id

Specifies the ID of the group. It must be different from any built-in group ID in the Microsoft 365 application and any other custom group.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 250.

**Supported values**  


#### label

Specifies the label on the group.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### controls

Defines the controls in the group. Only mobile buttons are supported.

**Type**  
Array of [extensionRibbonsCustomMobileControlButtonItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-mobile-control-button-item?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1. Maximum array items: 20.

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
                  "id": "myMobileGroup",
                  "label": "Contoso Actions",
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
