<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-types?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.activities.activityTypes object

Array of objects representing activity notifications that your app can post to a user's activity feed in Teams. The `systemDefault` activity type is a reserved value and invalid for use.

Properties that reference this object type:

- [root.activities.activityTypes](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities?view=m365-app-1.30#activityTypes-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "type": "{string}",
  "description": "{string}",
  "templateText": "{string}",
  "displayName": "{string}",
  "allowedIconIds": [
    "{string}"
  ]
}
```

```json
{
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
    "displayName": {
      "type": "string",
      "minLength": 1,
      "maxLength": 128,
      "pattern": "\\S",
      "description": "The localized, user-visible display name of this activity type. Author a concise standalone noun label using sentence casing appropriate for the locale; do not include surrounding host commands such as \u0022Turn off\u0022 or ending punctuation. Consumers must preserve the resolved value exactly, must not transform its casing, and must not use it as identity; type remains the stable identifier."
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
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "type": "{string}",
  "description": "{string}",
  "templateText": "{string}",
  "allowedIconIds": [
    "{string}"
  ]
}
```

```json
{
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
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "type": "{string}",
  "description": "{string}",
  "templateText": "{string}"
}
```

```json
{
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
```

## Properties

#### type

The notification type.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### type

The notification type.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### description

A brief description of the notification.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### templateText

Text template for the notification. For example: "{actor} created task {taskId} for you"

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### displayName

The localized, user-visible display name of this activity type. Author a concise standalone noun label using sentence casing appropriate for the locale; do not include surrounding host commands such as "Turn off" or ending punctuation. Consumers must preserve the resolved value exactly, must not transform its casing, and must not use it as identity; type remains the stable identifier.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 128.

**Supported values**  
The string must match the following regular expression: `\S`.

#### allowedIconIds

An array containing valid icon IDs per activity type.

**Type**  
Array of string

**Required**  
—

**Constraints**  
Maximum array items: 50.

**Supported values**  


## Examples

```json
{
   "activities":{
      "activityTypes":[
         {
            "type":"taskCreated",
            "description":"Task Created Activity",
            "templateText":"{actor} created task {taskId} for you"
         },
         {
            "type":"teamMention",
            "description":"Team Mention Activity",
            "templateText":"{actor} mentioned team"
         },
         {
            "type":"channelMention",
            "description":"Channel Mention Activity",
            "templateText":"{actor} mentioned channel"
         },
         {
            "type":"userMention",
            "description":"Personal Mention Activity",
            "templateText":"{actor} mentioned user"
         },
         {
            "type":"calendarForward",
            "description":"Forwarding a Calendar Event",
            "templateText":"{actor} sent user an invite on behalf of {eventOwner}"
         },
         {
            "type":"calendarForward",
            "description":"Forwarding a Calendar Event",
            "templateText":"{actor} sent user an invite on behalf of {eventOwner}"
         },
         {
            "type":"creatorTaskCreated",
            "description":"Created Task Created",
            "templateText":"The Creator created task {taskId} for you"
         }
      ]
   }
}
```
