<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-icons?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.icons object

Icons used within the Teams app. The icon files must be included as part of the upload package. For more information, see [Icons](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-package#app-icons).

Properties that reference this object type:

- [root.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#icons-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "outline": "{string}",
  "color": "{string}",
  "color32x32": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "outline": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a transparent PNG outline icon. The border color needs to be white. Size 32x32."
    },
    "color": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a full color PNG icon. Size 192x192."
    },
    "color32x32": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a full color PNG icon with transparent background. Size 32x32."
    }
  },
  "required": [
    "outline",
    "color"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "outline": "{string}",
  "color": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "outline": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a transparent PNG outline icon. The border color needs to be white. Size 32x32."
    },
    "color": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a full color PNG icon. Size 192x192."
    }
  },
  "required": [
    "outline",
    "color"
  ]
}
```

## Properties

#### outline

A relative file path to a transparent 32x32 PNG outline icon. The border color must be white.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### color

relative file path to a full color 192x192 PNG icon.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### color32x32

A relative file path to a full color 32x32 PNG icon with transparent background. Used when the app is pinned in Outlook and Microsoft 365 app.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


## Examples

```json
{
    "icons": {
        "outline": "A relative path to a transparent .png icon — 32px X 32px",
        "color": "A relative path to a full color .png icon — 192px X 192px"
    }
}
```

```json
{
    "icons": {
        "outline": "%FILENAME-32x32px%",
        "color": "%FILENAME-192x192px",
        "color32x32": "%FILENAME-32x32px%"
    }
}
```
