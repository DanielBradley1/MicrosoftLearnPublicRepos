<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-app-deeplinks-array?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# extensionAppDeeplinksArray object

For Microsoft internal use only.

Properties that reference this object type:

- [root.extensions.appDeeplinks](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-prev#appDeeplinks-property)

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
  "actionId": "{string}",
  "label": "{string}",
  "semanticDescription": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "type": "object",
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "contexts": {
      "type": "array",
      "$ref": "#/definitions/extensionContexts"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an action defined in runtimes. Manifest should be invalidated if no action with an id matching actionId is present in runtimes.",
      "maxLength": 64
    },
    "label": {
      "type": "string",
      "description": "the text that will be shown on the app as a clickable item.",
      "maxLength": 64
    },
    "semanticDescription": {
      "type": "string",
      "description": "the text metadata, for recommendation engine.",
      "maxLength": 255
    }
  },
  "additionalProperties": false,
  "required": [
    "contexts",
    "actionId",
    "label",
    "semanticDescription"
  ]
}
```

## Properties

#### requirements

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**  


#### contexts

Specifies the Office application windows in which the ribbon customization is available to the user. Each item in the array is a member of a string array. Possible values are: mailRead, mailCompose, meetingDetailsOrganizer, meetingDetailsAttendee, onlineMeetingDetailsOrganizer, logEventMeetingDetailsAttendee, spamReportingOverride.

**Type**  
Array of string

**Required**  
✅

**Constraints**  
Minimum array items: 1. Maximum array items: 8.

**Supported values**  
Allowed values: `mailRead`, `mailCompose`, `meetingDetailsOrganizer`, `meetingDetailsAttendee`, `onlineMeetingDetailsOrganizer`, `logEventMeetingDetailsAttendee`, `default`, `spamReportingOverride`.

#### actionId

The ID of an action defined in runtimes. Manifest should be invalidated if no action with an id matching actionId is present in runtimes.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### label

the text that will be shown on the app as a clickable item.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### semanticDescription

the text metadata, for recommendation engine.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 255.

**Supported values**
