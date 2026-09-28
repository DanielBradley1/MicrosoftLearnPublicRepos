<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsCustomTabGroupsItem object

Defines groups of controls on a ribbon tab on a non-mobile device. For mobile devices, see `tabs.customMobileRibbonGroups`.

Properties that reference this object type:

- [root.extensions.ribbons.tabs.groups](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30#groups-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "visible": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ],
      "keytip": "{string}"
    }
  ],
  "builtInGroupId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "visible": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this group within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "minItems": 3,
      "maxItems": 8,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem"
      },
      "minItems": 1,
      "maxItems": 20
    },
    "builtInGroupId": {
      "type": "string",
      "description": "Id of a built-in Group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "visible": {
      "type": "boolean",
      "description": "Controls whether the control is visible.",
      "default": true
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ],
      "visible": {boolean},
      "keytip": "{string}"
    }
  ],
  "builtInGroupId": "{string}",
  "overriddenByRibbonApi": {boolean},
  "visible": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this group within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "minItems": 3,
      "maxItems": 8,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem"
      },
      "minItems": 1,
      "maxItems": 20
    },
    "builtInGroupId": {
      "type": "string",
      "description": "Id of a built-in Group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    },
    "visible": {
      "type": "boolean",
      "description": "Controls whether the control is visible.",
      "default": true
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ],
      "keytip": "{string}"
    }
  ],
  "builtInGroupId": "{string}",
  "overriddenByRibbonApi": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this group within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "minItems": 3,
      "maxItems": 8,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem"
      },
      "minItems": 1,
      "maxItems": 20
    },
    "builtInGroupId": {
      "type": "string",
      "description": "Id of a built-in Group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "id": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ],
      "keytip": "{string}"
    }
  ],
  "builtInGroupId": "{string}",
  "overriddenByRibbonApi": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this group within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem"
      },
      "minItems": 1,
      "maxItems": 20
    },
    "builtInGroupId": {
      "type": "string",
      "description": "Id of a built-in Group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "id": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ]
    }
  ],
  "builtInGroupId": "{string}",
  "overriddenByRibbonApi": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this group within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem"
      },
      "minItems": 1,
      "maxItems": 20
    },
    "builtInGroupId": {
      "type": "string",
      "description": "Id of a built-in Group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "overriddenByRibbonApi": {
      "type": "boolean",
      "description": "Specifies whether a group will be hidden on application and platform combinations that support the API (Office.ribbon.requestCreateControls) that installs custom contextual tabs on the ribbon. Default is false.",
      "default": "false"
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_6_syntax)
- [Schema](#tabpanel_6_schema)

```json
{
  "id": "{string}",
  "label": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "controls": [
    {
      "id": "{string}",
      "type": "button | menu",
      "builtInControlId": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "supertip": {
        extensionCommonSuperToolTip object
      },
      "actionId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "enabled": {boolean},
      "items": [
        {
          extensionCommonCustomControlMenuItem object
        }
      ]
    }
  ],
  "builtInGroupId": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this group within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the group. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "icons": {
      "type": "array",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "$ref": "#/definitions/extensionCommonIcon"
      }
    },
    "controls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionCommonCustomGroupControlsItem"
      },
      "minItems": 1,
      "maxItems": 20
    },
    "builtInGroupId": {
      "type": "string",
      "description": "Id of a built-in Group. Maximum length is 64 characters.",
      "maxLength": 64
    }
  },
  "additionalProperties": false
}
```

## Properties

#### id

Specifies the ID for the tab group within the app. It must be different from any built-in group ID in the Microsoft 365 application and any other custom group.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### label

Specifies the text displayed for the group. Despite the maximum length of 64 characters, to correctly align the tab in the ribbon, we recommend you limit the label to 16 characters.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### icons

Specifies the icons displayed for the group.

**Type**  
Array of [extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 3. Maximum array items: 8.

**Supported values**  


#### icons

Specifies the icons displayed for the group.

**Type**  
Array of [extensionCommonIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-icon?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 3.

**Supported values**  


#### controls

Configures the buttons and menus in the group.

**Type**  
Array of [extensionCommonCustomGroupControlsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 20.

**Supported values**  


#### builtInGroupId

Specifies the ID of a built-in group. For more information, see [Find the IDs of controls and control groups](https://learn.microsoft.com/en-us/office/dev/add-ins/design/built-in-button-integration#find-the-ids-of-controls-and-control-groups).

Important

- This property can't be combined with any other child properties of the group object because built-in groups aren't customizable by an add-in.
- This property isn't supported in Outlook add-ins. In Outlook, you can put a custom group on a build-in tab, but you can't put a built-in group on any tab.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### overriddenByRibbonApi

Specifies whether a group is hidden on application and platform combinations that support the API \([Office.ribbon.requestCreateControls](https://learn.microsoft.com/en-us/javascript/api/office/office.ribbon#office-office-ribbon-requestcreatecontrols-member\(1\))\). This API installs custom contextual tabs on the ribbon. Default is false.

The purpose of this property is to create a fallback experience in an add-in that implements custom contextual tabs when the add-in is running on an application or platform that doesn't support custom contextual tabs. The essential strategy is that you duplicate some or all of the groups and controls from your custom contextual tab onto a custom core tab \(that is, noncontextual custom tab\). Then, to ensure that these groups and controls appear when custom contextual tabs aren't supported, but don't appear when custom contextual tabs are supported, you set `overriddenByRibbonApi` to `true` for a parent `groups`, `controls`, or menu `items` properties. The effect of doing so is the following:

- If the add-in runs on an application and platform that support custom contextual tabs, then the duplicated groups and controls won't appear on the ribbon. Instead, the custom contextual tab will be installed when the add-in calls the `requestCreateControls` method.
- If the add-in runs on an application or platform that doesn't support custom contextual tabs, then the duplicated groups and controls will appear on the ribbon.

Note

For a full understanding of this property, see [Implement an alternate UI experience when custom contextual tabs aren't supported](https://learn.microsoft.com/en-us/office/dev/add-ins/design/contextual-tabs#implement-an-alternate-ui-experience-when-custom-contextual-tabs-are-not-supported).

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `false`.

#### visible

Controls whether the control is visible.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `True`.

## Examples

```json
{
 "extensions": [
    {
      "ribbons": [
        {
          "tabs": [
            {
              "groups": [
                {
                  "id": "dashboard",
                  "label": "Controls",
                  "controls": [
                    {
                      "id": "control1",
                      "type": "button",
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
