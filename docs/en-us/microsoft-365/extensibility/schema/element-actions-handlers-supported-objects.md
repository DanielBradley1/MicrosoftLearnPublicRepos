<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-supported-objects?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# elementActions.handlers.supportedObjects object

The supported object types that can trigger this Action.

Properties that reference this object type:

- [root.actions.handlers.supportedObjects](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers?view=m365-app-prev#supportedObjects-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "file": {
    "extensions": [
      "{string}"
    ]
  },
  "folder": object | null
}
```

```json
{
  "type": "object",
  "properties": {
    "file": {
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
    },
    "folder": {
      "type": [
        "object",
        "null"
      ],
      "description": "A null value indicates that the file handler is not available when a folder is selected. An object with no parameters indicates that the file handler is available when a folder is selected or when no files are selected."
    }
  }
}
```

## Properties

#### file

Supported file types.

**Type**  
[file](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-supported-objects-file?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**  


#### folder

A null value indicates that the file handler is not available when a folder is selected. An object with no parameters indicates that the file handler is available when a folder is selected or when no files are selected.

**Type**  
object \| null

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
