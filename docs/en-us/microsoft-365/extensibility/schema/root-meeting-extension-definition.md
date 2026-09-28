<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.meetingExtensionDefinition object

Specify meeting extension definition. For more information, see [custom Together Mode scenes in Teams](https://learn.microsoft.com/en-us/microsoftteams/platform/apps-in-teams-meetings/teams-together-mode).

Properties that reference this object type:

- [root.meetingExtensionDefinition](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#meetingExtensionDefinition-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "scenes": [
    {
      "id": "{string}",
      "name": "{string}",
      "file": "{string}",
      "preview": "{string}",
      "maxAudience": {number},
      "seatsReservedForOrganizersOrPresenters": {number}
    }
  ],
  "supportsCustomShareToStage": {boolean},
  "videoFilters": [
    {
      "id": "{string}",
      "name": "{string}",
      "thumbnail": "{string}"
    }
  ],
  "videoFiltersConfigurationUrl": "{string}",
  "supportsStreaming": {boolean},
  "supportsAnonymousGuestUsers": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "scenes": {
      "description": "Meeting supported scenes.",
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "A unique identifier for this scene. This id must be a GUID."
          },
          "name": {
            "type": "string",
            "description": "Scene name.",
            "maxLength": 128
          },
          "file": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a scene metadata json file."
          },
          "preview": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a scene PNG preview icon."
          },
          "maxAudience": {
            "type": "integer",
            "description": "Maximum audiences supported in scene.",
            "maximum": 50
          },
          "seatsReservedForOrganizersOrPresenters": {
            "type": "integer",
            "description": "Number of seats reserved for organizers or presenters.",
            "maximum": 50
          }
        },
        "required": [
          "id",
          "name",
          "file",
          "preview",
          "maxAudience",
          "seatsReservedForOrganizersOrPresenters"
        ]
      },
      "maxItems": 5,
      "type": "array",
      "uniqueItems": true
    },
    "supportsCustomShareToStage": {
      "description": "Represents if the app has added support for sharing to stage.",
      "type": "boolean",
      "default": false
    },
    "videoFilters": {
      "description": "Meeting supported video filters.",
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "A unique identifier for this video filter. This id must be a GUID."
          },
          "name": {
            "type": "string",
            "description": "Video filter\u0027s name.",
            "maxLength": 128
          },
          "thumbnail": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a video filter\u0027s thumbnail."
          }
        },
        "required": [
          "id",
          "name",
          "thumbnail"
        ]
      },
      "maxItems": 32,
      "type": "array",
      "uniqueItems": true
    },
    "videoFiltersConfigurationUrl": {
      "type": "string",
      "description": "A URL for configuring the video filters.",
      "maxLength": 2048
    },
    "supportsStreaming": {
      "type": "boolean",
      "description": "A boolean value indicating whether this app can stream the meeting\u0027s audio video content to an RTMP endpoint.",
      "default": false
    },
    "supportsAnonymousGuestUsers": {
      "type": "boolean",
      "description": "A boolean value indicating whether this app supports access by anonymous guest users.",
      "default": false
    }
  },
  "description": "Specify meeting extension definition.",
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "scenes": [
    {
      "id": "{string}",
      "name": "{string}",
      "file": "{string}",
      "preview": "{string}",
      "maxAudience": {number},
      "seatsReservedForOrganizersOrPresenters": {number}
    }
  ],
  "supportsStreaming": {boolean},
  "supportsCustomShareToStage": {boolean},
  "supportsAnonymousGuestUsers": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "scenes": {
      "description": "Meeting supported scenes.",
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "A unique identifier for this scene. This id must be a GUID."
          },
          "name": {
            "type": "string",
            "description": "Scene name.",
            "maxLength": 128
          },
          "file": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a scene metadata json file."
          },
          "preview": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a scene PNG preview icon."
          },
          "maxAudience": {
            "type": "integer",
            "description": "Maximum audiences supported in scene.",
            "maximum": 50
          },
          "seatsReservedForOrganizersOrPresenters": {
            "type": "integer",
            "description": "Number of seats reserved for organizers or presenters.",
            "maximum": 50
          }
        },
        "required": [
          "id",
          "name",
          "file",
          "preview",
          "maxAudience",
          "seatsReservedForOrganizersOrPresenters"
        ]
      },
      "maxItems": 5,
      "type": "array",
      "uniqueItems": true
    },
    "supportsStreaming": {
      "type": "boolean",
      "description": "A boolean value indicating whether this app can stream the meeting\u0027s audio video content to an RTMP endpoint.",
      "default": false
    },
    "supportsCustomShareToStage": {
      "description": "Represents if the app has added support for sharing to stage.",
      "type": "boolean",
      "default": false
    },
    "supportsAnonymousGuestUsers": {
      "type": "boolean",
      "description": "A boolean value indicating whether this app allows management by anonymous users.",
      "default": false
    }
  },
  "description": "Specify meeting extension definition.",
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "scenes": [
    {
      "id": "{string}",
      "name": "{string}",
      "file": "{string}",
      "preview": "{string}",
      "maxAudience": {number},
      "seatsReservedForOrganizersOrPresenters": {number}
    }
  ],
  "supportsCustomShareToStage": {boolean},
  "supportsStreaming": {boolean},
  "supportsAnonymousGuestUsers": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "scenes": {
      "description": "Meeting supported scenes.",
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "A unique identifier for this scene. This id must be a GUID."
          },
          "name": {
            "type": "string",
            "description": "Scene name.",
            "maxLength": 128
          },
          "file": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a scene metadata json file."
          },
          "preview": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a scene PNG preview icon."
          },
          "maxAudience": {
            "type": "integer",
            "description": "Maximum audiences supported in scene.",
            "maximum": 50
          },
          "seatsReservedForOrganizersOrPresenters": {
            "type": "integer",
            "description": "Number of seats reserved for organizers or presenters.",
            "maximum": 50
          }
        },
        "required": [
          "id",
          "name",
          "file",
          "preview",
          "maxAudience",
          "seatsReservedForOrganizersOrPresenters"
        ]
      },
      "maxItems": 5,
      "type": "array",
      "uniqueItems": true
    },
    "supportsCustomShareToStage": {
      "description": "Represents if the app has added support for sharing to stage.",
      "type": "boolean",
      "default": false
    },
    "supportsStreaming": {
      "type": "boolean",
      "description": "A boolean value indicating whether this app can stream the meeting\u0027s audio video content to an RTMP endpoint.",
      "default": false
    },
    "supportsAnonymousGuestUsers": {
      "type": "boolean",
      "description": "A boolean value indicating whether this app allows management by anonymous users.",
      "default": false
    }
  },
  "description": "Specify meeting extension definition.",
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "scenes": [
    {
      "id": "{string}",
      "name": "{string}",
      "file": "{string}",
      "preview": "{string}",
      "maxAudience": {number},
      "seatsReservedForOrganizersOrPresenters": {number}
    }
  ],
  "supportsStreaming": {boolean},
  "supportsAnonymousGuestUsers": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "scenes": {
      "description": "Meeting supported scenes.",
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "A unique identifier for this scene. This id must be a GUID."
          },
          "name": {
            "type": "string",
            "description": "Scene name.",
            "maxLength": 128
          },
          "file": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a scene metadata json file."
          },
          "preview": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a scene PNG preview icon."
          },
          "maxAudience": {
            "type": "integer",
            "description": "Maximum audiences supported in scene.",
            "maximum": 50
          },
          "seatsReservedForOrganizersOrPresenters": {
            "type": "integer",
            "description": "Number of seats reserved for organizers or presenters.",
            "maximum": 50
          }
        },
        "required": [
          "id",
          "name",
          "file",
          "preview",
          "maxAudience",
          "seatsReservedForOrganizersOrPresenters"
        ]
      },
      "maxItems": 5,
      "type": "array",
      "uniqueItems": true
    },
    "supportsStreaming": {
      "type": "boolean",
      "description": "A boolean value indicating whether this app can stream the meeting\u0027s audio video content to an RTMP endpoint.",
      "default": false
    },
    "supportsAnonymousGuestUsers": {
      "type": "boolean",
      "description": "A boolean value indicating whether this app allows management by anonymous users.",
      "default": false
    }
  },
  "description": "Specify meeting extension definition.",
  "additionalProperties": false
}
```

## Properties

#### scenes

Meeting supported scenes.

**Type**  
Array of [scenes](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition-scenes?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 5. Array items must be unique.

**Supported values**  


#### supportsCustomShareToStage

Represents if the app has added support for sharing to stage.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### videoFilters

Meeting supported video filters.

**Type**  
Array of [videoFilters](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition-video-filters?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 32. Array items must be unique.

**Supported values**  


#### videoFiltersConfigurationUrl

The *https://* URL for configuring the video filters.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### supportsStreaming

A Boolean value that indicates whether an app can stream the meeting's audio and video content to a real-time meeting protocol \(RTMP\) endpoint.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### supportsAnonymousGuestUsers

A Boolean value that indicates whether the app supports access by anonymous guest users.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

## Remarks

Note

The `supportsAnonymousGuestUsers` property in the app manifest schema v1.16 is supported only in [new Teams client](https://learn.microsoft.com/en-us/microsoftteams/platform/resources/teams-updates).

## Examples

```json
{
 "meetingExtensionDefinition": {
        "scenes": [ ]
    }
}
```
