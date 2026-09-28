<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.description object

Describes your app to users. For apps submitted to AppSource, these values must match the information in your AppSource entry.

Properties that reference this object type:

- [root.description](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#description-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "short": "{string}",
  "full": "{string}",
  "features": [
    {
      "title": "{string}",
      "description": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "short": {
      "type": "string",
      "description": "A short description of the app used when space is limited. Maximum length is 80 characters.",
      "maxLength": 80
    },
    "full": {
      "type": "string",
      "description": "The full description of the app. Maximum length is 4000 characters.",
      "maxLength": 4000
    },
    "features": {
      "type": "array",
      "description": "Array of features sections describing what the app can do.",
      "minItems": 1,
      "maxItems": 3,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "title": {
            "type": "string",
            "maxLength": 45,
            "description": "Title of the feature the app provides."
          },
          "description": {
            "type": "string",
            "maxLength": 120,
            "description": "Detailed description of the specific feature."
          }
        },
        "required": [
          "title",
          "description"
        ]
      }
    }
  },
  "required": [
    "short",
    "full"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "short": "{string}",
  "full": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "short": {
      "type": "string",
      "description": "A short description of the app used when space is limited. Maximum length is 80 characters.",
      "maxLength": 80
    },
    "full": {
      "type": "string",
      "description": "The full description of the app. Maximum length is 4000 characters.",
      "maxLength": 4000
    }
  },
  "required": [
    "short",
    "full"
  ]
}
```

## Properties

#### short

A short description of the app, used when space is limited.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 80.

**Supported values**  


#### full

The full description of the app.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### features

Array of features sections describing what the app can do.

**Type**  
Array of [features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description-features?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 3.

**Supported values**  


## Remarks

Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does. You must note in the full description, if an external account is required for use. The values of `short` and `full` must be different. Your short description must not be repeated within the long description and must not include any other app name.

## Examples

```json
{
    "description": {
        "short": "Short description of your app",
        "full": "Full description of your app"
    }
}
```
