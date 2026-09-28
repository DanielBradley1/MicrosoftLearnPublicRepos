<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities-activity-icons?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.activities.activityIcons object

Defines custom activity feed icons for your app in Teams. These icons help users quickly identify your app's notifications from other apps when posted on the activity feed. To learn more about how to create customized activity feed icons for your app, see [Custom activity icons in activity feed notifications](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications#custom-activity-icons-in-activity-feed-notifications).

Properties that reference this object type:

- [root.activities.activityIcons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-activities?view=m365-app-1.30#activityIcons-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "iconFile": "{string}"
}
```

```json
{
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
```

## Properties

#### id

Represents the unique icon ID.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### iconFile

Represents the relative path to the icon image. Image should be size 32x32.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**
