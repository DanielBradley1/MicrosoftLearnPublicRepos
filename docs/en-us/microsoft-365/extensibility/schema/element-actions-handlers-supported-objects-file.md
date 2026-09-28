<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-supported-objects-file?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# elementActions.handlers.supportedObjects.file object

Properties that reference this object type:

- [root.actions.handlers.supportedObjects.file](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-supported-objects?view=m365-app-prev#file-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "extensions": [
    "{string}"
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "extensions": {
      "type": "array",
      "items": {
        "type": "string",
        "description": "File extension, e.g. .pdf, .docx."
      }
    }
  }
}
```

## Properties

#### extensions

File extension, e.g. .pdf, .docx.

**Type**  
Array of string

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
"actions": [
    {
      "handlers": [
        {
          "supportedObjects": {
            "file": {
              "extensions": [
                "doc",
                "pdf"
              ]
            }
          }
        }
      ]
    },
  ]
}
```
