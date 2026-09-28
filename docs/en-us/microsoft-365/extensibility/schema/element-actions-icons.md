<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-icons?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# elementActions.icons object

Object containing URLs to icon images for this action intent.

Properties that reference this object type:

- [root.actions.icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions?view=m365-app-prev#icons-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "size": {number},
  "url": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "size": {
      "type": "number",
      "description": "Icon size in pixels."
    },
    "url": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "URL for the icon."
    }
  },
  "additionalProperties": false,
  "required": [
    "size",
    "url"
  ]
}
```

## Properties

#### size

Icon size in pixels.

**Type**  
number

**Required**  
✅

**Constraints**  


**Supported values**  


#### url

URL for the icon.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.
