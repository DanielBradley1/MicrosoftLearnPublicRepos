<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.activities object

Defines the notifications your app posts to the user's [activity feed](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications) in Teams.

Properties that reference this object type:

- [root.activities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#activities-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "activityTypes": [
    {
      "type": "{string}",
      "description": "{string}",
      "templateText": "{string}",
      "allowedIconIds": [
        "{string}"
      ]
    }
  ],
  "activityIcons": [
    {
      "id": "{string}",
      "iconFile": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "activityTypes": {
      "type": "array",
      "description": "Specify the types of activites that your app can post to a users activity feed",
      "maxItems": 128,
      "items": {
        "type": "object",
        "properties": {
          "type": {
            "type": "string",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "maxLength": 128
          },
          "templateText": {
            "type": "string",
            "maxLength": 128
          },
          "allowedIconIds": {
            "type": "array",
            "description": "An array containing valid icon IDs per activity type.",
            "maxItems": 50,
            "items": {
              "type": "string"
            }
          }
        },
        "required": [
          "type",
          "description",
          "templateText"
        ],
        "additionalProperties": false
      }
    },
    "activityIcons": {
      "type": "array",
      "description": "Specify the customized icons that your app can post to a users activity feed",
      "maxItems": 50,
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "type": "string",
            "maxLength": 64,
            "description": "Represents the unique icon ID."
          },
          "iconFile": {
            "type": "string",
            "maxLength": 128,
            "description": "Represents the relative path to the icon image. Image should be size 32x32."
          }
        },
        "required": [
          "id",
          "iconFile"
        ],
        "additionalProperties": false
      }
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "activityTypes": [
    {
      "type": "{string}",
      "description": "{string}",
      "templateText": "{string}",
      "allowedIconIds": [
        "{string}"
      ]
    }
  ],
  "activityIcons": [
    {
      "id": "{string}",
      "iconFile": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "activityTypes": {
      "type": "array",
      "description": "Specify the types of activites that your app can post to a users activity feed",
      "maxItems": 128,
      "items": {
        "type": "object",
        "properties": {
          "type": {
            "type": "string",
            "maxLength": 64
          },
          "description": {
            "type": "string",
            "maxLength": 128
          },
          "templateText": {
            "type": "string",
            "maxLength": 128
          },
          "allowedIconIds": {
            "type": "array",
            "description": "An array containing valid icon IDs per activity type.",
            "maxItems": 50,
            "items": {
              "type": "string"
            }
          }
        },
        "required": [
          "type",
          "description",
          "templateText"
        ],
        "additionalProperties": false
      }
    },
    "activityIcons": {
      "type": "array",
      "description": "Specify the customized icons that your app can post to a users activity feed",
      "maxItems": 50,
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "type": "string",
            "maxLength": 64,
            "description": "Represents the unique icon ID."
          },
          "iconFile": {
            "type": "string",
            "maxLength": 128,
            "description": "Represents the relative path to the icon image. Image should be size 32x32."
          }
        },
        "required": [
          "id",
          "iconFile"
        ],
        "additionalProperties": false
      }
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "activityTypes": [
    {
      "type": "{string}",
      "description": "{string}",
      "templateText": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "activityTypes": {
      "type": "array",
      "description": "Specify the types of activites that your app can post to a users activity feed",
      "maxItems": 128,
      "items": {
        "type": "object",
        "properties": {
          "type": {
            "type": "string",
            "maxLength": 64
          },
          "description": {
            "type": "string",
            "maxLength": 128
          },
          "templateText": {
            "type": "string",
            "maxLength": 128
          }
        },
        "required": [
          "type",
          "description",
          "templateText"
        ],
        "additionalProperties": false
      }
    }
  },
  "additionalProperties": false
}
```

## Properties

#### activityTypes

Array of objects representing activity notifications that your app can post to a user's activity feed in Teams. The `systemDefault` activity type is a reserved value and invalid for use.

**Type**  
Array of [activityTypes](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 128.

**Supported values**  


#### activityIcons

Specify the customized icons that your app can post to a users activity feed

**Type**  
Array of [activityIcons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 50.

**Supported values**  


## Examples

```json
{
    "activities": {
        "activityTypes": [
            {
                "type": "taskCreated",
                "description": "Task created activity",
                "templateText": "<team member> created task <taskId> for you"
            },
            {
                "type": "userMention",
                "description": "Personal mention activity",
                "templateText": "<team member> mentioned you"
            }
        ]
    },
}
```
