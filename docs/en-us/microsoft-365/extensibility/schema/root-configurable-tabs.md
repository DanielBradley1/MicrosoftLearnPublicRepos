<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-configurable-tabs?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.configurableTabs object

These are tabs users can optionally add to their channels and 1:1 or group chats and require extra configuration before they are added. Configurable tabs are not supported in the personal scope. Currently only one configurable tab per app is supported.

Properties that reference this object type:

- [root.configurableTabs](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#configurableTabs-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "configurationUrl": "{string}",
  "canUpdateConfiguration": {boolean},
  "scopes": [
    "team | groupChat"
  ],
  "meetingSurfaces": [
    "sidePanel | stage"
  ],
  "context": [
    "personalTab | channelTab | privateChatTab | meetingChatTab | meetingDetailsTab | meetingSidePanel | meetingStage | callingSidePanel"
  ],
  "supportedPlatform": [
    "desktop | mobile | teamsMeetingDevices"
  ],
  "sharePointPreviewImage": "{string}",
  "supportedSharePointHosts": [
    "sharePointFullPage | sharePointWebPart"
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for the tab. This id must be unique within the app manifest.",
      "maxLength": 64
    },
    "configurationUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to use when configuring the tab."
    },
    "canUpdateConfiguration": {
      "type": "boolean",
      "description": "A value indicating whether an instance of the tab\u0027s configuration can be updated by the user after creation.",
      "default": true
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the tab offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive. Currently, configurable tabs are only supported in the teams and groupchats scopes.",
      "maxItems": 2,
      "items": {
        "enum": [
          "team",
          "groupChat"
        ]
      }
    },
    "meetingSurfaces": {
      "type": "array",
      "description": "The set of meetingSurfaceItem scopes that a tab belong to",
      "maxItems": 2,
      "items": {
        "enum": [
          "sidePanel",
          "stage"
        ]
      }
    },
    "context": {
      "type": "array",
      "description": "The set of contextItem scopes that a tab belong to",
      "maxItems": 8,
      "items": {
        "enum": [
          "personalTab",
          "channelTab",
          "privateChatTab",
          "meetingChatTab",
          "meetingDetailsTab",
          "meetingSidePanel",
          "meetingStage",
          "callingSidePanel"
        ]
      }
    },
    "supportedPlatform": {
      "type": "array",
      "description": "The set of supportedPlatform scopes that a tab belong to",
      "maxItems": 3,
      "items": {
        "enum": [
          "desktop",
          "mobile",
          "teamsMeetingDevices"
        ]
      }
    },
    "sharePointPreviewImage": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a tab preview image for use in SharePoint. Size 1024x768."
    },
    "supportedSharePointHosts": {
      "type": "array",
      "description": "Defines how your tab will be made available in SharePoint.",
      "maxItems": 2,
      "uniqueItems": true,
      "items": {
        "enum": [
          "sharePointFullPage",
          "sharePointWebPart"
        ]
      }
    }
  },
  "required": [
    "configurationUrl",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "configurationUrl": "{string}",
  "canUpdateConfiguration": {boolean},
  "scopes": [
    "team | groupChat"
  ],
  "meetingSurfaces": [
    "sidePanel | stage"
  ],
  "context": [
    "personalTab | channelTab | privateChatTab | meetingChatTab | meetingDetailsTab | meetingSidePanel | meetingStage"
  ],
  "sharePointPreviewImage": "{string}",
  "supportedSharePointHosts": [
    "sharePointFullPage | sharePointWebPart"
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for the tab. This id must be unique within the app manifest.",
      "maxLength": 64
    },
    "configurationUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to use when configuring the tab."
    },
    "canUpdateConfiguration": {
      "type": "boolean",
      "description": "A value indicating whether an instance of the tab\u0027s configuration can be updated by the user after creation.",
      "default": true
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the tab offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive. Currently, configurable tabs are only supported in the teams and groupchats scopes.",
      "maxItems": 2,
      "items": {
        "enum": [
          "team",
          "groupChat"
        ]
      }
    },
    "meetingSurfaces": {
      "type": "array",
      "description": "The set of meetingSurfaceItem scopes that a tab belong to",
      "maxItems": 2,
      "items": {
        "enum": [
          "sidePanel",
          "stage"
        ]
      }
    },
    "context": {
      "type": "array",
      "description": "The set of contextItem scopes that a tab belong to",
      "maxItems": 7,
      "items": {
        "enum": [
          "personalTab",
          "channelTab",
          "privateChatTab",
          "meetingChatTab",
          "meetingDetailsTab",
          "meetingSidePanel",
          "meetingStage"
        ]
      }
    },
    "sharePointPreviewImage": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a tab preview image for use in SharePoint. Size 1024x768."
    },
    "supportedSharePointHosts": {
      "type": "array",
      "description": "Defines how your tab will be made available in SharePoint.",
      "maxItems": 2,
      "uniqueItems": true,
      "items": {
        "enum": [
          "sharePointFullPage",
          "sharePointWebPart"
        ]
      }
    }
  },
  "required": [
    "configurationUrl",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "configurationUrl": "{string}",
  "canUpdateConfiguration": {boolean},
  "scopes": [
    "team | groupChat"
  ],
  "meetingSurfaces": [
    "sidePanel | stage"
  ],
  "context": [
    "personalTab | channelTab | privateChatTab | meetingChatTab | meetingDetailsTab | meetingSidePanel | meetingStage"
  ],
  "sharePointPreviewImage": "{string}",
  "supportedSharePointHosts": [
    "sharePointFullPage | sharePointWebPart"
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique identifier for the tab. This id must be unique within the app manifest.",
      "maxLength": 64
    },
    "configurationUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to use when configuring the tab."
    },
    "canUpdateConfiguration": {
      "type": "boolean",
      "description": "A value indicating whether an instance of the tab\u0027s configuration can be updated by the user after creation.",
      "default": true
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the tab offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive. Currently, configurable tabs are only supported in the teams and groupchats scopes.",
      "maxItems": 2,
      "items": {
        "enum": [
          "team",
          "groupChat"
        ]
      }
    },
    "meetingSurfaces": {
      "type": "array",
      "description": "The set of meetingSurfaceItem scopes that a tab belong to",
      "maxItems": 2,
      "items": {
        "enum": [
          "sidePanel",
          "stage"
        ]
      }
    },
    "context": {
      "type": "array",
      "description": "The set of contextItem scopes that a tab belong to",
      "maxItems": 7,
      "items": {
        "enum": [
          "personalTab",
          "channelTab",
          "privateChatTab",
          "meetingChatTab",
          "meetingDetailsTab",
          "meetingSidePanel",
          "meetingStage"
        ]
      }
    },
    "sharePointPreviewImage": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a tab preview image for use in SharePoint. Size 1024x768."
    },
    "supportedSharePointHosts": {
      "type": "array",
      "description": "Defines how your tab will be made available in SharePoint.",
      "maxItems": 2,
      "uniqueItems": true,
      "items": {
        "enum": [
          "sharePointFullPage",
          "sharePointWebPart"
        ]
      }
    }
  },
  "required": [
    "configurationUrl",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "configurationUrl": "{string}",
  "canUpdateConfiguration": {boolean},
  "scopes": [
    "team | groupChat"
  ],
  "meetingSurfaces": [
    "sidePanel | stage"
  ],
  "context": [
    "personalTab | channelTab | privateChatTab | meetingChatTab | meetingDetailsTab | meetingSidePanel | meetingStage"
  ],
  "sharePointPreviewImage": "{string}",
  "supportedSharePointHosts": [
    "sharePointFullPage | sharePointWebPart"
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "configurationUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to use when configuring the tab."
    },
    "canUpdateConfiguration": {
      "type": "boolean",
      "description": "A value indicating whether an instance of the tab\u0027s configuration can be updated by the user after creation.",
      "default": true
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the tab offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive. Currently, configurable tabs are only supported in the teams and groupchats scopes.",
      "maxItems": 2,
      "items": {
        "enum": [
          "team",
          "groupChat"
        ]
      }
    },
    "meetingSurfaces": {
      "type": "array",
      "description": "The set of meetingSurfaceItem scopes that a tab belong to",
      "maxItems": 2,
      "items": {
        "enum": [
          "sidePanel",
          "stage"
        ]
      }
    },
    "context": {
      "type": "array",
      "description": "The set of contextItem scopes that a tab belong to",
      "maxItems": 7,
      "items": {
        "enum": [
          "personalTab",
          "channelTab",
          "privateChatTab",
          "meetingChatTab",
          "meetingDetailsTab",
          "meetingSidePanel",
          "meetingStage"
        ]
      }
    },
    "sharePointPreviewImage": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a tab preview image for use in SharePoint. Size 1024x768."
    },
    "supportedSharePointHosts": {
      "type": "array",
      "description": "Defines how your tab will be made available in SharePoint.",
      "maxItems": 2,
      "uniqueItems": true,
      "items": {
        "enum": [
          "sharePointFullPage",
          "sharePointWebPart"
        ]
      }
    }
  },
  "required": [
    "configurationUrl",
    "scopes"
  ]
}
```

## Properties

#### id

A unique identifier for the tab. Used when defining one-way and mutual app capability dependencies under [elementRelationshipSet](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30). This id must be unique within the app manifest.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### id

A unique identifier for the tab. This id must be unique within the app manifest.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### configurationUrl

The *https://* url to use when configuring the tab.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### canUpdateConfiguration

A value indicating whether an instance of the tab's configuration can be updated by the user after creation.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `True`.

#### scopes

Specifies whether the tab offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive.

**Type**  
Array of enum

**Required**  
✅

**Constraints**  
Maximum array items: 2.

**Supported values**  
Allowed values: `team`, `groupChat`.

#### meetingSurfaces

The set of `meetingSurfaceItem` scopes to which a tab belongs.

**Type**  
Array of enum

**Required**  
—

**Constraints**  
Maximum array items: 2.

**Supported values**  
Allowed values: `sidePanel`, `stage`.

#### context

The set of `contextItem` scopes that a tab belong to.

**Type**  
Array of enum

**Required**  
—

**Constraints**  
Maximum array items: 8.

**Supported values**  
Allowed values: `personalTab`, `channelTab`, `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `callingSidePanel`.

#### context

The set of `contextItem` scopes that a tab belong to.

**Type**  
Array of enum

**Required**  
—

**Constraints**  
Maximum array items: 7.

**Supported values**  
Allowed values: `personalTab`, `channelTab`, `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`.

#### supportedPlatform

The set of supportedPlatform scopes that a tab belong to.

**Type**  
Array of enum

**Required**  
—

**Constraints**  
Maximum array items: 3.

**Supported values**  
Allowed values: `desktop`, `mobile`, `teamsMeetingDevices`.

#### sharePointPreviewImage

A relative file path to a tab preview image for use in SharePoint. Size 1024x768.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### supportedSharePointHosts

Defines how your tab will be made available in SharePoint.

**Type**  
Array of enum

**Required**  
—

**Constraints**  
Maximum array items: 2. Array items must be unique.

**Supported values**  
Allowed values: `sharePointFullPage`, `sharePointWebPart`.

## Examples

```json
{
"configurableTabs": [
        {
            "configurationUrl": "https://contoso.com/teamstab/configure",
            "scopes": [
                "team",
                "groupChat"
            ],
            "canUpdateConfiguration": true,
            "context": [
                "channelTab",
                "privateChatTab",
                "meetingChatTab",
                "meetingDetailsTab",
                "meetingSidePanel",
                "meetingStage"
            ],
            "sharePointPreviewImage": "Relative path to a tab preview image for use in SharePoint — 1024px X 768",
            "supportedSharePointHosts": [
                "sharePointFullPage",
                "sharePointWebPart"
            ]
        }
    ] 
}
```
