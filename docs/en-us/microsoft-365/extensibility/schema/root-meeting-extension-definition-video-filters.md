<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition-video-filters?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# root.meetingExtensionDefinition.videoFilters object

This object indicates meeting supported video filters.

Properties that reference this object type:

- [root.meetingExtensionDefinition.videoFilters](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition?view=m365-app-prev#videoFilters-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "name": "{string}",
  "thumbnail": "{string}"
}
```

```json
{
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
}
```

## Properties

#### id

The unique identifier for the video filter. This ID must be a GUID.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### name

The name of the video filter.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-prev).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### thumbnail

The relative file path to the video filter's thumbnail.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**
