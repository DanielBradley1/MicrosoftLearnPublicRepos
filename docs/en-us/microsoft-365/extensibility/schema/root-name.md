<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-name?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.name object

The name of your app experience, displayed to users in the Teams experience. For apps submitted to AppSource, these values must match the information in your AppSource entry. The values of `short` and `full` must be different. App name helps improve your app discoverability in the Teams Store.

Properties that reference this object type:

- [root.name](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#name-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "short": "{string}",
  "full": "{string}",
  "abbreviated": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "short": {
      "type": "string",
      "description": "A short display name for the app.",
      "maxLength": 30
    },
    "full": {
      "type": "string",
      "description": "The full name of the app, used if the full app name exceeds 30 characters.",
      "maxLength": 100
    },
    "abbreviated": {
      "type": "string",
      "description": "An abbreviated name for the app.",
      "maxLength": 15
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
      "description": "A short display name for the app.",
      "maxLength": 30
    },
    "full": {
      "type": "string",
      "description": "The full name of the app, used if the full app name exceeds 30 characters.",
      "maxLength": 100
    }
  },
  "required": [
    "short"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

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
      "description": "A short display name for the app.",
      "maxLength": 30
    },
    "full": {
      "type": "string",
      "description": "The full name of the app, used if the full app name exceeds 30 characters.",
      "maxLength": 100
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

The short display name for the app. The `short` property is used when space is limited, such as the app header.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 30.

**Supported values**  


#### full

The full name of the app, used if the full app name exceeds 30 characters.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 100.

**Supported values**  


#### full

The full name of the app, used if the full app name exceeds 30 characters. The `full` property is used when there's sufficient space, such as the app catalog or the app details page.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 100.

**Supported values**  


#### full

The full name of the app, used if the full app name exceeds 30 characters. The `full` property is used when there's sufficient space, such as the app catalog or the app details page.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 100.

**Supported values**  


#### abbreviated

Abbreviated name for the app; used as the display name on the app bar on the left hand side of the UI. If not specified, `short` name is used on the app bar.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 15.

**Supported values**  


## Remarks

Note

- In the app manifest v1.17 or later the `full` property is required and for app manifest v1.16 or earlier it isn't required.
- The `short` property is used across all UI surfaces.

## Examples

```json
{
    "name": {
        "short": "Name of your app (<=30 chars)",
        "full": "Full name of app, if longer than 30 characters (<=100 chars)"
    }
}
```
