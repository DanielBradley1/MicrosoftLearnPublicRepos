<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card-icon?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# dashboardCardIcon object

Defines the icon properties of a given dashboard card.

Properties that reference this object type:

- [root.dashboardCards.icon](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/dashboard-card?view=m365-app-1.30#icon-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "iconUrl": "{string}",
  "officeUIFabricIconName": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Represents a configuration for the source of the card\u2019s content",
  "properties": {
    "iconUrl": {
      "type": "string",
      "description": "The icon for the card, to be displayed in the toolbox and card bar, represented as URL.",
      "maxLength": 2048
    },
    "officeUIFabricIconName": {
      "type": "string",
      "description": "Office UI Fabric/Fluent UI icon friendly name for the card. This value will be used if \u2018iconUrl\u2019 is not specified.",
      "maxLength": 255
    }
  },
  "additionalProperties": false
}
```

## Properties

#### iconUrl

Location of the icon for the card, to be displayed in the toolbox and card bar.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### officeUIFabricIconName

Office UI Fabric or Fluent UI icon's friendly name for the card. This value is used if `iconUrl` is not specified.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 255.

**Supported values**
