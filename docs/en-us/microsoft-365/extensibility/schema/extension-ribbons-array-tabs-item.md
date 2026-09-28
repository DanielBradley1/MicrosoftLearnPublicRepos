<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# extensionRibbonsArrayTabsItem object

Configures a custom tab, or customized built-in tab, on the Office application ribbon. You can include custom and built-in control groups on the tab.

Properties that reference this object type:

- [root.extensions.ribbons.tabs](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array?view=m365-app-1.30#tabs-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "label": "{string}",
  "position": {
    "builtInTabId": "{string}",
    "align": "after | before"
  },
  "builtInTabId": "{string}",
  "groups": [
    {
      "id": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "controls": [
        {
          extensionCommonCustomGroupControlsItem object
        }
      ],
      "builtInGroupId": "{string}",
      "overriddenByRibbonApi": {boolean},
      "visible": {boolean}
    }
  ],
  "customMobileRibbonGroups": [
    {
      "id": "{string}",
      "label": "{string}",
      "controls": [
        {
          extensionRibbonsCustomMobileControlButtonItem object
        }
      ]
    }
  ],
  "visible": {boolean},
  "keytip": "{string}"
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this tab within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "position": {
      "type": "object",
      "properties": {
        "builtInTabId": {
          "type": "string",
          "description": "The id of the built-in tab. Maximum length is 64 characters.",
          "maxLength": 64
        },
        "align": {
          "type": "string",
          "description": "Define alignment of this custom tab relative to the specified built-in tab.",
          "enum": [
            "after",
            "before"
          ]
        }
      },
      "additionalProperties": false,
      "required": [
        "builtInTabId",
        "align"
      ]
    },
    "builtInTabId": {
      "type": "string",
      "description": "Id of the existing office Tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "groups": {
      "type": "array",
      "minItems": 1,
      "maxItems": 10,
      "description": "Defines tab groups.",
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomTabGroupsItem"
      }
    },
    "customMobileRibbonGroups": {
      "type": "array",
      "minItems": 1,
      "maxItems": 10,
      "description": "Defines mobile group item.",
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomMobileGroupItem"
      }
    },
    "visible": {
      "type": "boolean",
      "description": "Controls whether the control is visible.",
      "default": true
    },
    "keytip": {
      "type": "string",
      "description": "KeyTip shortcut for keyboard navigation (1-3 uppercase alphanumeric characters)",
      "minLength": 1,
      "maxLength": 3,
      "pattern": "^[A-Z0-9]\u002B$"
    }
  },
  "dependencies": {
    "builtInTabId": {
      "properties": {
        "groups": {
          "type": "array",
          "maxItems": 10,
          "items": {
            "$ref": "#/definitions/extensionCommonCustomGroup"
          }
        }
      },
      "required": [
        "builtInTabId"
      ]
    },
    "id": {
      "anyOf": [
        {
          "required": [
            "id",
            "label",
            "groups"
          ]
        },
        {
          "required": [
            "id",
            "label",
            "customMobileRibbonGroups"
          ]
        }
      ]
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
  "position": {
    "builtInTabId": "{string}",
    "align": "after | before"
  },
  "builtInTabId": "{string}",
  "groups": [
    {
      "id": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "controls": [
        {
          extensionCommonCustomGroupControlsItem object
        }
      ],
      "builtInGroupId": "{string}",
      "overriddenByRibbonApi": {boolean}
    }
  ],
  "customMobileRibbonGroups": [
    {
      "id": "{string}",
      "label": "{string}",
      "controls": [
        {
          extensionRibbonsCustomMobileControlButtonItem object
        }
      ]
    }
  ],
  "keytip": "{string}"
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this tab within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "position": {
      "type": "object",
      "properties": {
        "builtInTabId": {
          "type": "string",
          "description": "The id of the built-in tab. Maximum length is 64 characters.",
          "maxLength": 64
        },
        "align": {
          "type": "string",
          "description": "Define alignment of this custom tab relative to the specified built-in tab.",
          "enum": [
            "after",
            "before"
          ]
        }
      },
      "additionalProperties": false,
      "required": [
        "builtInTabId",
        "align"
      ]
    },
    "builtInTabId": {
      "type": "string",
      "description": "Id of the existing office Tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "groups": {
      "type": "array",
      "minItems": 1,
      "maxItems": 10,
      "description": "Defines tab groups.",
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomTabGroupsItem"
      }
    },
    "customMobileRibbonGroups": {
      "type": "array",
      "minItems": 1,
      "maxItems": 10,
      "description": "Defines mobile group item.",
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomMobileGroupItem"
      }
    },
    "keytip": {
      "type": "string",
      "description": "KeyTip shortcut for keyboard navigation (1-3 uppercase alphanumeric characters)",
      "minLength": 1,
      "maxLength": 3,
      "pattern": "^[A-Z0-9]\u002B$"
    }
  },
  "dependencies": {
    "builtInTabId": {
      "properties": {
        "groups": {
          "type": "array",
          "maxItems": 10,
          "items": {
            "$ref": "#/definitions/extensionCommonCustomGroup"
          }
        }
      },
      "required": [
        "builtInTabId"
      ]
    },
    "id": {
      "anyOf": [
        {
          "required": [
            "id",
            "label",
            "groups"
          ]
        },
        {
          "required": [
            "id",
            "label",
            "customMobileRibbonGroups"
          ]
        }
      ]
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
  "position": {
    "builtInTabId": "{string}",
    "align": "after | before"
  },
  "builtInTabId": "{string}",
  "groups": [
    {
      "id": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "controls": [
        {
          extensionCommonCustomGroupControlsItem object
        }
      ],
      "builtInGroupId": "{string}",
      "overriddenByRibbonApi": {boolean}
    }
  ],
  "customMobileRibbonGroups": [
    {
      "id": "{string}",
      "label": "{string}",
      "controls": [
        {
          extensionRibbonsCustomMobileControlButtonItem object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this tab within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "position": {
      "type": "object",
      "properties": {
        "builtInTabId": {
          "type": "string",
          "description": "The id of the built-in tab. Maximum length is 64 characters.",
          "maxLength": 64
        },
        "align": {
          "type": "string",
          "description": "Define alignment of this custom tab relative to the specified built-in tab.",
          "enum": [
            "after",
            "before"
          ]
        }
      },
      "additionalProperties": false,
      "required": [
        "builtInTabId",
        "align"
      ]
    },
    "builtInTabId": {
      "type": "string",
      "description": "Id of the existing office Tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "groups": {
      "type": "array",
      "minItems": 1,
      "maxItems": 10,
      "description": "Defines tab groups.",
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomTabGroupsItem"
      }
    },
    "customMobileRibbonGroups": {
      "type": "array",
      "minItems": 1,
      "maxItems": 10,
      "description": "Defines mobile group item.",
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomMobileGroupItem"
      }
    }
  },
  "dependencies": {
    "builtInTabId": {
      "properties": {
        "groups": {
          "type": "array",
          "maxItems": 10,
          "items": {
            "$ref": "#/definitions/extensionCommonCustomGroup"
          }
        }
      },
      "required": [
        "builtInTabId"
      ]
    },
    "id": {
      "anyOf": [
        {
          "required": [
            "id",
            "label",
            "groups"
          ]
        },
        {
          "required": [
            "id",
            "label",
            "customMobileRibbonGroups"
          ]
        }
      ]
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
  "position": {
    "builtInTabId": "{string}",
    "align": "after | before"
  },
  "builtInTabId": "{string}",
  "groups": [
    {
      "id": "{string}",
      "label": "{string}",
      "icons": [
        {
          extensionCommonIcon object
        }
      ],
      "controls": [
        {
          extensionCommonCustomGroupControlsItem object
        }
      ],
      "builtInGroupId": "{string}"
    }
  ],
  "customMobileRibbonGroups": [
    {
      "id": "{string}",
      "label": "{string}",
      "controls": [
        {
          extensionRibbonsCustomMobileControlButtonItem object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for this tab within the app. Maximum length is 64 characters. ",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "Displayed text for the tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "position": {
      "type": "object",
      "properties": {
        "builtInTabId": {
          "type": "string",
          "description": "The id of the built-in tab. Maximum length is 64 characters.",
          "maxLength": 64
        },
        "align": {
          "type": "string",
          "description": "Define alignment of this custom tab relative to the specified built-in tab.",
          "enum": [
            "after",
            "before"
          ]
        }
      },
      "additionalProperties": false,
      "required": [
        "builtInTabId",
        "align"
      ]
    },
    "builtInTabId": {
      "type": "string",
      "description": "Id of the existing office Tab. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "groups": {
      "type": "array",
      "minItems": 1,
      "maxItems": 10,
      "description": "Defines tab groups.",
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomTabGroupsItem"
      }
    },
    "customMobileRibbonGroups": {
      "type": "array",
      "minItems": 1,
      "maxItems": 10,
      "description": "Defines mobile group item.",
      "items": {
        "$ref": "#/definitions/extensionRibbonsCustomMobileGroupItem"
      }
    }
  },
  "dependencies": {
    "builtInTabId": {
      "properties": {
        "groups": {
          "type": "array",
          "maxItems": 10,
          "items": {
            "$ref": "#/definitions/extensionCommonCustomGroup"
          }
        }
      },
      "required": [
        "builtInTabId"
      ]
    },
    "id": {
      "required": [
        "id",
        "label",
        "groups"
      ]
    }
  },
  "additionalProperties": false
}
```

## Properties

#### id

Specifies the ID for a custom tab.

Important

- If the `id` property is present, the `tabs.label` and either the `tabs.groups` or `tabs.customMobileRibbonGroups` property must also be present.
- The `tabs.id` and `tabs.builtInTabId` are mutually exclusive. Don't use them both in the same tab object.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### label

Specifies the text displayed for a custom tab. Despite the maximum length of 64 characters, to correctly align the tab in the ribbon, we recommend you limit the label to 16 characters.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### position

Configures the position of the custom tab relative to other tabs on the ribbon.

**Type**  
[position](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item-position?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### builtInTabId

Specifies the ID of a built-in Office ribbon tab. For more information on possible values, see [Find the IDs of built-in Office ribbon tabs](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/built-in-ui-ids).

Important

The only other child properties of the tab object that can be combined with this one are `groups` and `customMobileRibbonGroups`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### groups

Defines groups of controls on a ribbon tab on a non-mobile device. For mobile devices, see `tabs.customMobileRibbonGroups`.

**Type**  
Array of [extensionRibbonsCustomTabGroupsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-tab-groups-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 10.

**Supported values**  


#### customMobileRibbonGroups

Defines groups of controls on the default tab of the ribbon on a mobile device. This array property can only be present on tab objects that have a `tabs.builtInTabId` property that is set to `DefaultTab`. For non-mobile devices, see `tabs.groups` above.

**Type**  
Array of [extensionRibbonsCustomMobileGroupItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-custom-mobile-group-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 10.

**Supported values**  


#### visible

Controls whether the control is visible.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `True`.

#### keytip

KeyTip shortcut for keyboard navigation \(1-3 uppercase alphanumeric characters\). To learn how to create custom KeyTips for your Office Add-in, see [Add custom KeyTips to your Office Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/design/add-custom-key-tips).

Note

This property isn't supported in Outlook add-ins.

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 3.

**Supported values**  
The string must match the following regular expression: `^[A-Z0-9]+$`.

## Remarks

There isn't as much support for custom tabs and customized built-in tabs in Outlook add-ins as there is in other Office applications. Custom tabs are supported in classic Outlook on Windows, but not in Outlook on the web, on Mac, and in the new Outlook on Windows; but you can put custom groups of controls on one of the built-in Office tabs instead. You can't put built-in groups on built-in tabs in Outlook on any platform.

## Examples

```json
{
 "extensions": [
    {
      "ribbons": [
        {
          "tabs": [
            {
              "builtInTabId": "TabDefault",
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
              ],
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
              "customMobileRibbonGroups": [
                {
                  "id": "mobileDashboard",
                  "label": "Controls",
                  "controls": [
                    {
                      "id": "control1",
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
