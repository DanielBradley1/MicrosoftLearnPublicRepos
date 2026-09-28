<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsArray object

The `extensions.ribbons` property provides the ability to add [add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/design/add-in-commands) \(buttons and menu items\) to the Microsoft 365 application's ribbon. The ribbon definition is selected from the array based on the requirements and first-of order.

Properties that reference this object type:

- [root.extensions.ribbons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#ribbons-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "contexts": [
    "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default | spamReportingOverride"
  ],
  "tabs": [
    {
      "id": "{string}",
      "label": "{string}",
      "position": {
        position object
      },
      "builtInTabId": "{string}",
      "groups": [
        {
          extensionRibbonsCustomTabGroupsItem object
        }
      ],
      "customMobileRibbonGroups": [
        {
          extensionRibbonsCustomMobileGroupItem object
        }
      ],
      "visible": {boolean},
      "keytip": "{string}"
    }
  ],
  "fixedControls": [
    {
      "id": "{string}",
      "type": "button",
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
      "enabled": {boolean}
    }
  ],
  "spamPreProcessingDialog": {
    "title": "{string}",
    "description": "{string}",
    "spamNeverShowAgainOption": {boolean},
    "spamReportingOptions": {
      spamReportingOptions object
    },
    "spamFreeTextSectionTitle": "{string}",
    "spamMoreInfo": {
      spamMoreInfo object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "contexts": {
      "$ref": "#/definitions/extensionContexts"
    },
    "tabs": {
      "type": "array",
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayTabsItem"
      }
    },
    "fixedControls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayFixedControlItem"
      },
      "minItems": 1,
      "maxItems": 1
    },
    "spamPreProcessingDialog": {
      "$ref": "#/definitions/extensionRibbonsSpamPreProcessingDialog"
    }
  },
  "additionalProperties": false,
  "required": [
    "tabs"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "contexts": [
    "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | spamReportingOverride | default"
  ],
  "tabs": [
    {
      "id": "{string}",
      "label": "{string}",
      "position": {
        position object
      },
      "builtInTabId": "{string}",
      "groups": [
        {
          extensionRibbonsCustomTabGroupsItem object
        }
      ],
      "customMobileRibbonGroups": [
        {
          extensionRibbonsCustomMobileGroupItem object
        }
      ],
      "visible": {boolean},
      "keytip": "{string}"
    }
  ],
  "fixedControls": [
    {
      "id": "{string}",
      "type": "button",
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
      "enabled": {boolean}
    }
  ],
  "spamPreProcessingDialog": {
    "title": "{string}",
    "description": "{string}",
    "spamNeverShowAgainOption": {boolean},
    "spamReportingOptions": {
      spamReportingOptions object
    },
    "spamFreeTextSectionTitle": "{string}",
    "spamMoreInfo": {
      spamMoreInfo object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "contexts": {
      "$ref": "#/definitions/extensionContexts"
    },
    "tabs": {
      "type": "array",
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayTabsItem"
      }
    },
    "fixedControls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayFixedControlItem"
      },
      "minItems": 1,
      "maxItems": 1
    },
    "spamPreProcessingDialog": {
      "$ref": "#/definitions/extensionRibbonsSpamPreProcessingDialog"
    }
  },
  "additionalProperties": false,
  "required": [
    "tabs"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "contexts": [
    "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | spamReportingOverride | default"
  ],
  "tabs": [
    {
      "id": "{string}",
      "label": "{string}",
      "position": {
        position object
      },
      "builtInTabId": "{string}",
      "groups": [
        {
          extensionRibbonsCustomTabGroupsItem object
        }
      ],
      "customMobileRibbonGroups": [
        {
          extensionRibbonsCustomMobileGroupItem object
        }
      ],
      "keytip": "{string}"
    }
  ],
  "fixedControls": [
    {
      "id": "{string}",
      "type": "button",
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
      "enabled": {boolean}
    }
  ],
  "spamPreProcessingDialog": {
    "title": "{string}",
    "description": "{string}",
    "spamNeverShowAgainOption": {boolean},
    "spamReportingOptions": {
      spamReportingOptions object
    },
    "spamFreeTextSectionTitle": "{string}",
    "spamMoreInfo": {
      spamMoreInfo object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "contexts": {
      "$ref": "#/definitions/extensionContexts"
    },
    "tabs": {
      "type": "array",
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayTabsItem"
      }
    },
    "fixedControls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayFixedControlItem"
      },
      "minItems": 1,
      "maxItems": 1
    },
    "spamPreProcessingDialog": {
      "$ref": "#/definitions/extensionRibbonsSpamPreProcessingDialog"
    }
  },
  "additionalProperties": false,
  "required": [
    "tabs"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "contexts": [
    "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default | spamReportingOverride"
  ],
  "tabs": [
    {
      "id": "{string}",
      "label": "{string}",
      "position": {
        position object
      },
      "builtInTabId": "{string}",
      "groups": [
        {
          extensionRibbonsCustomTabGroupsItem object
        }
      ],
      "customMobileRibbonGroups": [
        {
          extensionRibbonsCustomMobileGroupItem object
        }
      ]
    }
  ],
  "fixedControls": [
    {
      "id": "{string}",
      "type": "button",
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
      "enabled": {boolean}
    }
  ],
  "spamPreProcessingDialog": {
    "title": "{string}",
    "description": "{string}",
    "spamNeverShowAgainOption": {boolean},
    "spamReportingOptions": {
      spamReportingOptions object
    },
    "spamFreeTextSectionTitle": "{string}",
    "spamMoreInfo": {
      spamMoreInfo object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "contexts": {
      "$ref": "#/definitions/extensionContexts"
    },
    "tabs": {
      "type": "array",
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayTabsItem"
      }
    },
    "fixedControls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayFixedControlItem"
      },
      "minItems": 1,
      "maxItems": 1
    },
    "spamPreProcessingDialog": {
      "$ref": "#/definitions/extensionRibbonsSpamPreProcessingDialog"
    }
  },
  "additionalProperties": false,
  "required": [
    "tabs"
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "contexts": [
    "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default | spamReportingOverride"
  ],
  "tabs": [
    {
      "id": "{string}",
      "label": "{string}",
      "position": {
        position object
      },
      "builtInTabId": "{string}",
      "groups": [
        {
          extensionRibbonsCustomTabGroupsItem object
        }
      ],
      "customMobileRibbonGroups": [
        {
          extensionRibbonsCustomMobileGroupItem object
        }
      ]
    }
  ],
  "fixedControls": [
    {
      "id": "{string}",
      "type": "button",
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
      "enabled": {boolean}
    }
  ],
  "spamPreProcessingDialog": {
    "title": "{string}",
    "description": "{string}",
    "spamReportingOptions": {
      spamReportingOptions object
    },
    "spamFreeTextSectionTitle": "{string}",
    "spamMoreInfo": {
      spamMoreInfo object
    }
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "contexts": {
      "$ref": "#/definitions/extensionContexts"
    },
    "tabs": {
      "type": "array",
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayTabsItem"
      }
    },
    "fixedControls": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayFixedControlItem"
      }
    },
    "spamPreProcessingDialog": {
      "$ref": "#/definitions/extensionRibbonsSpamPreProcessingDialog"
    }
  },
  "additionalProperties": false,
  "required": [
    "tabs"
  ]
}
```

- [Syntax](#tabpanel_6_syntax)
- [Schema](#tabpanel_6_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "contexts": [
    "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default"
  ],
  "tabs": [
    {
      "id": "{string}",
      "label": "{string}",
      "position": {
        position object
      },
      "builtInTabId": "{string}",
      "groups": [
        {
          extensionRibbonsCustomTabGroupsItem object
        }
      ],
      "customMobileRibbonGroups": [
        {
          extensionRibbonsCustomMobileGroupItem object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "contexts": {
      "$ref": "#/definitions/extensionContexts"
    },
    "tabs": {
      "type": "array",
      "maxItems": 20,
      "items": {
        "$ref": "#/definitions/extensionRibbonsArrayTabsItem"
      }
    }
  },
  "additionalProperties": false,
  "required": [
    "tabs"
  ]
}
```

## Properties

#### requirements

Specifies the scopes, formFactors, and Office JavaScript library requirement sets that must be supported on the Office client in order for the ribbon customization to appear. For more information, see [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest).

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### contexts

**Type**  
Array of string

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 7.

**Supported values**  
Allowed values: `mailRead`, `mailCompose`, `meetingDetailsOrganizer`, `meetingDetailsAttendee`, `onlineMeetingDetailsOrganizer`, `logEventMeetingDetailsAttendee`, `spamReportingOverride`, `default`.

#### contexts

Specifies the Microsoft 365 application window in which the ribbon customization is available to the user. Each item in the array is a member of a string array.

The following values are supported.

- `default`: Adds add-in commands to the ribbon. Applies to Excel, PowerPoint, and Word.
- `mailRead`: Adds add-in commands to the ribbon of a message in read mode. Applies to Outlook only.
- `mailCompose`: Adds add-in commands to the ribbon of a message in compose mode. Applies to Outlook only.
- `meetingDetailsOrganizer`: Adds add-in commands to the ribbon of an appointment being composed by a meeting organizer. Applies to Outlook only.
- `meetingDetailsAttendee`: Adds add-in commands to the ribbon of an appointment that's displayed to a meeting attendee. Applies to Outlook only.
- `onlineMeetingDetailsOrganizer`: Adds an online-meeting provider toggle to an appointment being composed by a meeting organizer in Outlook on mobile devices. For more information, see [Create an Outlook add-in for an online-meeting provider](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/online-meeting).
- `logEventMeetingDetailsAttendee`: Adds a **Log** button to an appointment that's displayed to a meeting attendee in Outlook on mobile devices. For more information, see [Log appointment notes to an external application in Outlook mobile add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/mobile-log-appointments).
- `spamReportingOverride`: Adds the button of a spam-reporting add-in to a prominent spot on the ribbon of the Outlook client. Prevents the add-in button from appearing at the end of the ribbon or in the overflow menu. For more information, see [Implement an integrated spam-reporting add-in](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

**Type**  
Array of string

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 7.

**Supported values**  
Allowed values: `mailRead`, `mailCompose`, `meetingDetailsOrganizer`, `meetingDetailsAttendee`, `onlineMeetingDetailsOrganizer`, `logEventMeetingDetailsAttendee`, `default`, `spamReportingOverride`.

#### contexts

Specifies the Microsoft 365 application window in which the ribbon customization is available to the user. Each item in the array is a member of a string array.

The following values are supported.

- `default`: Adds add-in commands to the ribbon. Applies to Excel, PowerPoint, and Word.
- `mailRead`: Adds add-in commands to the ribbon of a message in read mode. Applies to Outlook only.
- `mailCompose`: Adds add-in commands to the ribbon of a message in compose mode. Applies to Outlook only.
- `meetingDetailsOrganizer`: Adds add-in commands to the ribbon of an appointment being composed by a meeting organizer. Applies to Outlook only.
- `meetingDetailsAttendee`: Adds add-in commands to the ribbon of an appointment that's displayed to a meeting attendee. Applies to Outlook only.
- `onlineMeetingDetailsOrganizer`: Adds an online-meeting provider toggle to an appointment being composed by a meeting organizer in Outlook on mobile devices. For more information, see [Create an Outlook add-in for an online-meeting provider](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/online-meeting).
- `logEventMeetingDetailsAttendee`: Adds a **Log** button to an appointment that's displayed to a meeting attendee in Outlook on mobile devices. For more information, see [Log appointment notes to an external application in Outlook mobile add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/mobile-log-appointments).
- `spamReportingOverride`: Adds the button of a spam-reporting add-in to a prominent spot on the ribbon of the Outlook client. Prevents the add-in button from appearing at the end of the ribbon or in the overflow menu. For more information, see [Implement an integrated spam-reporting add-in](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting).

**Type**  
Array of string

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 8.

**Supported values**  
Allowed values: `mailRead`, `mailCompose`, `meetingDetailsOrganizer`, `meetingDetailsAttendee`, `onlineMeetingDetailsOrganizer`, `logEventMeetingDetailsAttendee`, `default`, `spamReportingOverride`.

#### contexts

Specifies the Microsoft 365 application window in which the ribbon customization is available to the user. Each item in the array is a member of a string array.

The following values are supported.

- `default`: Adds add-in commands to the ribbon. Applies to Excel, PowerPoint, and Word.
- `mailRead`: Adds add-in commands to the ribbon of a message in read mode. Applies to Outlook only.
- `mailCompose`: Adds add-in commands to the ribbon of a message in compose mode. Applies to Outlook only.
- `meetingDetailsOrganizer`: Adds add-in commands to the ribbon of an appointment being composed by a meeting organizer. Applies to Outlook only.
- `meetingDetailsAttendee`: Adds add-in commands to the ribbon of an appointment that's displayed to a meeting attendee. Applies to Outlook only.
- `onlineMeetingDetailsOrganizer`: Adds an online-meeting provider toggle to an appointment being composed by a meeting organizer in Outlook on mobile devices. For more information, see [Create an Outlook add-in for an online-meeting provider](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/online-meeting).
- `logEventMeetingDetailsAttendee`: Adds a **Log** button to an appointment that's displayed to a meeting attendee in Outlook on mobile devices. For more information, see [Log appointment notes to an external application in Outlook mobile add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/mobile-log-appointments).

**Type**  
Array of string

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 7.

**Supported values**  
Allowed values: `mailRead`, `mailCompose`, `meetingDetailsOrganizer`, `meetingDetailsAttendee`, `onlineMeetingDetailsOrganizer`, `logEventMeetingDetailsAttendee`, `default`.

#### tabs

Configures custom tabs or customized built-in tabs on the Office application ribbon.

**Type**  
Array of [extensionRibbonsArrayTabsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-tabs-item?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Maximum array items: 20.

**Supported values**  


#### fixedControls

Configures the button of an [integrated spam-reporting](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting) add-in in Outlook. Must configure if `spamReportingOverride` is specified in the `extensions.ribbons.contexts` array.

**Type**  
Array of [extensionRibbonsArrayFixedControlItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 1.

**Supported values**  


#### fixedControls

Configures the button of an [integrated spam-reporting](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting) add-in in Outlook. Must configure if `spamReportingOverride` is specified in the `extensions.ribbons.contexts` array.

**Type**  
Array of [extensionRibbonsArrayFixedControlItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### spamPreProcessingDialog

Configures the preprocessing dialog of an [integrated spam-reporting](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/spam-reporting) add-in in Outlook.

**Type**  
[extensionRibbonsSpamPreProcessingDialog](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Remarks

To use `extensions.ribbons`, see [create add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest), [configure the UI for the task pane command](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest#configure-the-ui-for-the-task-pane-command), and [configure the UI for the function command](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest#configure-the-ui-for-the-function-command).

## Examples

```json
{
 "extensions": [
    {
      "ribbons": [
        {
          "contexts": [
            "mailCompose"
          ],
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
                    },
                    {
                      "id": "menu1",
                      "type": "menu",
                      "label": "My Menu",
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
                        "title": "My Menu",
                        "description": "Menu with 2 actions"
                      },
                      "items": [
                        {
                          "id": "menuItem1",
                          "type": "menuItem",
                          "label": "Action 2",
                          "supertip": {
                            "title": "Action 2 Title",
                            "description": "Action 2 Description"
                          },
                          "actionId": "action2"
                        },
                        {
                          "id": "menuItem2",
                          "type": "menuItem",
                          "label": "Action 3",
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
                            "title": "Action 3 Title",
                            "description": "Action 3 Description"
                          },
                          "actionId": "action3"
                        }
                      ]
                    }
                  ]
                }
              ],
            }
          ]
        },
        {
          "contexts": [ "mailRead" ],
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
