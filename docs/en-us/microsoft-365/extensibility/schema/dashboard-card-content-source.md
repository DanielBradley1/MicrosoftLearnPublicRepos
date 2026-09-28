<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card-content-source?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# dashboardCardContentSource object

Defines the content source of a given dashboard card.

Properties that reference this object type:

- [root.dashboardCards.contentSource](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card?view=m365-app-1.30#contentSource-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "sourceType": "bot",
  "botConfiguration": {
    "botId": "{string}"
  }
}
```

```json
{
  "type": "object",
  "description": "Represents a configuration for the source of the card\u2019s content.",
  "properties": {
    "sourceType": {
      "type": "string",
      "enum": [
        "bot"
      ],
      "description": "The content of the dashboard card is sourced from a bot."
    },
    "botConfiguration": {
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
  },
  "additionalProperties": false
}
```

## Properties

#### sourceType

Represents the source of a card's content.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `bot`.

#### botConfiguration

The configuration for the bot source. Required if the `sourceType` is set to `bot`.

**Type**  
[botConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card-content-source-bot-configuration?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
