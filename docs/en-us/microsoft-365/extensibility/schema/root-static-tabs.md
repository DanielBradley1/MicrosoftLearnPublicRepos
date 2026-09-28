<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-static-tabs?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.staticTabs object

A set of tabs that may be 'pinned' by default, without the user adding them manually. Static tabs declared in personal scope are always pinned to the app's personal experience. Static tabs do not currently support the 'teams' scope.

Properties that reference this object type:

- [root.staticTabs](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#staticTabs-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "entityId": "{string}",
  "name": "{string}",
  "contentUrl": "{string}",
  "contentBotId": "{string}",
  "websiteUrl": "{string}",
  "searchUrl": "{string}",
  "scopes": [
    "team | personal | groupChat"
  ],
  "context": [
    "personalTab | channelTab | privateChatTab | meetingChatTab | meetingDetailsTab | meetingSidePanel | meetingStage | teamLevelApp"
  ],
  "supportedPlatform": [
    "desktop | mobile | teamsMeetingDevices"
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "entityId": {
      "type": "string",
      "description": "A unique identifier for the entity which the tab displays.",
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "description": "The display name of the tab.",
      "maxLength": 128
    },
    "contentUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url which points to the entity UI to be displayed in the Teams canvas."
    },
    "contentBotId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "websiteUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to point at if a user opts to view in a browser."
    },
    "searchUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to direct a user\u0027s search queries."
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the tab offers an experience in the context of a channel in a team, or an experience scoped to an individual user alone or a group chat. These options are non-exclusive. Currently static tabs are only supported in the \u0027personal\u0027 scope.",
      "maxItems": 3,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat"
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
          "teamLevelApp"
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
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet",
      "description": "The set of requirements for the tab."
    }
  },
  "required": [
    "entityId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "entityId": "{string}",
  "name": "{string}",
  "contentUrl": "{string}",
  "contentBotId": "{string}",
  "websiteUrl": "{string}",
  "searchUrl": "{string}",
  "scopes": [
    "team | personal | groupChat"
  ],
  "context": [
    "personalTab | channelTab | privateChatTab | meetingChatTab | meetingDetailsTab | meetingSidePanel | meetingStage | teamLevelApp"
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "entityId": {
      "type": "string",
      "description": "A unique identifier for the entity which the tab displays.",
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "description": "The display name of the tab.",
      "maxLength": 128
    },
    "contentUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url which points to the entity UI to be displayed in the canvas."
    },
    "contentBotId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "websiteUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to point at if a user opts to view in a browser."
    },
    "searchUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url to direct a user\u0027s search queries."
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the tab offers an experience in the context of a channel in a team, or an experience scoped to an individual user alone or group chat. These options are non-exclusive. Currently static tabs are only supported in the \u0027personal\u0027 scope.",
      "maxItems": 3,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat"
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
          "teamLevelApp"
        ]
      }
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  },
  "required": [
    "entityId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "entityId": "{string}",
  "name": "{string}",
  "contentUrl": "{string}",
  "contentBotId": "{string}",
  "websiteUrl": "{string}",
  "searchUrl": "{string}",
  "scopes": [
    "team | personal | groupChat"
  ],
  "context": [
    "personalTab | channelTab | privateChatTab | meetingChatTab | meetingDetailsTab | meetingSidePanel | meetingStage | teamLevelApp"
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "entityId": {
      "type": "string",
      "description": "A unique identifier for the entity which the tab displays.",
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "description": "The display name of the tab.",
      "maxLength": 128
    },
    "contentUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url which points to the entity UI to be displayed in the canvas."
    },
    "contentBotId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "websiteUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to point at if a user opts to view in a browser."
    },
    "searchUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to direct a user\u0027s search queries."
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the tab offers an experience in the context of a channel in a team, or an experience scoped to an individual user alone or group chat. These options are non-exclusive. Currently static tabs are only supported in the \u0027personal\u0027 scope.",
      "maxItems": 3,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat"
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
          "teamLevelApp"
        ]
      }
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  },
  "required": [
    "entityId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "entityId": "{string}",
  "name": "{string}",
  "contentUrl": "{string}",
  "contentBotId": "{string}",
  "websiteUrl": "{string}",
  "searchUrl": "{string}",
  "scopes": [
    "team | personal | groupChat"
  ],
  "context": [
    "personalTab | channelTab | privateChatTab | meetingChatTab | meetingDetailsTab | meetingSidePanel | meetingStage | teamLevelApp"
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "entityId": {
      "type": "string",
      "description": "A unique identifier for the entity which the tab displays.",
      "maxLength": 64
    },
    "name": {
      "type": "string",
      "description": "The display name of the tab.",
      "maxLength": 128
    },
    "contentUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url which points to the entity UI to be displayed in the canvas."
    },
    "contentBotId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "websiteUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to point at if a user opts to view in a browser."
    },
    "searchUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url to direct a user\u0027s search queries."
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the tab offers an experience in the context of a channel in a team, or an experience scoped to an individual user alone or group chat. These options are non-exclusive. Currently static tabs are only supported in the \u0027personal\u0027 scope.",
      "maxItems": 3,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat"
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
          "teamLevelApp"
        ]
      }
    }
  },
  "required": [
    "entityId",
    "scopes"
  ]
}
```

## Properties

#### entityId

A unique identifier for the entity which the tab displays.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### name

The display name of the tab.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### contentUrl

The url which points to the entity UI to be displayed in the Teams canvas.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### contentBotId

The Microsoft App ID specified for the bot in the Bot Framework portal \([https://dev.botframework.com/bots](https://dev.botframework.com/bots)\).

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### websiteUrl

The url to point at if a user opts to view in a browser.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### searchUrl

The url to direct a user's search queries.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### scopes

Specifies whether the tab offers an experience in the context of a channel in a team, or an experience scoped to an individual user alone or a group chat. These options are non-exclusive. Currently static tabs are only supported in the `personal` scope.

**Type**  
Array of enum

**Required**  
✅

**Constraints**  
Maximum array items: 3.

**Supported values**  
Allowed values: `team`, `personal`, `groupChat`.

#### context

The set of `contextItem` scopes to which a tab belongs.

**Type**  
Array of enum

**Required**  
—

**Constraints**  
Maximum array items: 8.

**Supported values**  
Allowed values: `personalTab`, `channelTab`, `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`, `meetingStage`, `teamLevelApp`.

#### supportedPlatform

The set of `supportedPlatform` scopes to which a tab belongs.

**Type**  
Array of enum

**Required**  
—

**Constraints**  
Maximum array items: 3.

**Supported values**  
Allowed values: `desktop`, `mobile`, `teamsMeetingDevices`.

#### requirementSet

Runtime requirements for the tab to function properly in the Microsoft 365 host application. If one or more of the requirements aren't supported by the runtime host, the host won't load the tab.

**Type**  
[elementRequirementSet](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Remarks

Defines a set of tabs that can be pinned by default, without the user adding them manually. Static tabs declared in `personal` scope are always pinned to the app's personal experience. However, the pinned tabs can be reordered by adding the details of the tab in the same desired order. For more information, see [reorder static personal tabs](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/create-personal-tab#reorder-tabs).

This property also enables you to set the default landing capability for an app supporting both tab and bot capabilities in personal scope. For more information, see [configure default landing capability](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/add-default-install-scope#configure-your-apps-default-landing-capability).

This item is an array \(maximum of 16 elements\) with all elements of the type `object`. This block is required only for apps that provide one or more static tabs.

Render tabs with Adaptive Cards by specifying `contentBotId` instead of `contentUrl` in the **staticTabs** block.

Note

- The `groupChat` and `team` scopes are supported only in public developer preview.
- The `teamLevelApp` context is dedicated only for Education tenants.
- The `searchUrl` feature is not available for the third-party developers.
- If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, For more information, see [Get context for your Microsoft Teams tab](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/access-teams-context).

## Examples

```json
{
   "staticTabs": [
        {
            "entityId": "unique Id for the page entity",
            "scopes": [
                "personal"
            ],
            "context": [
                "personalTab",
                "channelTab"
            ],
            "name": "Display name of tab",
            "contentUrl": "https://contoso.com/content (displayed in Teams canvas)",
            "websiteUrl": "https://contoso.com/content (displayed in web browser)",
            "searchUrl": "https://contoso.com/content (displayed in web browser)"
        }
 ],
}
```

```json
{
      "staticTabs": [
        {
            "entityId": "idForPage",
            "name": "Display name of tab",
            "contentUrl": "https://contoso.com/content?host=msteams",
            "contentBotId": "Specifies to the app that tab is an Adaptive Card Tab. You can either provide the contentBotId or contentUrl.",
            "websiteUrl": "https://contoso.com/content",
            "scopes": [
                "personal"
            ],
            "requirementSet": {
                "hostMustSupportFunctionalities": [
                  {"name": "dialogUrl"},
                  {"name": "dialogUrlBot"}
                ]
            }
        }
    ],
}
```
