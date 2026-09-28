<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-page-info?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# elementActions.handlers.pageInfo object

Object containing metadata of the page to open. Required if the handler type is `openPage`.

Properties that reference this object type:

- [root.actions.handlers.pageInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers?view=m365-app-prev#pageInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "pageId": "{string}",
  "subpageId": "{string}"
}
```

```json
{
  "type": "object",
  "required": [
    "pageId"
  ],
  "properties": {
    "pageId": {
      "type": "string",
      "description": "Used to navigate to the page in MetaOS app."
    },
    "subpageId": {
      "type": "string",
      "description": "Used to navigate to the subpage in MetaOS app."
    }
  }
}
```

## Properties

#### pageId

Maps to the `EntityId` of the tab. Used to navigate to a page in the app.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  


#### subpageId

Maps to the `SubEntityId` of the tab. Used to navigate to a subpage in the app.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
"actions":
    {
      "handlers": [
        {
          "pageInfo": {
            "pageId": "newTaskPage",
            "subPageId": ""
          }
        }
      ]
    }
}
```
