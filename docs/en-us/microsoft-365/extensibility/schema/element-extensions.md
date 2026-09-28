<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# elementExtensions object

The `extensions` property specifies Outlook Add-ins within an app manifest and simplifies the distribution and acquisition across the Microsoft 365 ecosystem. Each app supports only one extension. For more information, see [Office Add-ins manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/unified-manifest-overview).

Properties that reference this object type:

- [root.extensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#extensions-property)

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
  "runtimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "type": "general",
      "code": {
        extensionRuntimeCode object
      },
      "lifetime": "short | long",
      "actions": [
        {
          extensionRuntimesActionsItem object
        }
      ],
      "customFunctions": {
        extensionCustomFunctions object
      }
    }
  ],
  "ribbons": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "contexts": [
        "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default | spamReportingOverride"
      ],
      "tabs": [
        {
          extensionRibbonsArrayTabsItem object
        }
      ],
      "fixedControls": [
        {
          extensionRibbonsArrayFixedControlItem object
        }
      ],
      "spamPreProcessingDialog": {
        extensionRibbonsSpamPreProcessingDialog object
      }
    }
  ],
  "autoRunEvents": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "events": [
        {
          events object
        }
      ]
    }
  ],
  "alternates": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "prefer": {
        prefer object
      },
      "hide": {
        hide object
      },
      "alternateIcons": {
        alternateIcons object
      }
    }
  ],
  "audienceClaimUrl": "{string}",
  "appDeeplinks": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "contexts": [
        "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default | spamReportingOverride"
      ],
      "actionId": "{string}",
      "label": "{string}",
      "semanticDescription": "{string}"
    }
  ],
  "contentRuntimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "code": {
        extensionRuntimeCode object
      },
      "requestedHeight": {number},
      "requestedWidth": {number},
      "disableSnapshot": {boolean}
    }
  ],
  "getStartedMessages": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "title": "{string}",
      "description": "{string}",
      "learnMoreUrl": "{string}"
    }
  ],
  "contextMenus": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "menus": [
        {
          extensionMenuItem object
        }
      ]
    }
  ],
  "keyboardShortcuts": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "shortcuts": [
        {
          extensionShortcut object
        }
      ],
      "keyMappingFiles": {
        keyboardShortcutsMappingFiles object
      }
    }
  ]
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "runtimes": {
      "$ref": "#/definitions/extensionRuntimesArray",
      "description": "General runtime for \u0022MailApp\u0022 or \u0022TaskpaneApp\u0022. Configures the set of runtimes and actions that can be used by each extension point. Min size 1."
    },
    "ribbons": {
      "$ref": "#/definitions/extensionRibbonsArray"
    },
    "autoRunEvents": {
      "$ref": "#/definitions/extensionAutoRunEventsArray"
    },
    "alternates": {
      "$ref": "#/definitions/extensionAlternateVersionsArray"
    },
    "audienceClaimUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url for your extension, used to validate Exchange user identity tokens."
    },
    "appDeeplinks": {
      "$ref": "#/definitions/extensionAppDeeplinksArray"
    },
    "contentRuntimes": {
      "$ref": "#/definitions/extensionContentRuntimeArray"
    },
    "getStartedMessages": {
      "$ref": "#/definitions/extensionGetStartedMessageArray"
    },
    "contextMenus": {
      "$ref": "#/definitions/extensionContextMenuArray",
      "description": "Specifies the context menus for your extension. A context menu is a shortcut menu that appears when a user right-clicks (selects and holds) in the Office UI. Min size 1."
    },
    "keyboardShortcuts": {
      "type": "array",
      "description": " Keyboard shortcuts, also known as key combinations, enable your add-in\u0027s users to work more efficiently. Keyboard shortcuts also improve the add-in\u0027s accessibility for users with disabilities by providing an alternative to the mouse.",
      "items": {
        "$ref": "#/definitions/extensionKeyboardShortcut"
      },
      "minItems": 1,
      "maxItems": 10
    }
  },
  "additionalProperties": false
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
  "runtimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "type": "general",
      "code": {
        extensionRuntimeCode object
      },
      "lifetime": "short | long",
      "actions": [
        {
          extensionRuntimesActionsItem object
        }
      ],
      "customFunctions": {
        extensionCustomFunctions object
      }
    }
  ],
  "ribbons": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "contexts": [
        "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | spamReportingOverride | default"
      ],
      "tabs": [
        {
          extensionRibbonsArrayTabsItem object
        }
      ],
      "fixedControls": [
        {
          extensionRibbonsArrayFixedControlItem object
        }
      ],
      "spamPreProcessingDialog": {
        extensionRibbonsSpamPreProcessingDialog object
      }
    }
  ],
  "autoRunEvents": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "events": [
        {
          events object
        }
      ]
    }
  ],
  "alternates": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "prefer": {
        prefer object
      },
      "hide": {
        hide object
      },
      "alternateIcons": {
        alternateIcons object
      }
    }
  ],
  "contentRuntimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "code": {
        extensionRuntimeCode object
      },
      "requestedHeight": {number},
      "requestedWidth": {number},
      "disableSnapshot": {boolean}
    }
  ],
  "getStartedMessages": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "title": "{string}",
      "description": "{string}",
      "learnMoreUrl": "{string}"
    }
  ],
  "contextMenus": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "menus": [
        {
          extensionMenuItem object
        }
      ]
    }
  ],
  "keyboardShortcuts": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "shortcuts": [
        {
          extensionShortcut object
        }
      ],
      "keyMappingFiles": {
        keyboardShortcutsMappingFiles object
      }
    }
  ],
  "audienceClaimUrl": "{string}"
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "runtimes": {
      "$ref": "#/definitions/extensionRuntimesArray"
    },
    "ribbons": {
      "$ref": "#/definitions/extensionRibbonsArray"
    },
    "autoRunEvents": {
      "$ref": "#/definitions/extensionAutoRunEventsArray"
    },
    "alternates": {
      "$ref": "#/definitions/extensionAlternateVersionsArray"
    },
    "contentRuntimes": {
      "$ref": "#/definitions/extensionContentRuntimeArray"
    },
    "getStartedMessages": {
      "$ref": "#/definitions/extensionGetStartedMessageArray"
    },
    "contextMenus": {
      "$ref": "#/definitions/extensionContextMenuArray"
    },
    "keyboardShortcuts": {
      "type": "array",
      "description": " Keyboard shortcuts, also known as key combinations, enable your add-in\u0027s users to work more efficiently. Keyboard shortcuts also improve the add-in\u0027s accessibility for users with disabilities by providing an alternative to the mouse.",
      "items": {
        "$ref": "#/definitions/extensionKeyboardShortcut"
      },
      "minItems": 1,
      "maxItems": 10
    },
    "audienceClaimUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url for your extension, used to validate Exchange user identity tokens."
    }
  },
  "additionalProperties": false
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
  "runtimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "type": "general",
      "code": {
        extensionRuntimeCode object
      },
      "lifetime": "short | long",
      "actions": [
        {
          extensionRuntimesActionsItem object
        }
      ],
      "customFunctions": {
        extensionCustomFunctions object
      }
    }
  ],
  "ribbons": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "contexts": [
        "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | spamReportingOverride | default"
      ],
      "tabs": [
        {
          extensionRibbonsArrayTabsItem object
        }
      ],
      "fixedControls": [
        {
          extensionRibbonsArrayFixedControlItem object
        }
      ],
      "spamPreProcessingDialog": {
        extensionRibbonsSpamPreProcessingDialog object
      }
    }
  ],
  "autoRunEvents": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "events": [
        {
          events object
        }
      ]
    }
  ],
  "alternates": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "prefer": {
        prefer object
      },
      "hide": {
        hide object
      },
      "alternateIcons": {
        alternateIcons object
      }
    }
  ],
  "contentRuntimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "code": {
        extensionRuntimeCode object
      },
      "requestedHeight": {number},
      "requestedWidth": {number},
      "disableSnapshot": {boolean}
    }
  ],
  "getStartedMessages": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "title": "{string}",
      "description": "{string}",
      "learnMoreUrl": "{string}"
    }
  ],
  "contextMenus": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "menus": [
        {
          extensionMenuItem object
        }
      ]
    }
  ],
  "keyboardShortcuts": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "shortcuts": [
        {
          extensionShortcut object
        }
      ],
      "keyMappingFiles": {
        keyboardShortcutsMappingFiles object
      }
    }
  ],
  "audienceClaimUrl": "{string}"
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "runtimes": {
      "$ref": "#/definitions/extensionRuntimesArray"
    },
    "ribbons": {
      "$ref": "#/definitions/extensionRibbonsArray"
    },
    "autoRunEvents": {
      "$ref": "#/definitions/extensionAutoRunEventsArray"
    },
    "alternates": {
      "$ref": "#/definitions/extensionAlternateVersionsArray"
    },
    "contentRuntimes": {
      "$ref": "#/definitions/extensionContentRuntimeArray"
    },
    "getStartedMessages": {
      "$ref": "#/definitions/extensionGetStartedMessageArray"
    },
    "contextMenus": {
      "$ref": "#/definitions/extensionContextMenuArray"
    },
    "keyboardShortcuts": {
      "type": "array",
      "description": " Keyboard shortcuts, also known as key combinations, enable your add-in\u0027s users to work more efficiently. Keyboard shortcuts also improve the add-in\u0027s accessibility for users with disabilities by providing an alternative to the mouse.",
      "items": {
        "$ref": "#/definitions/extensionKeyboardShortcut"
      },
      "minItems": 1,
      "maxItems": 10
    },
    "audienceClaimUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url for your extension, used to validate Exchange user identity tokens."
    }
  },
  "additionalProperties": false
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
  "runtimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "type": "general",
      "code": {
        extensionRuntimeCode object
      },
      "lifetime": "short | long",
      "actions": [
        {
          extensionRuntimesActionsItem object
        }
      ],
      "customFunctions": {
        extensionCustomFunctions object
      }
    }
  ],
  "ribbons": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "contexts": [
        "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default | spamReportingOverride"
      ],
      "tabs": [
        {
          extensionRibbonsArrayTabsItem object
        }
      ],
      "fixedControls": [
        {
          extensionRibbonsArrayFixedControlItem object
        }
      ],
      "spamPreProcessingDialog": {
        extensionRibbonsSpamPreProcessingDialog object
      }
    }
  ],
  "autoRunEvents": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "events": [
        {
          events object
        }
      ]
    }
  ],
  "alternates": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "prefer": {
        prefer object
      },
      "hide": {
        hide object
      },
      "alternateIcons": {
        alternateIcons object
      }
    }
  ],
  "contentRuntimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "code": {
        extensionRuntimeCode object
      },
      "requestedHeight": {number},
      "requestedWidth": {number},
      "disableSnapshot": {boolean}
    }
  ],
  "getStartedMessages": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "title": "{string}",
      "description": "{string}",
      "learnMoreUrl": "{string}"
    }
  ],
  "contextMenus": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "menus": [
        {
          extensionMenuItem object
        }
      ]
    }
  ],
  "keyboardShortcuts": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "shortcuts": [
        {
          extensionShortcut object
        }
      ],
      "keyMappingFiles": {
        keyboardShortcutsMappingFiles object
      }
    }
  ],
  "audienceClaimUrl": "{string}"
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "runtimes": {
      "$ref": "#/definitions/extensionRuntimesArray"
    },
    "ribbons": {
      "$ref": "#/definitions/extensionRibbonsArray"
    },
    "autoRunEvents": {
      "$ref": "#/definitions/extensionAutoRunEventsArray"
    },
    "alternates": {
      "$ref": "#/definitions/extensionAlternateVersionsArray"
    },
    "contentRuntimes": {
      "$ref": "#/definitions/extensionContentRuntimeArray"
    },
    "getStartedMessages": {
      "$ref": "#/definitions/extensionGetStartedMessageArray"
    },
    "contextMenus": {
      "$ref": "#/definitions/extensionContextMenuArray"
    },
    "keyboardShortcuts": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionKeyboardShortcut"
      },
      "minItems": 1,
      "maxItems": 10
    },
    "audienceClaimUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url for your extension, used to validate Exchange user identity tokens."
    }
  },
  "additionalProperties": false
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
  "runtimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "type": "general",
      "code": {
        extensionRuntimeCode object
      },
      "lifetime": "short | long",
      "actions": [
        {
          extensionRuntimesActionsItem object
        }
      ],
      "customFunctions": {
        extensionCustomFunctions object
      }
    }
  ],
  "ribbons": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "contexts": [
        "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default | spamReportingOverride"
      ],
      "tabs": [
        {
          extensionRibbonsArrayTabsItem object
        }
      ],
      "fixedControls": [
        {
          extensionRibbonsArrayFixedControlItem object
        }
      ],
      "spamPreProcessingDialog": {
        extensionRibbonsSpamPreProcessingDialog object
      }
    }
  ],
  "autoRunEvents": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "events": [
        {
          events object
        }
      ]
    }
  ],
  "alternates": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "prefer": {
        prefer object
      },
      "hide": {
        hide object
      },
      "alternateIcons": {
        alternateIcons object
      }
    }
  ],
  "contentRuntimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "code": {
        extensionRuntimeCode object
      },
      "requestedHeight": {number},
      "requestedWidth": {number},
      "disableSnapshot": {boolean}
    }
  ],
  "getStartedMessages": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "title": "{string}",
      "description": "{string}",
      "learnMoreUrl": "{string}"
    }
  ],
  "contextMenus": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "menus": [
        {
          extensionMenuItem object
        }
      ]
    }
  ],
  "keyboardShortcuts": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "shortcuts": [
        {
          extensionShortcut object
        }
      ]
    }
  ],
  "audienceClaimUrl": "{string}"
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "runtimes": {
      "$ref": "#/definitions/extensionRuntimesArray"
    },
    "ribbons": {
      "$ref": "#/definitions/extensionRibbonsArray"
    },
    "autoRunEvents": {
      "$ref": "#/definitions/extensionAutoRunEventsArray"
    },
    "alternates": {
      "$ref": "#/definitions/extensionAlternateVersionsArray"
    },
    "contentRuntimes": {
      "$ref": "#/definitions/extensionContentRuntimeArray"
    },
    "getStartedMessages": {
      "$ref": "#/definitions/extensionGetStartedMessageArray"
    },
    "contextMenus": {
      "$ref": "#/definitions/extensionContextMenuArray"
    },
    "keyboardShortcuts": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/extensionKeyboardShortcut"
      },
      "minItems": 1,
      "maxItems": 10
    },
    "audienceClaimUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url for your extension, used to validate Exchange user identity tokens."
    }
  },
  "additionalProperties": false
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
  "runtimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "type": "general",
      "code": {
        extensionRuntimeCode object
      },
      "lifetime": "short | long",
      "actions": [
        {
          extensionRuntimesActionsItem object
        }
      ]
    }
  ],
  "ribbons": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "contexts": [
        "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default | spamReportingOverride"
      ],
      "tabs": [
        {
          extensionRibbonsArrayTabsItem object
        }
      ],
      "fixedControls": [
        {
          extensionRibbonsArrayFixedControlItem object
        }
      ],
      "spamPreProcessingDialog": {
        extensionRibbonsSpamPreProcessingDialog object
      }
    }
  ],
  "autoRunEvents": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "events": [
        {
          events object
        }
      ]
    }
  ],
  "alternates": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "prefer": {
        prefer object
      },
      "hide": {
        hide object
      },
      "alternateIcons": {
        alternateIcons object
      }
    }
  ],
  "audienceClaimUrl": "{string}"
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "runtimes": {
      "$ref": "#/definitions/extensionRuntimesArray"
    },
    "ribbons": {
      "$ref": "#/definitions/extensionRibbonsArray"
    },
    "autoRunEvents": {
      "$ref": "#/definitions/extensionAutoRunEventsArray"
    },
    "alternates": {
      "$ref": "#/definitions/extensionAlternateVersionsArray"
    },
    "audienceClaimUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url for your extension, used to validate Exchange user identity tokens."
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_7_syntax)
- [Schema](#tabpanel_7_schema)

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
  "runtimes": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "id": "{string}",
      "type": "general",
      "code": {
        extensionRuntimeCode object
      },
      "lifetime": "short | long",
      "actions": [
        {
          extensionRuntimesActionsItem object
        }
      ]
    }
  ],
  "ribbons": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "contexts": [
        "mailRead | mailCompose | meetingDetailsOrganizer | meetingDetailsAttendee | onlineMeetingDetailsOrganizer | logEventMeetingDetailsAttendee | default"
      ],
      "tabs": [
        {
          extensionRibbonsArrayTabsItem object
        }
      ]
    }
  ],
  "autoRunEvents": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "events": [
        {
          events object
        }
      ]
    }
  ],
  "alternates": [
    {
      "requirements": {
        requirementsExtensionElement object
      },
      "prefer": {
        prefer object
      },
      "hide": {
        hide object
      },
      "alternateIcons": {
        alternateIcons object
      }
    }
  ],
  "audienceClaimUrl": "{string}"
}
```

```json
{
  "type": "object",
  "minProperties": 1,
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "runtimes": {
      "$ref": "#/definitions/extensionRuntimesArray"
    },
    "ribbons": {
      "$ref": "#/definitions/extensionRibbonsArray"
    },
    "autoRunEvents": {
      "$ref": "#/definitions/extensionAutoRunEventsArray"
    },
    "alternates": {
      "$ref": "#/definitions/extensionAlternateVersionsArray"
    },
    "audienceClaimUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url for your extension, used to validate Exchange user identity tokens."
    }
  },
  "additionalProperties": false
}
```

## Properties

#### requirements

Specifies the set of client or host requirements for the extension.

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### runtimes

Configures the set of runtimes and actions that can be used by each extension point. For more information, see [runtimes in Office Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes).

**Type**  
Array of [extensionRuntimesArray](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 20.

**Supported values**  


#### ribbons

Defines the ribbons extension point.

**Type**  
Array of [extensionRibbonsArray](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 20.

**Supported values**  


#### autoRunEvents

Defines the event-based activation extension point.

**Type**  
Array of [extensionAutoRunEventsArray](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 10.

**Supported values**  


#### alternates

Specifies the relationship to alternate existing Microsoft 365 solutions. It's used to hide or prioritize add-ins from the same publisher with overlapping functionality.

**Type**  
Array of [extensionAlternateVersionsArray](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 10.

**Supported values**  


#### audienceClaimUrl

Specifies the URL for your extension and is used to validate Exchange user identity tokens. For more information, see [inside the Exchange identity token](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/inside-the-identity-token).

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### appDeeplinks

Do not use. For Microsoft internal use only.

**Type**  
Array of [extensionAppDeeplinksArray](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-app-deeplinks-array?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1.

**Supported values**  


#### contentRuntimes

Configures a page of content that is embedded in an Excel or PowerPoint document.

**Type**  
Array of [extensionContentRuntimeArray](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-content-runtime-array?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1.

**Supported values**  


#### getStartedMessages

Provides information used by the callout that appears when the add-in is installed.

**Type**  
Array of [extensionGetStartedMessageArray](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-get-started-message-array?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 3.

**Supported values**  


#### contextMenus

Specifies the context menus for your extension. A context menu is a shortcut menu that appears when a user right-clicks \(selects and holds\) in the Office UI. Min size 1.

**Type**  
Array of [extensionContextMenuArray](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-context-menu-array?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1.

**Supported values**  


#### keyboardShortcuts

Keyboard shortcuts, also known as key combinations, enable your add-in's users to work more efficiently. Keyboard shortcuts also improve the add-in's accessibility for users with disabilities by providing an alternative to the mouse.

**Type**  
Array of [extensionKeyboardShortcut](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 10.

**Supported values**  


## Examples

```json
{
 "extensions": [
    {
      "requirements": {
        "scopes": [ "mail" ],
        "capabilities": [
          {
            "name": "Mailbox", "minVersion": "1.1"
          }
        ]
      },
      "runtimes": [
        {
          "requirements": {
            "capabilities": [
              {
                "name": "MailBox",
                "minVersion": "1.10"
              }
            ]
          },
          "id": "eventsRuntime",
          "type": "general",
          "code": {
            "page": "https://contoso.com/events.html",
            "script": "https://contoso.com/events.js"
          },
          "lifetime": "short",
          "actions": [
            {
              "id": "onMessageSending",
              "type": "executeFunction"
            },
            {
              "id": "onNewMessageComposeCreated",
              "type": "executeFunction"
            }
          ]
        },
        {
          "requirements": {
            "capabilities": [
              {
                "name": "MailBox", "minVersion": "1.1"
              }
            ]
          },
          "id": "commandsRuntime",
          "type": "general",
          "code": {
            "page": "https://contoso.com/commands.html",
            "script": "https://contoso.com/commands.js"
          },
          "lifetime": "short",
          "actions": [
            {
              "id": "action1",
              "type": "executeFunction"
            },
            {
              "id": "action2",
              "type": "executeFunction"
            },
            {
              "id": "action3",
              "type": "executeFunction"
            }
          ]
        }
      ],
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
      ],
      "autoRunEvents": [
        {
          "requirements": {
            "capabilities": [
              {
                "name": "MailBox", "minVersion": "1.10"
              }
            ]
          },
          "events": [
            {
              "type": "newMessageComposeCreated",
              "actionId": "onNewMessageComposeCreated"
            },
            {
              "type": "messageSending",
              "actionId": "onMessageSending",
              "options": {
                "sendMode": "promptUser"
              }
            }
          ]
        }
      ],
      "alternates": [
        {
          "requirements": {
            "scopes": [ "mail" ]
          },
          "prefer": {
            "comAddin": {
              "progId": "ContosoExtension"
            }
          },
          "hide": {
            "storeOfficeAddin": {
              "officeAddinId": "00000000-0000-0000-0000-000000000000",
              "assetId": "WA000000000"
            }
          },
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
      ]
    }
  ]
}
```
