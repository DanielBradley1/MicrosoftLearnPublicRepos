<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition-scenes?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.meetingExtensionDefinition.scenes object

Meeting supported scenes.

Properties that reference this object type:

- [root.meetingExtensionDefinition.scenes](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-meeting-extension-definition?view=m365-app-1.30#scenes-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "name": "{string}",
  "file": "{string}",
  "preview": "{string}",
  "maxAudience": {number},
  "seatsReservedForOrganizersOrPresenters": {number}
}
```

```json
{
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
}
```

## Properties

#### id

The unique identifier for the scene. This ID must be a GUID.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### name

The name of the scene.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### file

The relative file path to the scenes' metadata json file.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### preview

The relative file path to the scenes' PNG preview icon.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### maxAudience

The maximum number of audiences supported in the scene.

**Type**  
integer

**Required**  
✅

**Constraints**  
Maximum number value: 50.

**Supported values**  


#### seatsReservedForOrganizersOrPresenters

The number of seats reserved for organizers or presenters.

**Type**  
integer

**Required**  
✅

**Constraints**  
Maximum number value: 50.

**Supported values**  


## Examples

```json
{
 "meetingExtensionDefinition": {
        "scenes": [
            {
                "id": "9082c811-7e6a-4174-8173-6ccd57d377e6",
                "name": "Getting started sample",
                "file": "scenes/sceneMetadata.json",
                "preview": "scenes/scenePreview.png",
                "maxAudience": 15,
                "seatsReservedForOrganizersOrPresenters": 0
            }
        ]
    }
}
```
