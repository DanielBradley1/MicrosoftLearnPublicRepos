<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-dialog-info-parameters?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# elementActions.handlers.dialogInfo.parameters object

Array of parameter object, each contains: name, title, description, inputType.

Properties that reference this object type:

- [root.actions.handlers.dialogInfo.parameters](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-dialog-info?view=m365-app-prev#parameters-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "{string}",
  "title": "{string}",
  "description": "{string}",
  "inputType": "{string}"
}
```

```json
{
  "type": "object",
  "required": [
    "name",
    "title",
    "description",
    "inputType"
  ],
  "properties": {
    "name": {
      "type": "string",
      "description": "Parameter name."
    },
    "title": {
      "type": "string",
      "description": "Parameter title."
    },
    "description": {
      "type": "string",
      "description": "Parameter description."
    },
    "inputType": {
      "type": "string",
      "description": "Parameter input type."
    }
  }
}
```

## Properties

#### name

Parameter name.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  


#### title

Parameter title.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  


#### description

Parameter description.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  


#### inputType

Parameter input type.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**
