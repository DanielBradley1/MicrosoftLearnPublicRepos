<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card-content-source-bot-configuration?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# dashboardCardContentSource.botConfiguration object

The configuration for the bot source. Required if the `sourceType` is set to `bot`.

Properties that reference this object type:

- [root.dashboardCards.contentSource.botConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card-content-source?view=m365-app-1.30#botConfiguration-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "botId": "{string}"
}
```

```json
{
  "type": "object",
  "description": "The configuration for the bot source. Required if sourceType is set to bot.",
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The unique Microsoft app ID for the bot as registered with the Bot Framework."
    }
  },
  "additionalProperties": false
}
```

## Properties

#### botId

The unique Microsoft app ID for the bot as registered with the Bot Framework. The ID must be a GUID.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).
