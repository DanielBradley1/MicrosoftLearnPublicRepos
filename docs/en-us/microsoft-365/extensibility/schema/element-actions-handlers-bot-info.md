<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-bot-info?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# elementActions.handlers.botInfo object

Properties that reference this object type:

- [root.actions.handlers.botInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers?view=m365-app-prev#botInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "botId": "{string}",
  "fetchTask": {boolean}
}
```

```json
{
  "type": "object",
  "required": [
    "botId"
  ],
  "properties": {
    "botId": {
      "type": "string",
      "description": "Bot ID."
    },
    "fetchTask": {
      "type": "boolean",
      "description": "Fetch task from bot."
    }
  }
}
```

## Properties

#### botId

Bot ID.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  


#### fetchTask

Fetch task from bot.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**
