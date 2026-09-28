<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# dashboardCard object

Defines a single dashboard card and its properties.

Properties that reference this object type:

- [root.dashboardCards](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#dashboardCards-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "displayName": "{string}",
  "description": "{string}",
  "pickerGroupId": "{string}",
  "icon": {
    "iconUrl": "{string}",
    "officeUIFabricIconName": "{string}"
  },
  "contentSource": {
    "sourceType": "bot",
    "botConfiguration": {
      botConfiguration object
    }
  },
  "defaultSize": "medium | large"
}
```

```json
{
  "type": "object",
  "description": "Cards wich could be pinned to dashboard providing summarized view of information relevant to user.",
  "properties": {
    "id": {
      "$ref": "#/definitions/guid",
      "description": "Unique Id for the card. Must be unique inside the app."
    },
    "displayName": {
      "type": "string",
      "description": "Represents the name of the card. Maximum length is 255 characters.",
      "maxLength": 255
    },
    "description": {
      "type": "string",
      "description": "Description of the card.Maximum length is 255 characters.",
      "maxLength": 255
    },
    "pickerGroupId": {
      "$ref": "#/definitions/guid",
      "description": "Id of the group in the card picker. This must be guid."
    },
    "icon": {
      "$ref": "#/definitions/dashboardCardIcon"
    },
    "contentSource": {
      "$ref": "#/definitions/dashboardCardContentSource"
    },
    "defaultSize": {
      "type": "string",
      "enum": [
        "medium",
        "large"
      ],
      "description": "Rendering Size for dashboard card."
    }
  },
  "required": [
    "id",
    "displayName",
    "pickerGroupId",
    "description",
    "contentSource",
    "defaultSize"
  ],
  "additionalProperties": false
}
```

## Properties

#### id

A unique identifier for this dashboard card. The ID must be a GUID.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### displayName

Display name of the card.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 255.

**Supported values**  


#### description

Description of the card.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 255.

**Supported values**  


#### pickerGroupId

ID of the group in the card picker. The ID must be a GUID.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### icon

Specifies the icon for the card.

**Type**  
[dashboardCardIcon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card-icon?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### contentSource

Specifies the source of the card's content.

**Type**  
[dashboardCardContentSource](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card-content-source?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### defaultSize

Rendering size for the dashboard card.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `medium`, `large`.
